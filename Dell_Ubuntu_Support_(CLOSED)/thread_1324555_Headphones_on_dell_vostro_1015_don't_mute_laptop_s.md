---
title: "Headphones on dell vostro 1015 don't mute laptop speakers"
date: 2009-11-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by LProf on 2009-11-12
Help please. Headphones on dell vostro 1015 don't mute laptop speakers. I tried to install ubuntu 9.10 (vanilla) and try install basic linuxant driver, but did not help. Now installed ubuntu Dell 9.04 iso, 
but the problem remains. I apologize for my English and thank you in advance for any help.

> aplay -l
**** &#1057;&#1087;&#1080;&#1089;&#1086;&#1082; PLAYBACK &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074; ****
&#1082;&#1072;&#1088;&#1090;&#1072; 0: Intel [HDA Intel], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 0: HDA Generic [HDA Generic]
 &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
 &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0

> cat /proc/asound/card0/codec#* | grep Codec
Codec: Conexant ID 5067

---

### Post by nongentesimus on 2009-11-15
Hello!

I have the same notebook (vostro 1015), same Ubuntu (9.10) and the same problem. I tried plenty of settings following this forum-guide:
[http://ubuntuforums.org/showthread.php?p=6573913#poststop](http://ubuntuforums.org/showthread.php?p=6573913#poststop)
but sorrowfully non of them worked. 
Do you think there is any way of muting my speakers (naturally without destroying my hardware)? I wouldn't even mind if my speakers had no sound at all as far as my headphones work...
Or any other idea?
Thanks

Peter

---

### Post by nongentesimus on 2009-12-31
For anyone reading this, problem is mainly solved on this forum:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/477154](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/477154)

To put it breafly, the simpliest solution is to install hda-verb with theese commands

1. wget [http://ftp.kernel.org/pub/linux/kernel/people/tiwai/misc/hda-verb/hda-verb-0.3.tar.gz](http://ftp.kernel.org/pub/linux/kernel/people/tiwai/misc/hda-verb/hda-verb-0.3.tar.gz)
2. cd hda-verb-0.3
3. make
4. sudo cp hda-verb /usr/local/bin

and after that the command
```
sudo hda-verb /dev/snd/hwC0D0 0x1f SET_PIN_WIDGET_CONTROL 0x0
```
will mute the speaker,
and the command
```
hda-verb /dev/snd/hwC0D0 0x1f SET_PIN_WIDGET_CONTROL 0x40
```
will unmute it.
It's easy to write a simple bash-script which mutes the speaker if it is unmuted, and unmutes it if it is muted.
The script will look like this:


```
#/bin/bash
if [  $(/usr/local/bin/hda-verb /dev/snd/hwC0D0 0x1f GET_PIN_WIDGET_CONTROL 0x0 | grep 0x0 | wc -l)  = 1 ];then hda-verb /dev/snd/hwC0D0 0x1f SET_PIN_WIDGET_CONTROL 0x40;
echo 'unmuted';
else hda-verb /dev/snd/hwC0D0 0x1f SET_PIN_WIDGET_CONTROL 0x0;
fi
```

and you shuld run it with sudo.
Good news is that the whole problem should be fixed in kernel 2.6.33.

---

### Post by zsitvaij on 2010-01-01
Another workaround:
1. add ppa:zsitvaij/ppa-zsitvaij to your software sources
2. install linux-backports-modules-alsa-karmic-generic
3. reboot

This way you'll get the backports package with upstream patches for CX20583 (Conexant 5067) applied.

Reportedly, it should also work if you have a Vostro 1220 or Toshiba Qosmio X500 if you add the following to the end of /etc/modprobe.d/alsa-base.conf: 
options snd-hda-intel model=dell-vostro

---

### Post by xeribii on 2010-01-28
I have a Dell Vostro 1088 with Conexant ID 5067 and have been looking for the solution since I bought this laptop in Sepetember last year!

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

I'm running Ubuntu 9.10.

zsitvaij's solution doesn't work for me but nongentesimus's solution is the only solution I've ever found on the web that actually WORKS for me!  Hopefully ALSA will release a patch soon.

Thanks a lot!!!

---

### Post by juandadamo on 2010-02-18
zsitvaij solution works just fine in my Vostro 1015, I just added the repo, actualise and reboot. thanks for your work!

Juan

---

### Post by freechelmi on 2010-03-07
hello I plan to buy a FreeDos Vostro 1015 and run Ubuntu. Do you know if this issue is solved in Lucid? 

It's weird because in a lot of countries Dell sell this 1015 with Ubuntu Preinstalled but I could not find the recovery ISO image which would tell us what trick they use.

---

### Post by Kobsonn on 2010-04-16
I had same problem on Ubuntu 9.04, and my solution was
1) upgrading to 2.6.28-18-generic kernel by usual update mechanism
2) manual installation of [alsa-driver-1.0.22.1]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.22.1.tar.bz2").
Now Dell's vostro 1015 laptop speakers works properly.

---

### Post by charding on 2010-05-28
I have a vostro 1220 with 9.10 and this script worked. A nice work around, thanks! Will wait for new kernel for this fix..



> **nongentesimus said:**
> For anyone reading this, problem is mainly solved on this forum:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/477154](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/477154)

To put it breafly, the simpliest solution is to install hda-verb with theese commands

1. wget [http://ftp.kernel.org/pub/linux/kernel/people/tiwai/misc/hda-verb/hda-verb-0.3.tar.gz](http://ftp.kernel.org/pub/linux/kernel/people/tiwai/misc/hda-verb/hda-verb-0.3.tar.gz)
2. cd hda-verb-0.3
3. make
4. sudo cp hda-verb /usr/local/bin

and after that the command
```
sudo hda-verb /dev/snd/hwC0D0 0x1f SET_PIN_WIDGET_CONTROL 0x0
```
will mute the speaker,
and the command
```
hda-verb /dev/snd/hwC0D0 0x1f SET_PIN_WIDGET_CONTROL 0x40
```
will unmute it.
It's easy to write a simple bash-script which mutes the speaker if it is unmuted, and unmutes it if it is muted.
The script will look like this:


```
#/bin/bash
if [  $(/usr/local/bin/hda-verb /dev/snd/hwC0D0 0x1f GET_PIN_WIDGET_CONTROL 0x0 | grep 0x0 | wc -l)  = 1 ];then hda-verb /dev/snd/hwC0D0 0x1f SET_PIN_WIDGET_CONTROL 0x40;
echo 'unmuted';
else hda-verb /dev/snd/hwC0D0 0x1f SET_PIN_WIDGET_CONTROL 0x0;
fi
```

and you shuld run it with sudo.
Good news is that the whole problem should be fixed in kernel 2.6.33.

---

### Post by w43l on 2010-07-27
if you are on Lucid just go to synaptic and look for linux-backports-modules-alsa-lucid-generic and install it
no sources need to be added

---

### Post by juandadamo on 2010-09-06
> **w43l said:**
> if you are on Lucid just go to synaptic and look for linux-backports-modules-alsa-lucid-generic and install it
no sources need to be added

Works fine for me after restarting, thanks !

---

### Post by Rickie01 on 2011-03-14
I recently purchased wireless Sony headphones and they are amazing, I had never experienced such wonderful music with any other headphones till now. I carry it wherever I go and listen to music, it has seriously been worth for the money I have paid for it.

---

