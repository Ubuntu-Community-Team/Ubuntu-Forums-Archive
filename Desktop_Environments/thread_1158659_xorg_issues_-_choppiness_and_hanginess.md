---
title: "xorg issues - choppiness and hanginess"
date: 2009-05-13
forum: Desktop Environments
---

### Post by doesntcount on 2009-05-13
After being unsuccessful getting gentoo to recognize my wireless adapter on my T41 thinkpad, I decided to give ubuntu a try and install Jaunty. I must say, it was an impressively easy installation and things seem to "just work" which is a nice change from gentoo :)

However, I am having one issue and it seems to be xorg related. What happens is the mouse gets choppy very often. Doing anything graphics related is choppy. Even scrolling in firefox is choppy. top shows xorg constantly at above 8% and frequently spiking to 13 and occasionally (but not too rarely) to > 60%. I know this laptop is old with it's 1.7GHz celeron processor, but it shouldn't be that bad. Windows XP and Gentoo have run without any issues like this. I'm certain it's a configuration issue or a bug in ubuntu.

In addition to these issues I've had the X hang twice now. Once while watching a video with mplayer. When i CTRL-ALT-BS'ed, I got a screen full of crazy colours and then had to hard reboot.

Any ideas what could be the issue here? I'm not even too sure where to start debugging an issue like this.

Thanks for any help.

p.s. I'm using gnome for now.

---

### Post by aksheyjawa on 2009-05-13
What graphics card do you have?

---

### Post by lethalfang on 2009-05-14
I just noticed the same issue on Ubuntu 9.04 in one of my desktops. 
Xorg is constantly taking 15 - 25% of my CPU power.
I have Dell Dimension 3000 with integrated video card. The system is Pentium 4, 3.0 GHz, 1 GB RAM. 
**Compiz is turned off. **

---

### Post by doesntcount on 2009-05-17
My graphics card is:

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)

and ubuntu has correctly chosen to use the radeon driver, not the ati driver as I incorrectly tried to do with my gentoo installation.

The kernel hang is fairly reproducible while doing a continuous amount of mouse cursor movements through a vncviewer session to another machine on my lan.

As much as I am enjoying the ease of use of ubuntu vs gentoo on my laptop, and dreading the installation process and compilation of all my modules during a gentoo install, this issue is making my ubuntu install fairly unusable. Any help at all is great. Thanks.

---

### Post by aksheyjawa on 2009-05-17
I do not know about your problem. I got a better response when I mailed to ubuntu mailing list. 

Here is the list of all mailing lists- [https://lists.ubuntu.com/](https://lists.ubuntu.com/)
May be you can use ubuntu-users mailing list.

---

### Post by kerry_s on 2009-05-17
in /etc/X11/xorg.conf try disabling dri.

```
Section "Device"
        Option      "DRI" "false"
EndSection


```

---

### Post by doesntcount on 2009-05-18
Thanks for the idea, but it doesn't seem to have worked. Mouse movement is still choppy, and I've reproduced the freeze since disabling DRI.

---

### Post by doesntcount on 2009-05-20
One thing I've noticed is that the choppy mouse isn't actually related to a busy xorg process. Currently my firefox is chewing up 37% and Xorg is using around 20%. Both of these are way too high, I can't imaging why they're so busy, yet my cursor movement is nice and smooth. In fact, after restarting, the movement is fairly smooth and it's only after running for a few minutes that it gets choppy. How long it lasts in a good state after restart varies. Sometimes it only takes a few seconds to degrade, other times, it will be fine for 15minutes.

I'm afraid I have no idea what to debug at this point. Anybody have an idea what's responsible for interpreting mouse input and how I can debug it? Is it xorg's responsibility?

---

### Post by lethalfang on 2009-05-22
I fixed my problem when I rolled back the Xorg intel driver. 
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by doesntcount on 2009-05-24
Great suggestion. Tried it and the cpu usage of xorg has gone away, yet the choppy mouse issue persists. 

Are there special drivers for mouse control on the thinkpad? 

Is anybody else using a thinkpad with ubuntu and having these problems? Or not having these problems?

---

