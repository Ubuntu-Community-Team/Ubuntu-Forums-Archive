---
title: "gmplayer:  can't start mplayer from the applications menu"
date: 2006-11-19
forum: Desktop Environments
---

### Post by tinker123 on 2006-11-19
Hi;

I have never been able to start mplayer from the menu in Ubuntu. 

I peaked inside the menu layout tool and it turns out I am really trying to start gmplayer from the applications menu.

When I type "gmplayer" from the command line I get the follow long winded error message below as to why it can't start.  I don't have a "joystick".  Can I still run gmplayer without one?  How can I get it start up?

Thanks

===================================================
Error Message
===================================================
steve@00400582fa8a:~$ gmplayer
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron 4 Northwood; Pentium 4 EE/Xeon Prestonia,Gallatin (Family: 15, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.



91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
[skin] file ( /usr/share/mplayer/Skin/default/skin ) not found.
Skin not found (default).
steve@00400582fa8a:~$

---

### Post by Quietlife on 2006-11-19
Hi, your problem looks to be that the default skin is missing as seen in your error in these lines :

"
[skin] file ( /usr/share/mplayer/Skin/default/skin ) not found.
Skin not found (default).
"

Silly idea - re-install mplayer-skins ?

---

### Post by tinker123 on 2006-11-19
> **Quietlife said:**
> Hi, your problem looks to be that the default skin is missing as seen in your error in these lines :

"
[skin] file ( /usr/share/mplayer/Skin/default/skin ) not found.
Skin not found (default).
"

Silly idea - re-install mplayer-skins ?

How do I do that?

I never installed gmplayer or mplayer.  If it didn't come with Ubunutu I got it through automatix

---

### Post by Quietlife on 2006-11-19
Sorry not familiar with automatix, but the following may help :

"
sudo apt-get install mplayer-skins
"

Hope it helps

---

### Post by Kramxel on 2007-11-21
Same problem...

> 
MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: Intel Celeron Covington/Pentium II Deschutes,Tonga/Pentium II Xeon (Family: 6, Model: 5, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 0 SSE2: 0
Compiled for x86 CPU with extensions: MMX
[skin] file ( /usr/local/share/mplayer/skins/default/skin ) not found.
Skin not found (default).


I have reinstalled mplayer-skins, although it said it was "already most recent version"

The folder which the skin was supposed to be as a "broken link" to a non-existing "default" skin...


[B]
EDIT:[/B]

I found out that the problem is that the skins are being installed in **/usr/share/mplayer/skins** and mplayer expects them on **/usr/local/share/mplayer/skins**

How do I correct this?


This happened after I reinstalled it using this method:

[http://ubuntuforums.org/showthread.php?t=323181&highlight=asx](http://ubuntuforums.org/showthread.php?t=323181&highlight=asx)

My original problem was with the playback of asx files...


Any help would be appreciated...

---

### Post by Kramxel on 2007-11-21
> **Kramxel said:**
> Same problem...



I have reinstalled mplayer-skins, although it said it was "already most recent version"

The folder which the skin was supposed to be as a "broken link" to a non-existing "default" skin...


[B]
EDIT:[/B]

I found out that the problem is that the skins are being installed in **/usr/share/mplayer/skins** and mplayer expects them on **/usr/local/share/mplayer/skins**

How do I correct this?


This happened after I reinstalled it using this method:

[http://ubuntuforums.org/showthread.php?t=323181&highlight=asx](http://ubuntuforums.org/showthread.php?t=323181&highlight=asx)

My original problem was with the playback of asx files...


Any help would be appreciated...

My problem was I had 2 versions of mplayer installed....

mplayer from repositories and mplayer build by myself....

The solution I found was to install both... and then copy the skins and fonts folder from the repositories install to "my" install...

From here: /usr/share/mplayer/
To here: /usr/local/share/mplayer/

Now everything is working fine....

Tip:
When I type "mplayer" or "gmplayer" in the terminal it goes for the /usr/local/bin/ one....
The repositories one is located in /usr/bin/

---

