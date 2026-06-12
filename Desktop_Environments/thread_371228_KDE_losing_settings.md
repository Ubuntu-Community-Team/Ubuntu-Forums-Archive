---
title: "KDE losing settings"
date: 2007-02-26
forum: Desktop Environments
---

### Post by jaustill on 2007-02-26
Hey yall, I've done a fresh install of ubuntu on my desktop, installed kubuntu-desktop, and logged in.  My problem is that if I add an applet to the taskbar, say the audio mixer controls, when i log out and back in it's gone, it's not saving the setting for the fact that I added it.  Is this something Kubuntu is known for?  How do I fix it, cause it's REALLY annoying!!  Thanks yall.

Joshua

---

### Post by aysiu on 2007-02-26
Can you try creating a new user called *test* and seeing if the new user has the same problem when logged into KDE?

You can always delete the *test* user after you finish this little experiment.

---

### Post by ComplexNumber on 2007-02-26
> **aysiu said:**
> Can you try creating a new user called *test* and seeing if the new user has the same problem when logged into KDE?

You can always delete the *test* user after you finish this little experiment.
yeah, i would recommend that also. a dummy account can be useful for testing things out.


i'm wondering if its the old problem of files/folders in the users directory suddenly becoming owned by root (just like what happens with the main menu sometimes).


[B]jaustill
[/B]how exactly are you adding them to the taskbar? for example, are you adding them via the menu (eg going to the item in the main menu, right clicking, then adding to the panel)?
unfortunately, i haven't got kde installed, so i can only go by memory. when you add an item to the panel, it should store it in the settings in /home/<your-username>/.kde/share/config(i think). i can't remember the exact file, though. look for one that has panel in the name BEFORE your logout.

---

### Post by jaustill on 2007-02-27
Hey, the test user was a GREAT idea :)  When creating the new test user I got an out of disk space error, which was my problem.  I installed Ubuntu for the first time a few days ago over my existing gentoo install.  I had a /boot on sda1, swap on sda2, unused space on /sda3, and / on sda4.  So when I installed Ubuntu I told it to install to sda3 and use the unused space.  What I DIDN'T realize is that it grabbed my /boot /sda1 partition and mounted it as /home, and it was only 32 megabytes.  So once I installed google earth it wasn't very long before the caching had that partition filled up.

My solution was to log out of x completely to a prompt, and kill the gdm session, then

sudo mv /home/jlaustill /root/
sudo umount /home
sudo mv /root/jlaustill /home/
sudo gedit fstab (remove the mount point)

I also thought about moving the /boot to my sda1 like I had in gentoo, but since unbuntu already has it set up on the same partition I think I'll just leave it for now, everything seems to be working fine.  So now I know that kde doesn't have warning messages for disk space issues, I'm thinking about filing a bugzilla on that one!!! Thanks guys, this ubuntu forum is turning out to be just as helpful as the gentoo forums!!!

---

### Post by jaustill on 2007-02-27
> **ComplexNumber said:**
> yeah, i would recommend that also. a dummy account can be useful for testing things out.


i'm wondering if its the old problem of files/folders in the users directory suddenly becoming owned by root (just like what happens with the main menu sometimes).


[B]jaustill
[/B]how exactly are you adding them to the taskbar? for example, are you adding them via the menu (eg going to the item in the main menu, right clicking, then adding to the panel)?
unfortunately, i haven't got kde installed, so i can only go by memory. when you add an item to the panel, it should store it in the settings in /home/<your-username>/.kde/share/config(i think). i can't remember the exact file, though. look for one that has panel in the name BEFORE your logout.

In Kde you can drag and drop pretty much everything, I was adding for instance the firefox icon by clicking on the kmenu, going to internet, then clicking and dragging firefox to the taskbar.  I also add a sound mixer by right clicking on the taskbar and hitting add applet, then just double clicking on the sound mixer one.  Unlike gnome however, you can add things pretty much any way you want in kde, it's the paradigm of ease of use vs letting the user do anything and everything they want.  I'm not on any particuliar side of the gnome vs kde debate, I think they are both great de's, but for me personally, I can't use gnome, I would end up punching my monitor lol.  On the other hand, whenever I set up one of my friends/family with linux, I almost always set them up with gnome, because it's way simplified and doesn't present a bunch of confusing options.

---

### Post by ComplexNumber on 2007-02-27
> Unlike gnome howeveri think you'll find that gnome has better support for drag and drop. all of what you say you can do do in kde i can do in gnome. 



well, at least you've solved your particular problem anyway.

---

### Post by jaustill on 2007-02-27
> **ComplexNumber said:**
> i think you'll find that gnome has better support for drag and drop. all of what you say you can do do in kde i can do in gnome. 



well, at least you've solved your particular problem anyway.

That could very well be, I honestly don't use Gnome enough to have a clue :)  I've been thinking about switching back to xfce now that it supports beryl :)  I'm at work right now, and not having my cube, expose, and sticky windows is be drivin me nuts haha.  Thanks again for your help.

Joshua

---

### Post by ComplexNumber on 2007-02-27
well, one could compare the advantages and disadvantages of both. but at the end of the day, its what works best for *you* that counts.

---

### Post by chavo on 2007-02-27
> **ComplexNumber said:**
> i think you'll find that gnome has better support for drag and drop. all of what you say you can do do in kde i can do in gnome. 



well, at least you've solved your particular problem anyway.

Oh so you can switch desktops by scroll wheel on the desktop in gnome now? Awesome.
You can have your window manager remember exactly the size and position to launch a window with a couple of mouse clicks now? Amazing.

Gnome 3.0 must have come out while I was napping, time to catch up.

---

### Post by ComplexNumber on 2007-02-27
> **chavo said:**
> Oh so you can switch desktops by scroll wheel on the desktop in gnome now? Awesome.
You can have your window manager remember exactly the size and position to launch a window with a couple of mouse clicks now? Amazing.

Gnome 3.0 must have come out while I was napping, time to catch up.
you still are napping judging by your response. thats the first  anyone else has heard that switching desktops etc has got anything to do with drag and drop. amazing.

---

