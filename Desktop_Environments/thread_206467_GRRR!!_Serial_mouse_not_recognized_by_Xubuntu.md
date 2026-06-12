---
title: "GRRR!! Serial mouse not recognized by Xubuntu"
date: 2006-06-30
forum: Desktop Environments
---

### Post by coyotito on 2006-06-30
Major pain in the behind as I installed Xubuntu on my old AT standard AMD 400 machine: the serial mouse, which at least used to be a VERY common device was not recognized, did not even appear in the X configuration program when i did 
dpkg-reconfigure..

--Without a mouse you're pretty helpless when the GUI comes up..
..had to do Alt-F2 to get the run program dialog up, then 
#sudo vi /etc/X11/xorg.conf
and set the mouse to device /dev/ttyS1 (happened to be in com2), comment out the crap about wacoms, styluses and whatnot and THEN I had a mouse.

Not good enough, this is sufficient to make many people new to linux give up,
and Ubuntu is supposed to be usable for beginners and Xubuntu is supposed to run on low-end hardware (in addition to tablet pc's etc) -?

---

### Post by todoporron on 2006-08-24
Well I had the same problem on a PII 400 Mhz... this procedure solved the problem.

I totally agree with you, this issue should be fixed ASAP, otherwise this will keep newbies (like me) away from linux.

Thanks.

---

### Post by nathanbriggs on 2006-09-26
Sometimes even that doesn't work

I tried
mdetect -v
and got
 /dev/ttyS0
 /dev/ttys1
 /dev/psaux
intellimouse on psaux
but it isn't its a microsoft mouse of ttyS1
editing /etc/X11/xorg.conf for any posible combination of the above doesn't work
using inputattach as here
[https://launchpad.net/distros/ubuntu/+source/xorg/+bug/9068](https://launchpad.net/distros/ubuntu/+source/xorg/+bug/9068)
also doesn't work
either get input/output error or line control error or no response at all
so for my old P200 with a serial mouse I'm going to another distro <sigh>

---

### Post by srf21c on 2006-10-21
I was having a similar problem with Xubuntu 6.06 on an older Dell Dimension using a logitech 3-button serial mouse on COM1.  Eventually I got it working by modifying xorg.org to read as follows

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/ttyS0"
        Option          "Protocol"              "Auto"
EndSection

Note that I have removed the "Z axis mapping", and "emulate 3 buttons" options, I have not tested to see if that really makes much difference, but I do not believe these options are necessary with a 3 button serial mouse w/no scroll wheel.

During the course of troubleshooting the error, I had experimented with loading inputattach from /etc/rc.local.  Interestingly, once I got the xorg.conf configuration right, inputattach actually caused to mouse to  *stop* working shortly after the login screen appeared.  Once I commented out inputattach from /etc/rc.local, the mouse worked properly after logging into the xubuntu 6.06 desktop.

---

### Post by leopard6661 on 2006-10-31
I have the same problem, I tried using Alt+F2, the run window opened but when I typed #sudo vi /etc/X11/xorg.conf all I get was a run error saying :the command failed to run, text was empty (or contained only whitespace)
I am a complete nupe to Linux and xubuntu, I was hoping any one can help 
please, without the mouse I cant use the computer at all
thanx in advance

---

### Post by iamhugeinjapan on 2006-10-31
No ps/2 ports to plug a $5 mouse into?

---

### Post by leopard6661 on 2006-10-31
IT WORKED
finally after a lot of reading, failed trials and total reinstalling of xubuntu....my mouse worked. here is how
I hit Alt+Ctrl+F2, logged in, wrote sudo vi /etc/X11/xorg.conf
then, i was asked for password, then edited the mouse sector to be
Device "dev/ttys0"
protocol "Auto"
saved and exited, restarted 
and voila it worked 
thanx for the help

---

### Post by dheerajsp on 2006-10-31
> **srf21c said:**
> I was having a similar problem with Xubuntu 6.06 on an older Dell Dimension using a logitech 3-button serial mouse on COM1.  Eventually I got it working by modifying xorg.org to read as follows

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/ttyS0"
        Option          "Protocol"              "Auto"
EndSection

Note that I have removed the "Z axis mapping", and "emulate 3 buttons" options, I have not tested to see if that really makes much difference, but I do not believe these options are necessary with a 3 button serial mouse w/no scroll wheel.

During the course of troubleshooting the error, I had experimented with loading inputattach from /etc/rc.local.  Interestingly, once I got the xorg.conf configuration right, inputattach actually caused to mouse to  *stop* working shortly after the login screen appeared.  Once I commented out inputattach from /etc/rc.local, the mouse worked properly after logging into the xubuntu 6.06 desktop.
i wanted to ask, what dows the Z axis mapping do?

---

### Post by srf21c on 2006-12-10
To the best of my knowledge z axis mapping is for mouse wheel support.

---

### Post by Shinoda on 2007-11-03
For me [FONT=Courier New]Auto[/FONT] doesn't work, whereas [FONT=Courier New]Microsoft[/FONT] does.
> **leopard6661 said:**
> I have the same problem, I tried using Alt+F2, the run window opened but when I typed #sudo vi /etc/X11/xorg.conf all I get was a run error saying :the command failed to run, text was empty (or contained only whitespace)
Should've been
```
gksudo mousepad /etc/X11/xorg.conf
```
Alternatively run [FONT=Courier New]xfce4-terminal[/FONT] to open up a terminal.

---

