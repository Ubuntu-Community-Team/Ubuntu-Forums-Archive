---
title: "ubuntu 9.04 -&gt; Hot Temperature"
date: 2009-05-18
forum: General Help
---

### Post by yma981 on 2009-05-18
I am using ubuntu 9.04 on my Toshiba A305-S6825

I am noticing that the Laptop temperature is somehow hotter than when i used to be on windows XP?? 


How can i monitor the laptop temp and log any Temp abnormality?
Is there manufacturers standard for that?
Any idea ?

---

### Post by SteveDee on 2009-05-18
> **yma981 said:**
> I am using ubuntu 9.04 on my Toshiba A305-S6825

I am noticing that the Laptop temperature is somehow hotter than when i used to be on windows XP?? 


How can i monitor the laptop temp and log any Temp abnormality?
Is there manufacturers standard for that?
Any idea ?

Install X Sensors (Applications > Add/Remove...  then type "sensors" in the search field). This will show temps & fan speeds.

You could also add System Monitor to your desktop panel (right click on panel > Add to panel > System Monitor) and display the cpu%. You may have an app or process running that is driving your cpu to 100%.

---

### Post by yma981 on 2009-05-18
> **SteveDee said:**
> Install X Sensors (Applications > Add/Remove...  then type "sensors" in the search field). This will show temps & fan speeds.

You could also add System Monitor to your desktop panel (right click on panel > Add to panel > System Monitor) and display the cpu%. You may have an app or process running that is driving your cpu to 100%.

Actually my system is idle most of the time, the dual core cpu is most of the time idle with not more than 5% load. 

the uptime command gave:
20:56:26 up  9:11,  2 users,  load average: 0.25, 0.12, 0.04  

Anyway I am going to install the X Sensors to monitor a little more the temp. 

Can i compare the result to a standard ??

---

### Post by SteveDee on 2009-05-18
> **yma981 said:**
> Actually my system is idle most of the time, the dual core cpu is most of the time idle with not more than 5% load. 

the uptime command gave:
20:56:26 up  9:11,  2 users,  load average: 0.25, 0.12, 0.04  

Anyway I am going to install the X Sensors to monitor a little more the temp. 

Can i compare the result to a standard ??

You should be able to find the spec for your processor, but that will probably only tell you the max temp. I don't think you will find a "normal" figure.

The cpu scaling monitor is another tool (right click on desktop panel > Add to panel... > CPU Scaling Freq Monitor).
This should show the current frequency, which should fall when your system is idle, if supported by your hardware.

If your laptop still boots XP I guess you could do some comparisons of temp and fan speeds.

---

### Post by yma981 on 2009-05-18
I downloaded the C Sensor you mentioned and after some googleling I found that i should run 

sudo /usr/sbin/sensors-detect 

I answered some questions about hardware and sensors and stuff but the X Sensors aren't giving anything except for a blank box and with nothing to do ??? !!!!!!

---

### Post by SteveDee on 2009-05-19
> **yma981 said:**
> I downloaded the C Sensor you mentioned and after some googleling I found that i should run 

sudo /usr/sbin/sensors-detect 

I answered some questions about hardware and sensors and stuff but the X Sensors aren't giving anything except for a blank box and with nothing to do ??? !!!!!!

I guess I was lucky, I've installed this on 2 desktops, run sudo /usr/sbin/sensors-detect, answered "yes" to all questions, re-booted, and it just works.

Suggest you run this from a terminal:-
sudo /usr/bin/xsensors 
... and see what errors are reported.

You will probably need to re-run sensors-detect and try different options, or try to find a ready made config file here: [http://www.lm-sensors.org/wiki/Configurations](http://www.lm-sensors.org/wiki/Configurations)

Also look here: [http://www.lm-sensors.org/wiki/FAQ](http://www.lm-sensors.org/wiki/FAQ)

Or you could take a look at the config file /etc/sensors3.conf using a text editor.

---

### Post by WeEatVista on 2009-05-19
Im not sure if this will help you out at all but I found this guide extremely helpful when my X Sensors was malfunctioning. Instead of using X Sensors, you can use the sensors applet. Check it out - [http://cviorel.easyblog.ro/2008/04/04/enabling-temperature-sensors-in-ubuntu/](http://cviorel.easyblog.ro/2008/04/04/enabling-temperature-sensors-in-ubuntu/)

-WeEatVista

---

