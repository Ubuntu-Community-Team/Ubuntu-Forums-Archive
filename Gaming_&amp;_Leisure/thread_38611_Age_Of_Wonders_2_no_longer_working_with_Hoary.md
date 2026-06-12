---
title: "Age Of Wonders 2 no longer working with Hoary"
date: 2005-06-01
forum: Gaming &amp; Leisure
---

### Post by Poldi on 2005-06-01
hi, all.

I used AoW2 and the installer from [http://goldenfiles.sourceforge.net/index.php?page=aow2-installer](http://goldenfiles.sourceforge.net/index.php?page=aow2-installer) in Ubuntu Linux Warty 4.10 with great success. everything worked including sound, high resolution etc.

now upgrading to Ubuntu 5.10 (Hoary) breaks AOW2.

whats new?

2.6.9 -> 2.6.10 kernel
ESD instead of ALSA is the preferred soundsystem
XFree86 -> X.org

I have tried this with various changed soundsystem configurations as well as without sound. does not work.

reproduced broken AOW2 on 
- upgraded system as well as fresh install of Hoary 5.10
- Thinkpad T20 / T22 (S3 gc)
- Thinkpad R40 (ATI Radeon 7500 mobility - no proprietary driver available)
- inside a VMWare guest VM.

- Cedega 4.1.1
- Cedega 4.2.1, 4.2.2, 4.3

the results are the same. 

AOW2:WT starts, plays intro according to config, the menu is useble, sound and music play (if so configured) but on every 'next' screen - scenario selection, load game ... the game halts or exits.

I have not been able to start a game once.

I suspect the change from XFree to X.org might be the culprit. any suggestions? has anybody experienced similar behavior in games after upgrading to Hoary?


thanks and regards,
Carsten

---

### Post by Poldi on 2005-06-01
ok, now I was really stupid. I just wanted tto try wheather x11.org is the culprit and this message:

[http://ubuntuforums.org/showthread.php?t=25040&highlight=hoary+xfree86](http://ubuntuforums.org/showthread.php?t=25040&highlight=hoary+xfree86)

sounded as if trying xfree86 instead was really easy.

well, I did apt-get install xserver-xfree86 and now I have not X at all. gdm does not start and I have no /etc/X11/XF86Config-4 file at all. why does this not work? did nobody ever fall back to XFree86 before? I found no advice in this forum... what did I do wrong???

help me, please.

kind regards,
Carsten

---

