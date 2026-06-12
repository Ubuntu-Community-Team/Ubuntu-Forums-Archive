---
title: "Dell  Inspiron 1440 Sound Issues"
date: 2009-09-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by coolparth on 2009-09-06
The Problem : 
I have Kubuntu 9.04 Installed on my new Dell Inspiron 1440. There is absolutely no sound output via speakers or headphones. 

Solutions Tried :
Have tried solutions in various forums & tutorials to no avail. 

Debug Info : 

A. Audio Device (  lspci -v | less l)
> 
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Dell Device 02cf
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at f6afc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel


B. ALSA version ( cat /proc/asound/version)

> Advanced Linux Sound Architecture Driver Version 1.0.18.
Compiled on Sep  6 2009 for kernel 2.6.28-15-generic (SMP).

Note : Have tried upgrading to 1.0.21 by following this tutorial.. 
[http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)
But for some reason it wont upgrade ! Have tried the tutorial thrice. 

Also before i tried the upgrade, i tried this fix. 

> sudo apt-get install module-assistant
 sudo m-a update
 sudo m-a prepare
 sudo m-a a-i alsa


C. aplay -l

> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

D. Codec (cat /proc/asound/card0/codec#* | grep Codec)
> Codec: IDT 92HD81B1X5


Can anyone point me in the right direction ? 

I saw some edits that should be done in /etc/modprobe.d/alsa-base.conf 

But i am not really sure what they should be for my model. 

Thanks! 

Parth

---

### Post by coolparth on 2009-09-07
Update : I have now installed Ubuntu & now Sound works only via Headphones. No Sound via Laptop speakers. 

Also i managed to upgrade ALSA to 1..0.20 but no avail.

---

### Post by garysbasem3nt on 2009-09-22
I'm also having these issues while using Linux Mint - I've done everything you recommended and thanks to you,  I've gotten my headphones to work.  And I'm usually listening to my notebook via headphones - so thank you :]

... but still... any one out there have any advice on how to get these speakers to work?

---

### Post by coolparth on 2009-09-23
As i mentioned earlier .. I switched back to good old Ubuntu.. Upgraded ALSA now both speakers & headphones work but mike does not..

Also i find that i cannot control the sound via the task bar applet.. 

Any suggestions ?

---

### Post by RobiTux on 2009-10-07
I got Dell 1440's sound working - both speakers and headphones

[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/84656](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/84656)

---

### Post by coolparth on 2009-10-08
Ya me too ! Forgot to post it.. 

Upgrading Alsa to 1.021 worked :)

Got all mike as well as speakers working.. But still sometimes Rythombox sometimes cant get which sound card to use..

---

