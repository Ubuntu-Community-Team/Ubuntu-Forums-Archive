---
title: "Unbuntu 9.10 on Dell Precision M6500"
date: 2010-04-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by phico on 2010-04-03
Hello,

I begin a thread about Ubuntu 9.10 on Dell Precision M6500.

Both 32bit & 64bit versions install without any problem.

To get 32bit with PAE support (PAE is usefull to access more that 4G Ram)
you MUST be connected to the LAN during installation (if not connected you
end up with the standard "non pae" kernel)

Everthing works out of the box except the microphone.

After installation go to :
System>Administration>Hardware Driver
1. install the two BroadCom driver in the order they appears
2. install ATI video driver

WORKING

V - All CPUs supported
V - All RAM supported with either 32 bit + PAE or 64 bit version
V - Video card ATI FirePro M7740 after driver installation
V - Wifi (Dell Wireless 1510) working after driver installation
V - Bluetooth  (was able to pair and send a file to my phone)
V - Webcam 
V - Sound (except microphone see below)
V - Touchpad. Touchpad scrolling.
V - Keyboard backlight and its Fn Key 
V - Wifi/Bluetooth button 
V - Calc button 
V - Light sensor 
V - Brightness Fn Keys with screen widget
V - Sound volume buttons with screen widget

V - Suspend (pause Fn Key works)
V - Hibernate 

NOT WORKING

X - Microphone not working 
(I tried installing linux-backports-modules-alsa but none
internal neither external mic works)
Please help if you have any idea ..

UPDATE
V - Microphone working since laste udate

NOT TESTED

x - eSATA port

---

### Post by phico on 2010-04-08
Microphone works also since laste udate

---

### Post by emptythevoid on 2010-04-15
I'm running 9.10 (32bit) on an M6500 and I'm having all kinds of trouble burning CDs and DVDs.  Are you able to replicate any failures when burning CD/DVDs?  I'd highly appreciate your observations.

---

### Post by MisterVince on 2010-04-26
Hi,
 
Same problem for me. I am not able to burn CD or DVD on Ubuntu 9.10. 
No burner is detected by k3B nor Brasero.
 
Good luck ! ;)

---

### Post by emptythevoid on 2010-04-26
I'm curious to see how 10.04 works.  I tried a beta of it (installed to a flashdrive) and still experienced issues.

---

### Post by atkaper on 2010-04-27
I'm currently running ubuntu 10.04 on my dell M6500, but no working internal microphone... Most of the rest seems to run fine, I'm quite impressed by this (beta) release! (although in open office, and some other app's the dark font on black background is completely unreadable).

For the microphone, I already tried installing different pulse audio mixers / device choosers, and as suggested in another thread turning off one of the microphone inputs (unlocking the stereo sliders, and moving one down). Also tried installing the ppa.launchpad.net ubuntu-audio-dev drivers.
No luck...

So if anyone has any other suggestions, please let me know.

Thanks & Greetings,
   Thijs.

---

### Post by phico on 2010-04-28
Sorry I have not tried yet to burn a CD on this machine.
I'll try soon and let you know.
I also plan to swith to ubuntu 10.04 final release tomorrow

---

### Post by phico on 2010-04-29
My DVD works.  I was able to burn Ubuntu 10.04 with
Brasero.  I must say I have the Drive Tray DVD (the 
one which go out of the laptop)

---

### Post by kthari85 on 2010-05-01
Yes, I too upgraded to the new 10.04 . I am using Dell Vostro 1510 , the external mic is not working for me too :( .
Let me google and try something and will let you know if figured , else please let me know it too.

---

### Post by alobo on 2010-05-05
I cannot install the ATI video driver, it starts "Downloading and installing driver..." but never ends. After a long time I get: "SystemError: InstallArchives() Failed"

Can I download the driver from any web site?

Thanks

Agus

> **phico said:**
> Hello,

I begin a thread about Ubuntu 9.10 on Dell Precision M6500.

Both 32bit & 64bit versions install without any problem.

To get 32bit with PAE support (PAE is usefull to access more that 4G Ram)
you MUST be connected to the LAN during installation (if not connected you
end up with the standard "non pae" kernel)

Everthing works out of the box except the microphone.

After installation go to :
System>Administration>Hardware Driver
1. install the two BroadCom driver in the order they appears
2. install ATI video driver

WORKING

V - All CPUs supported
V - All RAM supported with either 32 bit + PAE or 64 bit version
V - Video card ATI FirePro M7740 after driver installation
V - Wifi (Dell Wireless 1510) working after driver installation
V - Bluetooth  (was able to pair and send a file to my phone)
V - Webcam 
V - Sound (except microphone see below)
V - Touchpad. Touchpad scrolling.
V - Keyboard backlight and its Fn Key 
V - Wifi/Bluetooth button 
V - Calc button 
V - Light sensor 
V - Brightness Fn Keys with screen widget
V - Sound volume buttons with screen widget

V - Suspend (pause Fn Key works)
V - Hibernate 

NOT WORKING

X - Microphone not working 
(I tried installing linux-backports-modules-alsa but none
internal neither external mic works)
Please help if you have any idea ..

UPDATE
V - Microphone working since laste udate

NOT TESTED

x - eSATA port

---

### Post by alobo on 2010-05-05
Worked the next time, maybe it was connection problem. Had to
restart as noted by the installation tool and works fine now.

I'm using 9.10, any experiences with 10.04 on this machine?
Thanks
Agus

---

### Post by alobo on 2010-05-06
My SD driver does not mount the SD card unless it is inserted before starting the machine.

Does anybody else have experienced the same problem?

Using ubuntu 9.10

Agus

> **phico said:**
> Hello,

I begin a thread about Ubuntu 9.10 on Dell Precision M6500.

Both 32bit & 64bit versions install without any problem.

To get 32bit with PAE support (PAE is usefull to access more that 4G Ram)
you MUST be connected to the LAN during installation (if not connected you
end up with the standard "non pae" kernel)

Everthing works out of the box except the microphone.

After installation go to :
System>Administration>Hardware Driver
1. install the two BroadCom driver in the order they appears
2. install ATI video driver

WORKING

V - All CPUs supported
V - All RAM supported with either 32 bit + PAE or 64 bit version
V - Video card ATI FirePro M7740 after driver installation
V - Wifi (Dell Wireless 1510) working after driver installation
V - Bluetooth  (was able to pair and send a file to my phone)
V - Webcam 
V - Sound (except microphone see below)
V - Touchpad. Touchpad scrolling.
V - Keyboard backlight and its Fn Key 
V - Wifi/Bluetooth button 
V - Calc button 
V - Light sensor 
V - Brightness Fn Keys with screen widget
V - Sound volume buttons with screen widget

V - Suspend (pause Fn Key works)
V - Hibernate 

NOT WORKING

X - Microphone not working 
(I tried installing linux-backports-modules-alsa but none
internal neither external mic works)
Please help if you have any idea ..

UPDATE
V - Microphone working since laste udate

NOT TESTED

x - eSATA port

---

### Post by zaphod777 on 2010-05-06
In 10.04 I had to remove and re-install Alsa to fix my mic on my 1530.

For those with the M6500 just curious how much you spent I checked and they are buko bucks. 

I wan't to find a slim laptop with a Core i7, SSD, and no CD Drive.

---

### Post by emptythevoid on 2010-05-13
My SD card slot works normally on 9.10.

My work bought my (their) m6500.  I wouldn't have spend this much money on a personal laptop. It was about $2500 or so.  It replaced my Lenovo Thinkpad T61.

---

### Post by emptythevoid on 2010-05-19
I just upgraded my m6500 to Ubuntu 10.04 (not a fresh install) and the DVD burner seems to be working normally using Brasero.  The only thing it can't do is automatically eject the disc (not a big deal).  It feels good to be able to burn CDs and DVDs again.

---

### Post by atkaper on 2010-05-20
Any success with the internal microphone on your 6500 with 10.04 ? Mine is still not working...

---

### Post by emptythevoid on 2010-05-20
Sadly, no.  I went through all the hardware profiles and inputs in the sound preferences.  I'll let you know if I discover anything

---

### Post by zzzqzzz on 2010-06-07
I just installed 10.04 x64 (fresh install). 
Biggest challenge was to use on-board raid controller,  10.04 has some serious problems about using hardware raid. Anyway, everything seems to be fine right now.

I just did  a quick check for sound; Internal mic. seems to be not working, on the other hand external mic is working fine.

---

### Post by elotter on 2010-06-17
Same here, we have two machines (Dell Precision M6500) here with Ubuntu 10.04 (64-bit, fresh install) - for both the internal mic seems to not be working, but plugging in an external mic works fine. Any ideas on how to get the internal mic working? As far as I remember, it did work at some stage in 9.10 - so some recent update must have killed it off.

---

### Post by ramsrambo on 2010-06-18
Please refer to [http://ubuntuforums.org/showthread.php?t=1509957](http://ubuntuforums.org/showthread.php?t=1509957) and it does not even boot can you give me some ideas to get this 10.04 64 bit workin?

---

### Post by Gargoulf on 2010-07-05
Hi,
Same here. M6500 with ubuntu 10.04 32-bit, fresh install. I tried different alsa drivers without success.
Built-in microphone still not working. Has anyone find a solution to this annoying problem? 
Thanks.

---

### Post by zaphod777 on 2010-07-05
On my Dell XPS 1530 I had to completely uninstall and reinstall Also to get it to work. 

There are also a few other solutions on this thread.   
[http://ubuntuforums.org/showthread.php?t=1466096](http://ubuntuforums.org/showthread.php?t=1466096)

---

### Post by Gargoulf on 2010-07-06
Hi,
Just tried what you said and resinstalled ALSA following your link.
Sadly, after rebooting, got no sound at all (neither microphone nor speakers). I reinstalled linux-backports-modules-alsa-lucid-generic-pae and after rebootig, speakers work back. But built-in microphone is still NOT working on my dell precision M6500 with ubuntu 10.04 32-bit.

Has anyone succeded in making this mic work for M6500 under ubuntu? Seems some people were able to do this with 9.10 (begining of this post)...so why isn it working under 10.04?

---

### Post by atkaper on 2010-07-06
I tried the reinstall also on my M6500, but no luck...

---

### Post by Gargoulf on 2010-07-13
Hi, 

Since this post was for ubuntu 9.10, I started a fresh one for 10.04 on M6500

[http://ubuntuforums.org/showthread.php?p=9584042#post9584042](http://ubuntuforums.org/showthread.php?p=9584042#post9584042)

Please visit and comment!

---

