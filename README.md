# JMeter Documentation

**@author: Saksham Varshney**

## Description: This repository contains documentation of Performance testing tool JMeter

### Performance Testing:
Performance Testing is a type of testing to ensure software applications will perform well under the particular workload

### Types of Performance Testing:
	1. Load Testing
	2. Stress Testing
	3. Volume Testing
	4. Endurance Testing
	5. Spike Testing
	6. Scalability Testing

### Load Testing:
	1. Script runs in headless mode
	2. Script will run for 1k, 10k or more times depend upon our configurations

### Load Testing Tools:
	1. JMeter
	2. Load Runner
	3. New Load
	4. Load UI

### JMeter:
	1. It is the most popular Load Test Tool
	2. It is Open Source & free of cost tool
	3. Built on Java
	4. GUI is more user-friendly
	5. Cross Plateform Support

### Installing JMeter:
	1. Download Binaries-zip file
	2. Make sure to have require java version
	3. Extract the JMeter zip file
	4. Go to bin >> Launch the application

### Record & Play back in JMeter:
Perform set of steps on browser and JMeter will listen those steps and write script for us

**Steps:**
1. Click on Test Plan >> Add >> Non Test Elements >> HTTP(s) Test Script Recorder
2. Need to configure the port number [suppose 8888]
3. Need to configure Test Plan Creation >> Target Controller

### Thread Group:
A thread group is a set of threads executing the same scenario

>**Some other thread groups:**

**Prerequisite:** Need to install Jmeter Plugin Manager

**Other Thread Groups:**
1. Concurrency Thread group: Contains following parameters
	1. Target Concurrency
	2. Ramp Up Time
	3. Ramp-Up Steps Count
	4. Hold Target Rate Time

**Reference:**
![](https://github.com/sakshamvarshney/JMeter-Documentation/blob/master/files/Concurrency-Thread-Group.png)

2. Ultimate Thread group: Contains following parameters
	1. Start Threads Count
	2. Initial Delay
	3. Startup Time
	4. Hold Load For
	5. Stutdown Time

**Reference:**
![](https://github.com/sakshamvarshney/JMeter-Documentation/blob/master/files/Ultimate-Thread-Group.png)

### Some Important terms in JMeter Report/Results:
1. **Samples:** No of users hit that specific request

2. **90%ile:** 90% of the samples took no more than this time. The remaining samples took at least as long as this (90th percentile)

3. **Average transition value:** It is the average time taken by all the samples to execute specific
label

4. **Error %:** Percentage of Failed requests per Label

5. **Throughput:**
	1. Throughput is the number of request that are processed per time unit(seconds, minutes, hours) by the server
	2. This time is calculated from the start of first sample to the end of the last sample
	3. Larger throughput is better

>**Cookie Manager:** It is use to store the cookie [Auth token/key] of transition like any application login page

### Some Important Listeners in JMeter Script:
1. Aggregate Report
2. Graph Results
3. View Results tree

### Assertion Results:
1. Response Assertion:
	1. Status code Assertion
	2. Response text Assertion
2. Size Assertion

### Controller:
1. Controller is simply a container/folder that can store multiple requests
2. It is use to categorize request in good manner

**Different Types of Controller:**
1. **Recording Controller:** It is simply use to record the requests
2. **Transaction Controller:** It is use to represent the parent request [Controller Name] in Aggregate Result Report
3. **Simple Controller:** The parent rquest [Controller Name] is not displayed in Aggregate Result Report
4. **Module Controller:** It is use to re-use the controllers script requests again without recording / copy paste the same requests
5. **Interleave Controller:** One sampler per Iteration is executed in top to bottom order
6. **Runtime Controller:** Runtime Controller controls the execution of its samplers/requests for the given time
7. **Random Controller:** Random Controller plays only one of its children samples picking it randomly
8. **IF Controller**: It is condition based controller, if the curtain condition matches/passes then only execute that particular request
9. **Loop Controller:** It is same as Runtime Controller but the difference is request getting execute as per number of loop count not per time count
10. **While Controller:** Samples getting execute until condition becomes false

### Timer:
1. Constant Timer:
2. Gaussian Random Timer: Constant Time + Deviation Time
3. Poisson Random Timer: Constant Time + Lambda Time
4. Costant Throughput Timer: It can restrict the request processed per time

>**Regular Expression Extractor**:
1. It is use when need to grab data from the site itself and use that data in next steps in test
2. Generally use as post-proceessor

>**Question:** Can we use single Regular Expression Extractor to extract or grab the multiple data ?

>**Answer:** Yes

**Reference:**
![1](https://github.com/sakshamvarshney/JMeter-Documentation/blob/master/files/RegEx-Extractor-1.png)
![2](https://github.com/sakshamvarshney/JMeter-Documentation/blob/master/files/RegEx-Extractor-2.png)
![3](https://github.com/sakshamvarshney/JMeter-Documentation/blob/master/files/RegEx-Extractor-3.png)

>**Debug Sampler:** It is the place we can see all the variables used during the whole test

>**Data Driven Testing:** It simply means get data from csv file

### Run tests via non GUI via cmd:
	1. Launch cmd via Administratative mode
	2. go to apache bin directory
	3. Run "jmeter -n -t testname.jmx -l results.jtl" command on cmd

>**Note:**

	Give filename with path if script is not present in bin directory
	n: non GUI mode
	t: testplan
	l: store results

### What is JMeter Distributed mode:
There are certain limitations to the number of users you can run, with the CPU memory and RAM Configuration for a single machine so it is use to distribute the load

**Setup steps:**

>**In Slave Machine:**
1. Go to bin directory > Open jmeter.properties
2. Make this "server.rmi.ssl.disable" config unhide and true
3. Launch the jmeter-server.bat
4. It will show "Created remote object" on some ip statement on cmd
5. Remember the IP address of slave machine

>**In Master Machine:**
1. Go to bin directory > Open jmeter.properties
2. Make this "server.rmi.ssl.disable" config unhide and true
3. Give this "remote_hosts" config the IP address of slave machine
4. Launch the JMeter application and start the test on Remote server as Click on Run from top menu > Click Remote Start > Select the Slave Machine IP Address

**Pre-cautions:**
1. Both Master & Slave machines must run the same Jmeter version
2. Both Master & Slave machines must be on the same subnetwork(wifi)
3. Both Master & Slave machines should be as similar as possible: same OS, same directory tree, etc

### BeanShell Scripting in JMeter:
**Scenario:** Need to add/append india in username if country is india

	String newUsername;
	log.info(vars get("country"));
	String country= vars.get("country");
	if(country.equals("india")
    {
		newUsername= vars.get("username")+"india";
		vars.put("username", newUsername);
	}

>**Sample jmx file:**

#### Description: File contains login/logout script of internet.herokuapp application

#### Pre-requiste:
1. Download the both files [jmx & csv] from below google drive link
2. Put these downloaded files in same folder to avoid wrong csv file directory in script

#### Files link: [Click here to download the files](https://drive.google.com/drive/folders/1Vs_QVHTH53loTtdadeAt14LsVQ2u_GdY)

>**Note:** File is restricted in access, please request to access these files

#### Aggregate Report Sample:
![](https://github.com/sakshamvarshney/JMeter-Documentation/blob/master/files/AggregateReportSample.png)

---
