---
title: "compiz not working after 9.04 upgrade"
date: 2009-04-23
forum: Desktop Environments
---

### Post by b-boy on 2009-04-23
Hi all 

I just upgraded from 8.10 to 9.04 and my compiz stopped working it worked fine on 8.10. Here are my output for **lspci** and **compiz -check**



```
**lspci |[B]grep VGA**[/B]
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
```


```
**compiz -check**
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 
metacity: Unknown option -check
```

---

### Post by GOROSSI on 2009-04-23
Type in terminal sudo gedit /usr/bin/compiz

find the line 

T="$T 8086:2a02 " # Intel GM965

then put a # in front like this

#T="$T 8086:2a02 " # Intel GM965

then save then log out and back in 

then enable by right clicking on the desktop

---

### Post by b-boy on 2009-04-23
thanks for the help but it works quite badly I think I need the driver that was used in 8.10

---

### Post by Sol1 on 2009-04-23
I had the same issue and same video card as you.

When you're done changing xorg.conf logout, log back in, open up a terminal and run "compiz", then open up another terminal and run "emerald --replace" (leave the compiz terminal instance running).  If that works, add them to your Startup Applications.

---

### Post by xitrum1110 on 2009-04-25
> **GOROSSI said:**
> Type in terminal sudo gedit /usr/bin/compiz

find the line 

T="$T 8086:2a02 " # Intel GM965

then put a # in front like this

#T="$T 8086:2a02 " # Intel GM965

then save then log out and back in 

then enable by right clicking on the desktop
Thks GOROSSI! It works like a charm ! (:

---

### Post by revberaldo on 2009-05-03
Thanks!, this worked for me too!

---

### Post by GOROSSI on 2009-05-03
cool if it worked for you :)

if it didn't

you chip might be a different revision try getting the pci id by running compiz in terminal as you will get the log
the full list of blacklisted pci id's are here

[http://wiki.compiz-fusion.org/Hardware/Blacklist]("http://wiki.compiz-fusion.org/Hardware/Blacklist")

the 8.10 drivers are probably worth a try if it doesn't work with your system with this or other methods

---

### Post by Mozes251 on 2009-05-04
Not working for me!!

This is the VGA

```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
```

10x in advanced for helping me.

---

### Post by balboost on 2009-05-04
+1 with Mozes251. i have the same chipset.

btw, i work with metacity + xcompmgr + gnome-do. it's brilliant. stable and fast.

it'll help to wait for the fix, as i choosed to wait for an update from the repos.

---

### Post by rfincher on 2009-05-05
Thanks Gorossi - disabling the line T="$T8086:2a02...... etc solved my problem too. So far everything else i tried in 9.04 seems to work really well, including the Atheros wifi link. Previous upgrades required a complicated patch from madwifi to be reinstalled. Thanks again
Rob

---

### Post by leetspoofer on 2009-05-14
Thanks it work for me too ;)

---

### Post by Laurence94 on 2009-05-16
[LEFT]my problem was similar here is i link to another thread which resloved the problem for me
[http://ubuntuforums.org/showthread.php?p=7289112&posted=1#post7289112](http://ubuntuforums.org/showthread.php?p=7289112&posted=1#post7289112)

hope it works for you
[/LEFT]

---

### Post by sayantandas on 2009-05-23
```
**lspci |[B]grep VGA**[/B]
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400

``````

compiz -check
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
metacity: Unknown option -check

```can anyone help me with this ATI graphics card? i screwed it up while updating the kernel . now i cant get the compiz back.

---

