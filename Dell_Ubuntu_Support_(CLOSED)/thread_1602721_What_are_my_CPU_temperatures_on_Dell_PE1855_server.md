---
title: "What are my CPU temperatures on Dell PE1855 server blade?"
date: 2010-10-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by annahaywood on 2010-10-21
HI all,
Pretty new to Ubuntu and Linux in general. Have installed Ubuntu 10.04 LTS on 10 Dell PowerEdge 1855 servers. Would like to find a way to tell what the temperatures of the CPUs are?  
 
Tried to install Open Manage to measure do this but no luck> here's what happened and where I'm at with Open manage install:
 
[EMAIL="bluetool@bluetool:~$"]bluetool@bluetool:~$[/EMAIL] sudo apt-get install dellomsa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
The following packages have unmet dependencies:
dellomsa: Depends: libstdc++5 but it is not installable
E: Broken packages
 
And, hey, if you know of a more straightforward way of gauging the CPU temperatures for Ubuntu 10.04, please let me know!
 
Thanks,
Anna

---

### Post by Jimtheplanner on 2010-10-22
Hi Anna,

First you have install the appropriate code....This my method using the terminal.

> sudo apt-get install lm-sensors sensorps-applet hddtem
Then
> sudo apt-get install cpufrequtils lm-sensors
Then
> sudo sensors-detect
selecting yes to all the questions asked....then I reboot to allow every thing to set up properly.

Then back in to terminal

> sensors
Will give you the CPU temps
and
> sudo hddtemp /dev/sda
will give to HD temp

Hope this is helpful

Jim

---

### Post by annahaywood on 2010-10-22
Jim,
Thanks for your reply.

I get my hdd temp, but not my CPU temp, which is really what I want.

I followed your instructions, rebooted and typed in "sensors" to get my CPU temps.
This is the result.

bluetool@bluetool:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.


Any ideas?
  
Thanks,
Anna

---

### Post by annahaywood on 2010-10-22
Also, just so you can see the entire response. This is what happens when I type in sensors and then sensors-detect.  Does this mean our CPUs have no embedded thermal sensors? I thought all CPUs had thermal diodes built in to the circutry??

bluetool@bluetool:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
bluetool@bluetool:~$ sensors-detect
You need to be root to run this script.
bluetool@bluetool:~$ sudo sensors-detect
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: Dell Computer Corporation PowerEdge 1855
# Board: Dell Computer Corporation 0KC123

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): yes
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

---

