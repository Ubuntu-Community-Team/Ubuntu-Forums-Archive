---
title: "nw8240 + Feisty + Compiz FINALLY"
date: 2007-04-24
forum: Desktop Effects &amp; Customization
---

### Post by gapplewagen on 2007-04-24
I was FINALLY able to get my HP nw8240 with ATI FireGL V5000 (X700) to work with Compiz today.  It was a pretty serious process but only because I had so may old configs and other bad things laying around.  The trick for me was to completely remove xorg-driver-fglrx.  I had it installed from a while ago when I was trying to get Beryl to run with Xgl instead of AIGLX (was getting the dreaded "GLX_EXT_texture_from_pixmap is missing" error).  After some searching I ran into this:

[http://blog.micampe.it/articles/2006/02/18/ubuntu-fglrx-xgl-compiz-and-missing-glx_ext_texture_from_pixmap]("http://blog.micampe.it/articles/2006/02/18/ubuntu-fglrx-xgl-compiz-and-missing-glx_ext_texture_from_pixmap")

Which states:

The problem is that when you install the fglrx driver it overwrites /usr/lib/libGL.so.1.2 with its own version wich lacks this feature.

Removed and purged fglrx, copied the config file from my desktop (ATI Radeon 9800 pro), restarted X, clicked the magical "Enable desktop effects", and instead of crashing or logging me straight out, I got wonderful wobbly windows.

---

### Post by Taz1of4 on 2007-06-28
Hi Gapplewagen!

I really looked forward to a message like yours! Before I give it a try myself I wonder if you ran in any of the problems with the monitor-detection (like blank screen and no possibility to change any config-files)? I did with the feisty-live-cd - I was not even able to get a text-based interface running, because my screen simply stayed blank :-( A lot of other people having a nw8240 ran in the same problems as I did.

You were using a different xorg.conf from a different pc, as it seems? Did you edit anything mentionable before, or was it a default one, concerning the monitor,screen and device options?

THX in advance!

Taz!

---

### Post by qopit on 2007-07-14
I've also had a hellish time trying to get my nw8240 to work with Ubuntu.  I eventually did by using the Ubuntu 7.04 alternate install cd, which will get you the text window (although I think I had to interrupt GRUB at the start  latter and go recovery mode... I forget now).

Once I got a command line the first thing I did was use wget to pull down the Envy script, then installed all the needed drivers, and then I rejoiced to get my desktop.

Since then, I think I've been able to get it running simply with: "sudo aptitude install fglrx-driver" then a reboot to command line and then "sudo aticonfig --initial" and then reboot.

I think that is it... sorry for the impreciseness of that... it is from memory, and I 've currently got my system a bit screwed up so I can't verify much.

My latest problems have been the hours and hours I've spent trying to get Beryl running.  I'm not having much luck and have been through several attempts using both the closed fglrx drivers and the open ones, using XGL and not... the latter just gives me a blank screen with an X cursor...

I expect my configs are all totally hosed, even though I keep uninstalling everything and reverting to backups.

The original post here is interesting, although I don't think it is quite enough info.  We'll see!  Interesting that it was done without XGL.

---

