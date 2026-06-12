---
title: "Log-in Screen Resolution"
date: 2014-12-19
forum: Desktop Environments
---

### Post by rbscairns on 2014-12-19
Using Ubuntu 14.04 with Unity.

I needed to set my screen resolution to 1368x768 (from the default 1024x768) that was not an available option in Settings>Displays. To do this, I installed xrandr and wrote the shell script file /usr/bin/lightdmxrandr.sh
```
#!/bin/sh
xrandr --newmode "1368x768_60.00" 85.86 1368 1440 1584 1800 768 769 772 795 -HSync +Vsync
xrandr --addmode VGA1 1368x768_60.00
```
I then added the following line to /usr/share/lightdm/lightdm,conf.d/50-ubuntu.conf
```
session-setup-script=/usr/bin/lightdmxrandr.sh
```
After rebooting, the log-in screen is displayed at 1024x768 and it is not until after I log in that the screen resolution changes to my desired 1368x768.

How do I get the log-in screen to display at 1368x768 resolution?

---

### Post by carlwsnyder on 2014-12-19
Have you set the default GRUB resolution to 1368x768 in /etc/default/grub ?  Did that help?  Also, your modeline is not the modeline I get from the terminal **cvt 1368 768 60** command.  Mine is the following:```
 cvt 1368 768 60
# 1368x768 59.88 Hz (CVT) hsync: 47.79 kHz; pclk: 85.25 MHz
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
```

---

### Post by rbscairns on 2014-12-20
I am going a little off topic here. When setting up my new default resolution (1368x768), I used gft (not cvt) to get my modeline info:
```
gtf 1368 768 60
# 1368x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 85.86 MHz
Modeline "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
```
I now notice that if I use cvt, I get different modeline info:
```
cvt 1368 768
# 1368x768 59.88 Hz (CVT) hsync: 47.79 kHz; pclk: 85.25 MHz
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
```
I will try using the cvt modelinn info in my .sh file now and see if that helps. Will get back soon with the results.

PS:  I tried the cvt moneline info and found that I lost a few mm of window at the edges of my screen, so I have reverted back the the gtf modeline info.

---

### Post by deadflowr on 2014-12-20
Your script works as it should, The problem is you should look at adding something to the lightdm that will affect the greeter-session.
Session means the session(The actual desktop session) that you would be running AFTER the greeter(login) session.
I think two entries to look at would be 
1)
> display-setup-script = Script to run when starting a greeter session (runs as root)
or 
2)
> greeter-setup-script = Script to run when starting a greeter (runs as root)

---

### Post by rbscairns on 2014-12-20
Thank you for your guidance deadflower.

It would appear that 50-unity.conf is run after the greeter-session, so my lightdmxrandr.sh (that is executed in 50-unity.conf) is also run after the greeter session.

Where should I insert my "session[display or greeter]-setup-script=/usr/bin/lightdmxrandr.sh" so that my .sh file is executed before the greeter (login) session starts?

Remember, I am using Ubnutu 14.04 with unity.

---

### Post by deadflowr on 2014-12-20
You should not muck around with the lightdm files in /usr/share/lightdm/..., but instead make one that would go in /etc/lightdm/lightdm.conf.d/.
14.04 does not come with any lightdm.conf in /etc/lightdm/lightdm.conf.d, so you need to make one yourself.
Any files/entries in that folder, though, will override the ones used in /usr/share/lightdm/...

In the file you make in /etc/... you can have all the command entries for lightdm, all in one file.
I would probably have the entries listed in order I want them to execute.
A good primer here
[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

---

### Post by rbscairns on 2014-12-20
> **deadflowr said:**
> You should not muck around with the lightdm files in /usr/share/lightdm/..., but instead make one that would go in /etc/lightdm/lightdm.conf.d/.
14.04 does not come with any lightdm.conf in /etc/lightdm/lightdm.conf.d, so you need to make one yourself.
Any files/entries in that folder, though, will override the ones used in /usr/share/lightdm/...

In the file you make in /etc/... you can have all the command entries for lightdm, all in one file.
I would probably have the entries listed in order I want them to execute.
A good primer here
[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

I have studied the Lightdm primer here:
[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)
In part, it states:
> LightDM configuration is provided by the following files:

/usr/share/lightdm/lightdm.conf.d/*.conf
/etc/lightdm/lightdm.conf.d/*.conf [COLOR="#FF0000"][does not exist in 14.04][/COLOR]
/etc/lightdm/lightdm.conf [COLOR="#FF0000"][does not exist in 14.04][/COLOR]

System provided configuration is stored in /usr/share/lightdm/lightdm.conf.d/*.conf and is not user editable [COLOR="#FF0000"][yes it is, using "sudo gedit"][/COLOR]. System administrators can override this configuration in /etc/lightdm/lightdm.conf.d/*.conf and /etc/lightdm/lightdm.conf [COLOR="#FF0000"][however, these files do not exist in 14.04][/COLOR]. Files are read in the above order and combined together to make the LightDM configuration [COLOR="#FF0000"][in 14.04, there are only the /usr/share/lightdm.conf.d/*conf files, so I assume that only these files are read to make the LightDM configeration - but in which order?][/COLOR].

For example, if you want to override the system configured default session (provided in /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf) you should make a file /etc/lightdm/lightdm.conf.d/50-myconfig.conf [COLOR="#FF0000"][does this mean I start a new folder /etc/lightdm/lightdm.conf.d and write a 50-myconfig file in that folder?][/COLOR] with the following:

[SeatDefaults]
user-session=mysession

An example file showing all the possible configuration is provided in /usr/share/doc/lightdm/lightdm.conf.gz. 

I also read /usr/share/doc/lightdm/lightdm.conf.gz. This is very helpful - once I know where to put my code.

Dearflower, you could probably solve my problem fairly easily, however I prefer you to just point me in the right direction (as you are doing) to solve my own problem and thus I learn.

---

### Post by deadflowr on 2014-12-21
1)Yes, you need to create the lightdm.conf.d folder as well as the 50-myconfig.conf file in the /etc directory.

2)There is a very simple reason for why it is that the files in /usr/share/lightdm are not editable.
Whenever an update comes for lightdm, which will happen, the new updates will overwrite those files with new files.
Wiping out any changes you have written to them there.
Fortunately, the updates will not overwrite the files in the /etc directory. At least not without warning you that changes can happen.
(Typically whenever a file in the /etc directory needs an upgrade, I get a pop-up window during the update that such a change will happen, at which point
I can accept the new files, or decline them; At my own peril)

3)As far as the actual configuration goes, you can put everything that you need done inside one file.

4)Truth be told this all really seems more or less academic to me, and I would think the resolution problems could be better served by creating and customizing a functional xorg.conf file. Have you tried something like that?

I do not know if any of this is helpful, I hope it is.

---

