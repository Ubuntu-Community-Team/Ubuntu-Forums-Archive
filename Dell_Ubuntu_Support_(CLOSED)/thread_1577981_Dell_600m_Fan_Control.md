---
title: "Dell 600m Fan Control"
date: 2010-09-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by The Squirrel Unit on 2010-09-19
Greetings,
             I am a new Ubuntu convert and am loving it. Suck it, Bill Gates! Anyway...I'm running a 5 year old Dell Inspiron 600m. Seeing as how it's 5 years old things tend to get a little hot :twisted:...no surprise there. However, for whatever reason my fans don't start working hard until my CPU hits ~85 C. This is a little high for me and I am trying to configure the fans to work harder at lower temps.

             I tried running the detect-sensors command in lm-sensors and it came back with no sensors detected. Is this a problem specific to the 600m ( no sensors for this application)? 

             As well as lms I downloaded/installed the i8kutils and enabled the plug in for gkrellm...the only sensors it detects/displays is basic CPU temp. So I tried running pwmconfig but my system tells me I need to be 'root' to run this command. Being new to Linux/Ubuntu and not very good with code I'm a little nervous to go that route. As a last resort I looked into running speed fan through WINE, but apparently WINE doesn't like speed fan.

           Any suggestions appreciated.

Thanks,
             TSU /endblog

PS- I searched this forum but didn't find anything similar under '600m'.

---

### Post by jcolyn on 2010-09-19
The 600m does not have fan sensors just cpu and hard drive sensors. First make sure lm-sensors is installed ```
sudo apt-get install lm-sensors
``` then You need to run ```
sensors-detect
``` at the terminal and answer yes to all of the questions. Then to check cpu temp type ```
sensors
``` to get a true reading of cpu temp.

What are you running that raises the cpu temp so high? Are you sure the fan is working properly?

Try cleaning the fan/heatsink/vents with compressed air to remove any dust that might be clogging it..

I have the same model and it runs between 35-45C tops even with two or more programs running.

---

### Post by jcolyn on 2010-09-19
If you also want to check hard drive temp make sure hddtemp is installed ```
sudo apt-get install hddtemp
``` then ```
sudo gedit /etc/default/hddtemp
```Change the values in your hddtemp file to match the values in the below example. 


```
# Defaults for hddtemp initscript (/etc/init.d/hddtemp)
# This is a POSIX shell fragment

# [automatically edited by postinst, do not change line format ]

# hddtemp network daemon switch. If set to true, hddtemp will listen
# for incoming connections.
RUN_DAEMON="true"

# List of devices you want to use with hddtemp. If none specified,
# hddtemp will probe standard devices.
 DISKS="/dev/hda /dev/sda"

# List of devices you want to use with hddtemp, but that would not be
# probed for a working sensor.
DISKS_NOPROBE=""

# IP address of the interface on which you want hddtemp to be bound
# on. If none specified, goes to 127.0.0.1. Use 0.0.0.0 to bind hddtemp
# on all interfaces.
INTERFACE="127.0.0.1"

# Port number on which you want hddtemp to listen on. If none specified,
# the port 7634 is used.
PORT="7634"

# Database file to use. If none specified, /etc/hddtemp.db is used.
#DATABASE="/etc/hddtemp.db"

# Separator to use between fields. The default separator is '|'.
#SEPARATOR="|"

# Logging period (in seconds) for the temperatures. If set to a value
# different than 0, hddtemp will run as a daemon periodically logging
# the temperatures through syslog
RUN_SYSLOG="300"

# Other options to pass to hddtemp
OPTIONS=""
```Once done reboot then to check hard drive temp type ```
sudo hddtemp /dev/sda
```

---

### Post by The Squirrel Unit on 2010-09-19
Thanks for the quick reply! 

 I kind of figured that maybe it didn't have the right sensors. As far as it getting hot, maybe it is a dust problem. The fans are usually running at a fairly low RPM and then start to really work, so there is nothing obviously (to me) wrong with them. I have not opened it up, but have tried to clean the vents. I don't run anything really taxing when it gets hot. Just using grooveshark and nothing else it usually runs ~75 C. My 600m suffers from the problem of not wanting to fully wake up after sleep/hibernation so it stays active/warm for long periods of time.

Thanks again!
TSU

---

### Post by jcolyn on 2010-09-19
If you haven't already done it try upgrading the ram to 1GB. If you can afford it go with 2GB. This will max out this model with ram and it will run a lot better.

I've tried all of the different Ubuntu distros on this laptop and Ubuntu with the Gnome DE seems to be the best suited..or Linux Mint 9 Gnome 32 bit is by far the best I've used on this model which is what it is running now..

---

### Post by The Squirrel Unit on 2010-09-25
So......I cleaned out the vents and that seems to have made a noticeable difference (shocking I know.) I followed your advice with regards to the hddtemp app, and it works. I can see the temp when I run the /dev/sba command but for some reason the sensors applet doesn't see the hddtemp sensor. Any thoughts? The only things that I changed were the IP addy and the testing interval.

Thanks,
          TSU

---

### Post by jcolyn on 2010-09-26
> **The Squirrel Unit said:**
> So......I cleaned out the vents and that seems to have made a noticeable difference (shocking I know.) I followed your advice with regards to the hddtemp app, and it works. I can see the temp when I run the /dev/sba command but for some reason the sensors applet doesn't see the hddtemp sensor. Any thoughts? The only things that I changed were the IP addy and the testing interval.

Thanks,
          TSU

When you edited your /etc/default/hddtemp did you uncomment the below line?

```
#List of devices you want to use hddtemp. If none specified
#hddtemp will probe standard devices.
DISKS="/dev/hda /dev/sda"
```

be sure your hard drive is /dev/hda, /dev/sda, /dev/sdb, etc and is listed in the DISK= line. If not add it.

---

