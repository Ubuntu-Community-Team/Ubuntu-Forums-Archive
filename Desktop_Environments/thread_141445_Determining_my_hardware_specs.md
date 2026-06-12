---
title: "Determining my hardware specs"
date: 2006-03-08
forum: Desktop Environments
---

### Post by groggyboy on 2006-03-08
So I've been toying around with Ubuntu recently.  I was never more than mildly proficient with windows, and one day I just decided to switch for the sheer fun of it.  Wow!  Ubuntu is serious fun.  I've hardly touched my windows partition since the big install.

Anyways, for a handful of reasons (suspend2, improved WPA wireless security), I've been trying to recompile my kernel.  Twice, now, I've tried but I've always had problems at boot.

I'm ready for lucky try number three, but I was wondering if there is any way to figure out my hardware specifications, so I know what modules I can include and which ones I don't need.  Example: Pentium M processor, IDE drive, Intel 2200 bg wireless, etc.  There are so many options, I feel a little swamped.  Sorry if this is a repost of someone else, or such.  Just wanted to know.  Any other advice for an ubuntu newbie about to recompile his kernel is also appreciated.  I know there are a few HowTos out there, but they say nothing about finding out hardware specs.

Sorry for the long (and maybe redundant) post. #-o  Cheers!

---

### Post by aggiechemist on 2006-03-08
I've got two suggestions:

1. I assume your using Gnome. I don't have Gnome handy at the moment (I'm on a WMaker box today), but I know there is a menu about system hardware. It is under the preferences or administration folder on the menus I think. It gives really detailed information about your hardware. Things like brands, sizes, speeds, its all there.

2. Open the box. Most of the stuff should be labeled in some way. Don't go too nuts, especially if you have no idea what you are doing, but there is probably quite a bit of info available that way.

I know nothing about compiling kernels though. Best of luck, its the sort of thing I have always wanted to try.

---

### Post by groggyboy on 2006-03-08
thanks.  hopefully this will help.  it's System --> Administration --> Device Manager, in case anyone cares.  small problem, tho, as a bunch of the stuff is listed as "unknown".  i wish i knew more about using "dmesg" or "grep" commands in the terminal.  i guess i'll find out if device manager is enuf when i actually sit down tonight and compile it.

---

### Post by steve.horsley on 2006-03-08
Try **sudo lshw > hardware.txt**. It'll blow you away.

---

### Post by groggyboy on 2006-03-08
Nice.  That answers a number of questions for me.  Should help with kernel rebuilding.:D

---

