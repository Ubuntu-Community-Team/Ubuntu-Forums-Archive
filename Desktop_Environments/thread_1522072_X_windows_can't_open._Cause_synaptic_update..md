---
title: "X windows can't open. Cause synaptic update."
date: 2010-07-01
forum: Desktop Environments
---

### Post by likeitfast on 2010-07-01
[FONT="Arial"]I apologize if I am posting in the wrong place or not following the right procedure This is my first post (actualy 2nd I forgot of the one of me trying linux the first time). If I am please inform me.

Ok with that out of the way. I am seeking any enlightenment that can be given on my problem I appreciate any guesses or better.

I am trying to run Ubuntu 10.04 amd64. And Ubuntu typically is stable for me dispute all windows installs get BSOD. Graphic card is nvidia geforce 8400. more details will be included in system section

Index:
[INDENT]Cause[/INDENT]
[INDENT]Symptoms[/INDENT]
[INDENT]System[/INDENT]


Cause:  3-5 days ago I updated my computer that had not been updated for 2-4 days using synaptic. I had no error warnings so I decided to reboot (I might have used alt ctrl delete to restart). After restart I received the standard prompt that occurs when the graphics driver is having problems. The screen with the options: run low graphics mode, reconfig graphics, ..., restartx.
I tried low graphics. Eventually I boot to netroot. In net root I tried messing with nvidia driver packages not modalias. and messing with xorg.conf using nvidia-xconfig. Also attempted to change drivers using update-alternatives --config gl_conf those are where I messed and possibly exacerbated the problem (but probably not by much)(but I have had nvidia-current driver problems before due to updates that make me decide to reinstall).

Symptoms:  The command startx returns no errors that I can tell from the log but startx stops. gdm (in netroot) returns cant find user list (cant readily recall the exact name but sounds like the password and names of users). Then some graphics errors. Most gtk and X programs/commands return the error x window cant open. and gtkbox (the gtk test program I will correct later) returned an error at ".run priority 0". Not when the same command was called with no priority explicity stated.

System: 
   Hardware: user built. Amd Athlon II x3 435. ECS IC780M-A2 (V1.0A) EliteGroup motherboard. 2Gb ram. 500gb linux HDD. 40GB xp 32bit. grub2 boot.
   Software: ubuntu 10.04 amd64. Sources partners and some APPs.


I suspect the initial cause (before I monkeyed around) was that one of the lib packages that was updated in that session made my computer unstable. Also to note I removed a lot of lib packages in netroot thru the autoremove command. If not one of the lib packaged one of the others that were updated (I wish I could find out what was changed so I could at least undo it manually (in theory).
If you want any additional info please ask.[/FONT]
I apologize for the formatting it seems a little dense.

---

### Post by likeitfast on 2010-07-03
Should I just do another reinstall?

---

### Post by likeitfast on 2010-07-04
Did a reinstall everything works fine but I am hesitant to enable the nvidia restricted drivers because I think those cause incapability problems that my computer can't recover from. It might be my inexperience using synaptic and using synaptic default settings and enabling partner and universe sources causing the problem.

Any ways marking this as fixed.

---

