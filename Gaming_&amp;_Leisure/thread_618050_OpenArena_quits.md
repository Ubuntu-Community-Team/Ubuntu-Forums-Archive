---
title: "OpenArena quits"
date: 2007-11-20
forum: Gaming &amp; Leisure
---

### Post by BinaryDemon on 2007-11-20
Hi guys.

I rebuild alot of older systems and usually end up installing the latest Ubuntu version to sell them cheaply or give them to family.  Usually as quick benchmark / system test, I install OpenArena and play online for a few minutes. I am not a linux power user, but most times if I have a problem I can do a quick search here, or google and find a solution. Well here's my problem:

On my latest build OpenArena installs normally, but when I attempt to run OpenArena it runs, flashes black, and instantly returns to the desktop.

The system is a Duron 1200, 768mb ram, Voodoo3000 agp card.
It's running Ubuntu 7.10 with the latest updates.Ubuntu is using the tdfx driver. I have heard OpenArena generates a logfile, but I have been unable to find it. Initially, I thought maybe a file corrupted so I reinstalled Ubuntu but the same issue returned. I have tried various desktop resolutions with the same result. I tried removing the --quiet from the launcher command line, but I still cant see any error. I don't see any other issues with system stability, I dont think the hardware is bad. Advice?

Thanks

---

### Post by BinaryDemon on 2007-11-20
Actaully, it was a hardware issue. Apparently the Voodoo3 was fine displaying 2D but broken when attempting 3d. I switched to a tnt2 agp and OpenArena runs fine.

So consider this issue resolved, but if someone wants to point out the location of the logfile, id still like to see the error OpenArena was generating.

---

### Post by Dreamlocked on 2007-11-20
Hello.

I don't know exactly where that specific file is, but maybe I can help you find it.
Open a terminal window and type :

```

cd /
sudo find -name '*log*' > /home/<username>/mylogsearch.txt

```

Where <username> is your username...

Notice the asterisk (*)  before and after the *log*. They are wildcards that will enable you to find all files that contain *log* (begining, middle or end of file). 
The search will be saved on your desktop in the *mylogsearch.txt* file.
If you're not lucky with the *log* word, I guess you can try replacing with arena, error, or whatever you deem likely to help you.

---

