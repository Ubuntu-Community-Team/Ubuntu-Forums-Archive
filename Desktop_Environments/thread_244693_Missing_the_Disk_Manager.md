---
title: "Missing the Disk Manager"
date: 2006-08-26
forum: Desktop Environments
---

### Post by ice_gamer on 2006-08-26
Hi there.  I have returned to using Ubuntu after a few months of no computer use, now using the latest version of Ubuntu: Dapper Drake.

It seems that I am missing the disk manager usually found under System > Administration > Disks.  This is an invaluable tool to me as I need to transfer some music to my Linux disk from my XP disk or I will die of boredom!

So, how can I reclaim this disk manager?  Is there a way I can apt-get it?

Thanks in advance.

PS.  The update manager is nowhere to be found as well.  I was able to run update-manager from the terminal, and it ran fine.  Any clue as to why it isnt in my start menu?

---

### Post by meng on 2006-08-26
First thing to do is check out your Alacarte Menu Editor. I bet either the options are there but unchecked, or else somewhere you weren't expecting (e.g. Applications > System Tools).

---

### Post by ice_gamer on 2006-08-26
Opened up Alacarte, and it is indeed selected, but it doesnt show up in the menu.

HOWEVER :D The alacarte menu properties for Disks gave me the terminal command:  gksu disks-admin ;  running this in the terminal gives me that same great disk managing goodness.  Thanks for the help there.

---

