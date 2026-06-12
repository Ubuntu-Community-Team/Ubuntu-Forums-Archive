---
title: "Monitoring temperatures of my XPS M1710"
date: 2007-10-07
forum: Dell  Ubuntu Support
---

### Post by anarchypower on 2007-10-07
Dear ubuntu community members,

I own a Dell XPS m1710 and since a few days now I've been trying to read the status of my temperature sensors. This however is not working without problems. I am very confused. 
Back in windows I used i8kfan from [www.diefer.de/i8kfan/](www.diefer.de/i8kfan/) . This program allowed me to monitor 5 different sensors. I assume that some app in ubuntu can do the same, but so far I haven't found one...
I tried 2 programs (the only 2 I found): "gkrellm" and "Computer Temperature Monitor"
Both of them only allow me to monitor 2 sensors. But I can't find any logic behind these programs...I have a screenshot to explain my problem:
Have a look at gkrellm. According to gkrellm the temperature of my CPU is 59°, but this temperature matches my GPU Core temp which can be found in my NVIDIA settings menu. This means that gkrellm thinks that my GPU temp is my CPU temp...Not a very good start :s
Computer temperature monitor on the other hand thinks it is displaying my CPU temperature (43°), and indeed, this temperature matches the THM sensor that gkrellm is displaying. But which device has a temperature of 40°? I don't understand a thing...

Am I doing anything wrong or something? Are there better programs to use? Does anyone have experience with this stuff?:)

Any help is appreciated,

greetings

EDIT: I just tried lm-sensors, it has the same result as Computer temperature monitor.



[IMG]http://users.pandora.be/anarchypower/temp.jpg[/IMG]

---

### Post by sonofusion82 on 2007-10-07
yes, if you type sensors at CLI you might get something like this:

temp1:       +34°C  (high =   +12°C, hyst =   +71°C)   sensor = thermistor      
temp2:     +40.0°C  (high =  +120°C, hyst =  +115°C)   sensor = diode
temp3:     +32.5°C  (high =  +120°C, hyst =  +115°C)   sensor = thermistor 

for me, temp2 is my CPU temperature because the sensor type is CPU's built-in diode sensor

---

### Post by mtbsoft on 2007-10-08
FYI.  i8kutils is also available on Ubuntu to plug into gkrellm and permits better control of the dell lappy fans.

---

### Post by anarchypower on 2007-10-08
If I type sensors in the command line, no sensors are detected. Also, when I run sensors-detect, not much changes... :s

Second, I already used i8kutils as a plug-in in gkrellm...That is what's showing the temperature in the first place :p

---

### Post by tturrisi on 2007-10-09
Your comp has a Core2 Duo cpu, thus you need the coretemp kernel module, not i8k. The coretemp module is only available in kernel 2.6.22.x and upward.  What kernel are you running?

---

### Post by anarchypower on 2007-10-09
Dear tturisi,

I am running kernel 2.6.20-16-generic :s

I am not familiar with updating a kernel tho...I guess it'll be better to wait a few more days, till 7.10 is out :) It'll probably have the new kernel on board...

---

### Post by tturrisi on 2007-10-10
[http://ubuntuforums.org/showthread.php?t=511974&page=19](http://ubuntuforums.org/showthread.php?t=511974&page=19)

---

