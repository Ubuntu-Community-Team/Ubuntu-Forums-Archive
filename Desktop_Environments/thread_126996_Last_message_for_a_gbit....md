---
title: "Last message for a gbit..."
date: 2006-02-07
forum: Desktop Environments
---

### Post by jhbumby on 2006-02-07
I am having a baby tomorrow, scheduled c-section-First time Dad.  Nervous as a bastard.  Anyway, aside from a couple tweaks here and there, I cannot figure out my windows problem.  I had/have a dual boot.  Windows xp, swap, and ubuntu are my three allocations.  I am trying to rid myself of xp, and put windows 98 in the xp partion spot.  I tried using Gparted.  It said it couldn't do something because something was still mounted and would affect kernel.  So I tried umount, and that didn't work.  Somewhere in the middle, something happened.  Here's where I am at:

I start up my computer, and the swap comes on, offering the many ubuntu choices and windows xp.  If I click on XP, it says it isn't there.  So I try reading windows 98, my paid copy, and it won't read, meaning that xp is still there (from what I gather.)  So now I load ubuntu, and go into gparted.  It shows the third device as something, not the xp, but as it should be, a swap, and the ubuntu.  I still try to do stuff and I get the same error message about things still being mounted as I did before.  Quite the conundrum.  I was hoping to have things in place by tomorrow, but I understand these things take time.  I might be able to sneak back on to check up on things here and there, but I was hoping someone could help me solve this thing.  I appreciate everything you all do here.  I hope one day to help the cause in my own way.  Until next time-
JohnnyB
Ubuntu user for life

---

### Post by codejunkie on 2006-02-07
[QUOTE=jhbumby]I am having a baby tomorrow, scheduled c-section-First time Dad.  Nervous as a bastard.  Anyway, aside from a couple tweaks here and there, I cannot figure out my windows problem.  I had/have a dual boot.  Windows xp, swap, and ubuntu are my three allocations.  I am trying to rid myself of xp, and put windows 98 in the xp partion spot.  I tried using Gparted.  It said it couldn't do something because something was still mounted and would affect kernel.  So I tried umount, and that didn't work.  Somewhere in the middle, something happened.  Here's where I am at:

I start up my computer, and the swap comes on, offering the many ubuntu choices and windows xp.  If I click on XP, it says it isn't there.  So I try reading windows 98, my paid copy, and it won't read, meaning that xp is still there (from what I gather.)  So now I load ubuntu, and go into gparted.  It shows the third device as something, not the xp, but as it should be, a swap, and the ubuntu.  I still try to do stuff and I get the same error message about things still being mounted as I did before.  Quite the conundrum.  I was hoping to have things in place by tomorrow, but I understand these things take time.  I might be able to sneak back on to check up on things here and there, but I was hoping someone could help me solve this thing.  I appreciate everything you all do here.  I hope one day to help the cause in my own way.  Until next time-
JohnnyB
Ubuntu user for life[/QUOTE]
congrats on the new baby
gparted won't get rid of the windows XP ntfs partition it just can't do ntfs. when your in this situation you have a couple of options. 
1:**backup all important data** this ones not an option it's the life saver because when you are partitoning on your drive something can always go wrong no matter how or what program you use to do it.
2:**wipe the whole drive** and start clean install win98 first and leave some free space for ubuntu then install it. this ones probably not the one your looking for but i thought id add it.
3:**get your hands on partition magic** i find it the best on resizing formating windows partitons it works on linux partitions but it's not the best. use partition magic to wipe the ntfs partition create a new fat32 one in it's place and install windows 98.
4:**use cfdisk** open a terminal and do ```
sudo cfdisk /dev/hda
```it will list the  partitons and types just del the ntfs one make a new fat32 one and install 98 
when you say >  So I try reading windows 98, my paid copy, and it won't read, meaning that xp is still there (from what I gather.) 
if you mean when you try booting from the windows 98 cd to install it, the windows 98 cd is not bootable like XP you have to use a windows 98 boot floppy, boot from it choose start with cd support and when it boots into the command line insert the 98 disk cd to your cd-rom drive and type setup.exe hope one of these help and again congrats on the new baby.

---

### Post by plors on 2006-02-08
[QUOTE=codejunkie]
gparted won't get rid of the windows XP ntfs partition it just can't do ntfs. [/QUOTE]

oh please... you might consider checking on your data before throwing it public.
1) by using the ntfslib gparted is perfectly able to deal with ntfs.
2) when only trying to remove a partition the filesystem doesn't matter. 

About that warning he gets.. That's simply some piece of advice which will be removed in gparted's next release.

---

### Post by codejunkie on 2006-02-08
[QUOTE=plors]oh please... you might consider checking on your data before throwing it public.
1) by using the ntfslib gparted is perfectly able to deal with ntfs.
2) when only trying to remove a partition the filesystem doesn't matter. 

About that warning he gets.. That's simply some piece of advice which will be removed in gparted's next release.[/QUOTE]
gparted sucks at handling ntfs partitions at least that's my opinion and my experience with it.

---

### Post by plors on 2006-02-09
[QUOTE=codejunkie]gparted sucks at handling ntfs partitions at least that's my opinion and my experience with it.[/QUOTE]

Instead of acting childish you could consider filing bugs. That's the way OSS works you know. constant developing and bughunting. All parties are involved in creating better software. The developers are not here for your convience.

This is apart from the issue ntfs handling seems to work great for almost everyone else, especially in the latest release (0.2) which fixes some annoying issues with ntfs handling.

---

### Post by codejunkie on 2006-02-09
[QUOTE=plors]Instead of acting childish you could consider filing bugs. That's the way OSS works you know. constant developing and bughunting. All parties are involved in creating better software. The developers are not here for your convience.

This is apart from the issue ntfs handling seems to work great for almost everyone else, especially in the latest release (0.2) which fixes some annoying issues with ntfs handling.[/QUOTE]
this isn't going anywhere and im not going to let this become another flame war this forum has enough of them already have a good one plors.

---

