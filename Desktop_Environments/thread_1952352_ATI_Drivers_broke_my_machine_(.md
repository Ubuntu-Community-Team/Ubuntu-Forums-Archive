---
title: "ATI Drivers broke my machine :("
date: 2012-04-04
forum: Desktop Environments
---

### Post by alex-turner on 2012-04-04
Hey guys,

I know my machine isn't screwed but I need some help. I was a Ubuntu user for a while then I had to return my machine to work and I reverted to OSX. I've since acquired a really nice Desktop with the full shebang and a really nice graphics card - Plus i've got a 5TB Fiber Channel array for all my goodies :)

Now I've installed Ubuntu and the open source drivers worked ok for a couple of days then they died, text started to jumble and windows would just screw up, like scribble everywhere. I've tried installing the proprietary drivers (again) following this guide:

[http://linux-software-news-tutorials.blogspot.com.au/2011/10/ubuntu-1110-oneiric-problems-with-ati.html](http://linux-software-news-tutorials.blogspot.com.au/2011/10/ubuntu-1110-oneiric-problems-with-ati.html)

Which described the errors I was having and now I can't boot, I'm just being greeted with a black screen. I've tried pressing esc at grub to boot into recovery mode with no luck. What can I do? HELPPPPPP

Alex

---

### Post by alex-turner on 2012-04-04
Video showing the bootup:
[http://www.youtube.com/watch?v=MjzMjvWFF0g&feature=plcp&context=C4b9ec88VDvjVQa1PpcFOdot8t2fz1FTMgMFhKdRZqSHlGjEF004k%3D](http://www.youtube.com/watch?v=MjzMjvWFF0g&feature=plcp&context=C4b9ec88VDvjVQa1PpcFOdot8t2fz1FTMgMFhKdRZqSHlGjEF004k%3D)

---

### Post by alex-turner on 2012-04-04
Update:

I've since discovered that after trying everything here:
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

with no luck, i've found that when booting into recovery mode and opening a root terminal - If I run shutdown -r now and press enter when greeted with the recovery menu (I.e "resume normal startup") Ubuntu boots and the graphics are flawless.

What is occurring during a normal boot that wouldn't be happening when I enter recovery mode? I can't wrap my head around this one - all I want is a working computer :(

---

### Post by Zvlwab on 2012-04-10
In /boot/grub/grub.cfg comment out
```
gfxmode $linux_gfx_mode
``` and reboot

If you have more than one kernel installed, remove it from the newest menuentry.

If this doesn't work run
```
sudo update-grub
```
to fix your grub again. I can't help you any further.

If it did help, it was a temporary fix and you should edit /etc/default/grub and add the following line
```
GRUB_GFXPAYLOAD=keep
```

and then run ```
sudo update-grub
```

this might ruin the resolution of your TTY though.

---

