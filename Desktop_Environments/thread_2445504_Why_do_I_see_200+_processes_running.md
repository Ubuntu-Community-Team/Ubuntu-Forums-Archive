---
title: "Why do I see 200+ processes running?"
date: 2020-06-15
forum: Desktop Environments
---

### Post by s1van on 2020-06-15
I have a clean installation of 20.04, with xubuntu-desktop, soon after start up, with no application launched, ps-aux shows about 200 processes running.  How many of these processes are absolutely necessary, if I am only going to use a browser (with audio), a terminal and a virt-manager?  In other words, how do I make my desktop lighter and limit the number of processes?  Top screenshots attached.

Thank you.

---

### Post by yaminb on 2020-06-15
Well I guess we should ask a couple questions

1. What number of processes are you expecting?
2. Do you see anything in the process list that looks like you don't need it

I have a pretty stock ubuntu and it's around 300 processes just right now. So, I wouldn't say 200 for Xubuntu would be abnormal.
Some processes are pretty specific too, so a count of the processes isn't actually too valuable in terms of what is being done or saving resources. For example, there's often just a process to handle power management.

A quick browse of your screen shots leads to just a handful of items you could maybe disable, but as Xubuntu is already pretty light, unless you have performance issues, 
Things like evolution (mail/calender), especially if you mainly use web versions like gmail.
Maybe livepatch and snap processes if you really want to play that game.

---

### Post by T6&amp;sfpER35% on 2020-06-15
i think that's pretty normal.
run** htop** in terminal to see to get an overview ,if you don't have **htop** install ```
sudo apt install htop
```

understanding the output from ** htop **[here]("https://www.deonsworld.co.za/2012/12/20/understanding-and-using-htop-monitor-system-resources")

here's a screenshot of my htop ,i'm also on xubuntu

[ATTACH=CONFIG]286227[/ATTACH]

---

### Post by s1van on 2020-06-15
Thank you yaminb for clarifying that these many processes are normal. And, how do I disable a process from starting up on boot?  

As suggested by 3nd, I opened htop and thanks for sharing the screenshot. My htop window shows just about something similar. 

Thank you.

---

### Post by Skaperen on 2020-06-15
i have a crazy xubuntu and it's over 1100 processes right now.  the reason might be due to:
```

lt2a/forums /home/forums 18> who|wc -l
17
lt2a/forums /home/forums 19>
```

---

### Post by The Cog on 2020-06-15
Look at the status (S) column in htop. If it says "S" then that process is sleeping - waiting for some event to wake it up. Each has its own job to do.
There are hundreds of process running by default, some critical, some would only cause minor problems if they died, some you might not even notice if they died. But unless you are very sure what you are doing, I think you should let them be.

---

### Post by Skaperen on 2020-06-15
which process do you want to disable?  there is no one simple answer.  the method depends on which process.  some (most) of them should not be disabled.  some need a lot of steps.  for example, you can disable your mail server unless you send or receive mail that way.

---

### Post by Yellow Pasque on 2020-06-15
> **Skaperen said:**
> There is no one simple answer. 

^Yes, that. I've learned how to cut out a bunch of stuff from a default Xubuntu install, but it took a lot of googling. Synaptic is very useful to see everything you have installed and descriptions. 
Also, this will give you an idea of what is taking longest to start up:
```
systemd-analyze blame
```

Here's my quick and dirty list of packages you can eliminate if you're not interested in the corresponding functionality:
```
BLUETOOTH
blueman	2.1.2-1
bluez	5.53-0ubuntu3
bluez-cups	5.53-0ubuntu3
bluez-obexd	5.53-0ubuntu3

THUNDERBOLT
bolt	0.8-4

ACCESSIBILITY
at-spi2-core
brltty	6.0+dfsg-4ubuntu6
brltty-x11	6.0+dfsg-4ubuntu6
onboard	1.4.1-2ubuntu7
onboard-common	1.4.1-2ubuntu7
onboard-data	1.4.1-2ubuntu7

WEBCAM
cheese-common

PRINTING
cups	2.3.1-9ubuntu1
cups-browsed	1.27.4-1
cups-bsd	2.3.1-9ubuntu1
cups-client	2.3.1-9ubuntu1
cups-common	2.3.1-9ubuntu1
cups-core-drivers	2.3.1-9ubuntu1
cups-daemon	2.3.1-9ubuntu1
cups-filters	1.27.4-1
cups-filters-core-drivers	1.27.4-1
cups-ipp-utils	2.3.1-9ubuntu1
cups-pk-helper	0.2.6-1ubuntu3
cups-ppdc	2.3.1-9ubuntu1
cups-server-common	2.3.1-9ubuntu1
foomatic-db-compressed-ppds
hplip	3.20.3+dfsg0-2
hplip-data	3.20.3+dfsg0-2
system-config-printer	1.5.12-0ubuntu1
system-config-printer-common	1.5.12-0ubuntu1
system-config-printer-udev	1.5.12-0ubuntu1
printer-driver-brlaser	6-1build1
printer-driver-c2esp	27-6
printer-driver-foo2zjs	20171202dfsg0-4
printer-driver-foo2zjs-common	20171202dfsg0-4
printer-driver-hpcups	3.20.3+dfsg0-2
printer-driver-m2300w	0.51-14
printer-driver-min12xxw	0.0.9-11
printer-driver-pnm2ppa	1.13+nondbs-0ubuntu6
printer-driver-postscript-hp	3.20.3+dfsg0-2
printer-driver-ptouch	1.4.2-3
printer-driver-pxljr	1.4+repack0-5
printer-driver-sag-gdi	0.1-7
printer-driver-splix	2.0.0+svn315-7fakesync1build1
python3-cups	1.9.73-3build1
python3-cupshelpers	1.5.12-0ubuntu1
openprinting-ppds

PCMCIA
pcmciautils	018-11

SCANNING
sane-utils	1.0.29-0ubuntu5

TEXT TO SPEECH
espeak	1.48.04+dfsg-8build1
espeak-data:amd64	1.48.04+dfsg-8build1
espeak-ng-data:amd64	1.50+dfsg-6
speech-dispatcher	0.9.1-4
speech-dispatcher-audio-plugins:amd64	0.9.1-4
speech-dispatcher-espeak-ng	0.9.1-4

hddtemp (if you don't care about hard disk or SATA SSD temps)

systemd-timesyncd (if you take care of setting your own system time and don't want to bother with NTP)
```

There are also plenty of other programs, fonts, and such you can get rid of (or switch to lighter alternatives) to save disk space. But it seems like you are asking about how to save RAM and shave boot time.

---

