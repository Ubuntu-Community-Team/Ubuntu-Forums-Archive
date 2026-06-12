---
title: "Dell mini 10v wireless behaving strangely"
date: 2009-08-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Stratus_Hunter on 2009-08-19
Hi everyone
Im a new member and a newbie to ubuntu so please bear with me :S
I recieved a new Dell mini 10v and quickly installed a fresh copy of ubuntu 9.04
Ive since been spending all my time trying to get the wireless to work correctly.
The wired connection works perfectly. The broadcom wifi drivers are installed and activated under the system-> administration -> hardware drivers    section.
The strangest thing of all is that it connects to the wireless network (that has no protection) says that everything is all fine but cant load up any webpages. 
Everything has been updated in the update manager.
The oddest thing of all is that yesterday I managed to connect online once or twice. It was after I deleted all the wifi profiles and turned the enable wireless tick on and off (by right clicking on the wireless connection icon in the top right) Then making a new wireless profile. (I even rebooted several times to check it wasnt something one off in the settings)
However today I have tried the same tricks and nothing is happening.

I am using a dlink DSL-G624T  I have looked on some forums and read about similar issues and it was a wireless router problem as opposed to the laptop, does that sound possible? Im hoping to test it on some different wireless networks asap and see if its that error.

Thanks in advance :D

---

### Post by MartynT on 2009-08-23
I feel your pain.  I too have a 10v that seems to want to ruin my life by refusing to establish a wireless connection. :P

Yesterday it wouldn't connect at all and I finally got it going by dropping dhcp and using a fixed IP.

All described here [http://ubuntuforums.org/showthread.php?t=1234714]("http://ubuntuforums.org/showthread.php?t=1234714")

You can watch your wireless card's connection attempts in the syslog ....
System -> Administration -> System Log

If you find any solutions please post them back here.  You are not alone.  Several of us are having troubles.

---

