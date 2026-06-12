---
title: "clock shows the wrong time (not problem with timezone)"
date: 2009-10-14
forum: Desktop Environments
---

### Post by pieman711 on 2009-10-14
When I first moved over to ubuntu from XP I was having problems with the clock in the Gnome panal being about 1 hour fast. Even with the super-user password it wouldn't let me change it. All of a sudden it started working properly, I don't think I changed any thing. 

Now about half a year later it has gone back to being an hour fast again. I haven't changed any settings recently or installed any thing new. 

I googled this problem and it suggested that there was a problem with it handling timezones however when I checked /etc/default/rcS UTC was already set to no.

This time I can change the time as super user but it gives this error:

/sbin/hwclock returned 256

And goes back to being wrong if when I restart my computer.

I'm currently running Intrepid Ibex

---

### Post by pieman711 on 2009-10-15
I just tried to see what th eharsarew clock is set to to see if the problem was with that and this is the readout I got:

pieman@pieman-desktop:~$ hwclock --show
Cannot access the Hardware Clock via any known method.
Use the --debug option to see the details of our search for an access method.
pieman@pieman-desktop:~$ hwclock -r
Cannot access the Hardware Clock via any known method.
Use the --debug option to see the details of our search for an access method.
pieman@pieman-desktop:~$ hwclock --debug
hwclock from util-linux-ng 2.14
hwclock: Open of /dev/rtc failed, errno=2: No such file or directory.
No usable clock interface found.
Cannot access the Hardware Clock via any known method.
pieman@pieman-desktop:~$ 

Is it possible that this could be causing my problem?

---

### Post by Lars Noodén on 2009-10-15
The program 'hwclock' needs special privileges to run.  Try

[indent]
sudo hwclock
[/indent]

What do the logs from ntp or openntpd say in regards to keeping the time in sync?

---

### Post by pieman711 on 2009-10-15
pieman@pieman-desktop:~$ sudo hwclock
[sudo] password for pieman: 
Cannot access the Hardware Clock via any known method.
Use the --debug option to see the details of our search for an access method.
pieman@pieman-desktop:~$ sudo hwclock --debug
hwclock from util-linux-ng 2.14
hwclock: Open of /dev/rtc failed, errno=2: No such file or directory.
No usable clock interface found.
Cannot access the Hardware Clock via any known method.

I get the same output using sudo. Where would I find the ntp logs?

---

### Post by Lars Noodén on 2009-10-18
> **pieman711 said:**
> $ sudo hwclock --debug
hwclock from util-linux-ng 2.14
hwclock: Open of /dev/rtc failed, errno=2: No such file or directory.
No usable clock interface found.
Cannot access the Hardware Clock via any known method.

I get the same output using sudo. 

Hmm. Strange.  What does a directory listing of /dev/ show in regards to the clock?

[indent]
$ ls -lhi /dev/rt*
1517 lrwxrwxrwx 1 root root      4 2009-10-18 10:41 /dev/rtc -> rtc0
1515 crw-rw---- 1 root root 254, 0 2009-10-18 10:41 /dev/rtc0
[/indent]

> **pieman711 said:**
> Where would I find the ntp logs?

Usually in /var/log/daemon.log

---

### Post by pieman711 on 2009-11-02
Sorry I've been away for a bit.
The plot thickens... I booted in windows for the first time in ages (I probably should have mentioned that I dual boot XP/ubuntu 8.10) and now the time is correct, however I still can't access the hwclock and just get the same problems as before.

typing ls -lhi /dev/rt* into a terminal gave this:

pieman@pieman-desktop:~$ ls -lhi /dev/rt*
ls: cannot access /dev/rt*: No such file or directory

Is there anything I am particularly looking for in daemon.log? there is a lot of information there, mostly network information but i cant see anything specifically for time management. eg.

Nov  2 15:03:08 pieman-desktop avahi-daemon[4903]: Registering new address record for 192.168.1.7 on eth0.IPv4.
Nov  2 15:03:08 pieman-desktop dhclient: bound to 192.168.1.7 -- renewal in 34627 seconds.

---

### Post by Lars Noodén on 2009-11-02
The hardware clock utilities are in the package util-linux.  You might try reinstalling that.  *maybe* that will recreate the device.  

[INDENT][FONT="Courier New"]sudo apt-get --reinstall install util-linux[/FONT][/INDENT]

This is what rtc looks like on karmic for amd64:

[INDENT][FONT="Courier New"]$ ls -l /dev/rtc /dev/rtc0
lrwxrwxrwx 1 root root      4 2009-11-02 10:33 /dev/rtc -> rtc0
crw-rw---- 1 root root 254, 0 2009-11-02 10:33 /dev/rtc0
[/FONT][/INDENT]

Riskier, boot to a rescue cd, mount the hardrive and go into /dev and re-create the missing device:

---

### Post by pieman711 on 2009-11-03
Reinstalling util didn't help. As far as I can tell nothing happened. 
In my dev directory I don't have any thing that has an rt anywhere in the name, I could give a print out of ls -l /dev but there's alot of stuff in there.

---

### Post by johnyjamesz on 2009-11-05
The system may think that the hardware click is set to the UTC time zone, while it is set to the local time zone. To tell the system that the hardware clock is set to the local time zone just run the command: ```
sudo hwclock --localtime
```and to set the system time from the hardware clock run: ```
sudo hwclock -s
```hope this helps.

---

### Post by pieman711 on 2009-11-05
I don't think it is a problem with the time zones. Since I've booted in windows and back to ubuntu the time is now right, although I don't know why. I aslo still get an error when I try to do anything with hwclock...


pieman@pieman-desktop:~$ sudo hwclock --localtime
[sudo] password for pieman: 
Cannot access the Hardware Clock via any known method.
Use the --debug option to see the details of our search for an access method.

pieman@pieman-desktop:~$ sudo hwclock -s
Cannot access the Hardware Clock via any known method.
Use the --debug option to see the details of our search for an access method.

---

### Post by johnyjamesz on 2009-11-05
[http://www.garyshood.com/systemclock/](http://www.garyshood.com/systemclock/)
This link may help you access hwclock.

---

### Post by pieman711 on 2009-11-19
Still no good...


pieman@pieman-desktop:~$ modprobe rtc-cmos
FATAL: Module rtc_cmos not found.
pieman@pieman-desktop:~$

---

### Post by ScottMinster on 2009-11-19
> **pieman711 said:**
> When I first moved over to ubuntu from XP I was having problems with the clock in the Gnome panal being about 1 hour fast. Even with the super-user password it wouldn't let me change it. All of a sudden it started working properly, I don't think I changed any thing. 

Now about half a year later it has gone back to being an hour fast again. I haven't changed any settings recently or installed any thing new. 


I don't know about your /dev/rtc* missing, but this to me sounds like a daylight saving time problem (half the year it's an hour fast).  Do you observe DST?  If you don't, maybe you have set a timezone/locale that does observe it.  It's also possible that your hardware is automatically adjusting for DST, though I don't think I've ever heard of a computer clock that does that.

Another possibility is that it's Windows doing the adjusting when you boot to it.  IIRC, Windows stores the local time in the hardware clock, not UTC.  So, when the DST change comes, Windows may adjust the time as it thinks appropriate.  There may be something else funny going on there.

It's weird that you cannot adjust the time at all on Linux.  Can you adjust it in Windows?  Does Windows have the "auto adjust for DST" option set?  Maybe try turning that off?

---

### Post by pieman711 on 2009-11-20
I'm in England and we do adjust for DST here. The clock changes didn't happen at the right time to coincide with DST so I don't think it was that. I think you are right that Windows did set the hardware clock when I booted into it, I'm not sure how it managed to get an hour off in the first place though.

---

### Post by pieman711 on 2010-05-19
Sorry to dig up this old thread again, but I never got to the bottom of it. I'm a bit more experienced now and thought I'd have another go. 
When I adjust the clock by right clicking on it in the gnome panel and clicking 'adjust system time' it says 'failed to set teh system time /sbin/hwclock returned 256' like it used to. It changes the time on my ubuntu until I turn it off and back on again then it goes out by an hour again. From some time on google and the previous posts I think the problem is the hardware clock being wrong and linux not being able to correct it, then when l start ubuntu it loads the wrong Hardware Clock time into the system time. 
these are some terminal outputs I get from hwclock.

pieman@pieman-desktop:~$ hwclock --show
Cannot access the Hardware Clock via any known method.
Use the --debug option to see the details of our search for an access method.

pieman@pieman-desktop:~$ hwclock --debug
hwclock from util-linux-ng 2.14
hwclock: Open of /dev/rtc failed, errno=2: No such file or directory.
No usable clock interface found.
Cannot access the Hardware Clock via any known method.

---

