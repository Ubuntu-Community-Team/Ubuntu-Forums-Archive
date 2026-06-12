---
title: "Installing CairoDock"
date: 2009-06-07
forum: General Help
---

### Post by Rownrie on 2009-06-07
I know there are several (if not many) tutorials online on how to install CairoDock, but I am having a horrible time installing it. 

I'm brand new to Ubuntu 8.10 and I have absolutely NO Idea of what ANY of the terminology in this [https://help.ubuntu.com/community/CairoDock]("https://help.ubuntu.com/community/CairoDock") tutorial means. 

I tried installing it through Synaptic but, yeah, I honestly don't know what I'm doing.

A quick how-to would be great!

Also, I'm switching from OS X and I can't seem to function w/o spotlight, is there something similar to that on Ubuntu 8.10?

---

### Post by Tipped OuT on 2009-06-07
Make sure to completely uninstall Cairo Dock using Synaptic Manager.

Then download one of the two links below (depending if you use 32 bit or 64 bit). Double click and install "**cairo-dock_v2.0.3**". Once it has installed succesfully, double click and install "**cairo-dock-[COLOR="Red"]plug-ins[/COLOR]_v2.0.3**".

Go to Applications< System Tools< Cairo Dock No-OpenGL (You can try the OpenGL version, but it probably won't work depending on your graphics card)

32 Bit Versions:

------------------------------------------------------------------------------------------------------------------

[http://prdownload.berlios.de/cairo-dock/cairo-dock-plug-ins_v2.0.3_i686.deb](http://prdownload.berlios.de/cairo-dock/cairo-dock-plug-ins_v2.0.3_i686.deb)

[http://prdownload.berlios.de/cairo-dock/cairo-dock_v2.0.3_i686.deb](http://prdownload.berlios.de/cairo-dock/cairo-dock_v2.0.3_i686.deb)

------------------------------------------------------------------------------------------------------------------
64 Bit Versions:

[http://prdownload.berlios.de/cairo-dock/cairo-dock-plug-ins_v2.0.3_x86_64.deb](http://prdownload.berlios.de/cairo-dock/cairo-dock-plug-ins_v2.0.3_x86_64.deb)

[http://prdownload.berlios.de/cairo-dock/cairo-dock_v2.0.3_x86_64.deb](http://prdownload.berlios.de/cairo-dock/cairo-dock_v2.0.3_x86_64.deb)

---

### Post by DeusExM1 on 2009-06-07
in that case you might want to consider installing gnome-do and gnome docky instead of cairo dock. [http://do.davebsd.com/release.shtml](http://do.davebsd.com/release.shtml) Cairo dock has a lot of features, but it is quite buggy. I tried using it a few days, and it hung up my system requiring a hard reboot.

Gnome-do is similar to spotlight, but with a few extra features. You can run programs by just typing in the name. You should check it out. Gnome-Docky is the dock for gnome do. Hope this helps.

Note: *I do not use any dock at all.

---

### Post by newb85 on 2009-07-04
Thanks, Tipped OuT - your directions are very helpful.  The links, however, do not lead to the newest release anymore.  The newest release (or any other release that suits your fancy) can be found at:

[http://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=16450](http://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=16450)

As Tipped OuT said, you need to install both the dock and the plug-ins.

---

### Post by misswham on 2009-07-12
i have downloaded the cairo dock and cairo dock plugins to my desktop now I dont have a clue what to do once i click on the folders.  I have never downloaded a program without tying commands in the terminal.  i have gone to every older post on what to type in the terminal and still nothing.  i am running hardy can someone tell me what to do with the folders on my desktop?

---

### Post by newb85 on 2009-10-14
Double-click on the cairo-dock (not plug-ins) file, and installing should be straightforward from there.  Once that is done, you can do the same with the plug-ins file.

---

### Post by newb85 on 2009-12-14
Addendum: I recommend that, if possible, you follow the directions at help.ubuntu.com/community/CairoDock (From a Repository) instead of the directions given here by Tipped OuT.  I say this because when Cairo-Dock has been installed through a package manager (like Synaptic), it will be automatically updated in the future.    Since my last post, the Cairo Dock team has added several cool features and fixed a couple bugs I was running into.

Let me try to explain a little:

A repository (or repo) is an online location that a package manager looks for software packages.  By default, the Ubuntu repository should have been set up on your computer.  Probably a majority of Ubuntu users add the Medibuntu repo, which adds a lot of capabilities.  Synaptic will show all available packages in all the repos you have set up.  

The file /etc/apt/sources.list is a text file that Synaptic uses to keep track of your repos.  The lines beginning with # do not affect Synaptic; they are only comments to help human users know what's going on.  when you add the line
> deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) karmic cairo-dock  # For Ubuntu 9.10I recommend that you also add a line or two of comments to remind you in the future what this repo is.

The line[FONT=monospace]
[/FONT]> wget -q [http://repository.cairo-dock.org/cairo-dock.gpg](http://repository.cairo-dock.org/cairo-dock.gpg) -O- | sudo apt-key add -is a security measure - it helps your computer know that when you access the CD repo, you're getting what you think you're getting, and not some bogus software that's going to wreck havoc on your computer.  It should be entered directly into the terminal, not into /etc/apt/sources.list

The line
> sudo apt-get updatesimply updates the packages you already have installed.  This is usually a good idea before adding more packages.  Running Update Manager would accomplish the same thing.

The line
> sudo apt-get install cairo-dock cairo-dock-plug-insinstalls the two packages.  You could also do this by running Synaptic and installing the two packages from there.

---

