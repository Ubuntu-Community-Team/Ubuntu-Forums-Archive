---
title: "KDE on Ubuntu 20.04 vanilla"
date: 2020-09-22
forum: Desktop Environments
---

### Post by agvantibo on 2020-09-22
So I installed a fresh version of Ubuntu 20.04 on an external HDD, and I was pretty much amazed by how smoothly it ran, but then an idea popped inside my mind: what if I will install KDE on a vanilla Ubuntu with GNOME and just alternate between these DEs. So I installed the plasma-desktop with apt, and relogged, choosing KDE as a DE in Mutter. The first thing I have noticed, is that the DE loads veeeery slooooowly - it took about 2 minutes. I have done some customizing and installing there, and I was pretty much happy with how it ran. When I switched back to GNOME, it was a complete disaster :D. The fonts, theme, wallpaper, mouse pointer, icons, my elaborate GNOME app folder system - all pretty much destroyed. After some rapid usage of GNOME-tweaks, Dconf and settings I managed to get the original Ubuntu look back. So, how do I run two DEs without one dominating another and freaking me out? #-o

---

### Post by CelticWarrior on 2020-09-22
Welcome.

Maybe try installing 'kubuntu-desktop' instead?

---

### Post by crip720 on 2020-09-22
If going to play with adding/changing DEs, should be done on VM or a practice dual boot first.  Some DEs play nice, some don't, do it on system you don't care about wiping.  "but then an idea popped inside my mind:"  what a scary thought.

---

### Post by guiverc on 2020-09-22
I would also install `kubuntu-desktop` on-top of the standard Ubuntu install. 

I've done it for years, as my ISP has always allowed Ubuntu ISOs to be downloaded quota-free, so I've used that as my base, then installed the desktop I really wanted to use (I loved GNOME when it was GNOME2, lost interest with Unity or GNOME3; but I never removed it).

Loading the second desktop in my experience won't have problems, problems start appearing at the fourth desktop.  

However be aware when you change GTK settings in KDE, it'll impact GNOME. And changes made to Qt5 based settings in GNOME will impact KDE. You gave little details as to what you configured, but be aware of what or where in the stack (mutter is a GTK program so changes made to make it nicer in KDE could of course be expected to impact GNOME as it's changing GNOME's stack)

---

### Post by agvantibo on 2020-09-23
> **crip720 said:**
> If going to play with adding/changing DEs, should be done on VM or a practice dual boot first.  Some DEs play nice, some don't, do it on system you don't care about wiping. 
Yeah, I have thought about it, but the CPU I will be using probably doesn't support virtualisation, and a VM would probably run slow as hell.
Thanks for help everyone!

---

### Post by agvantibo on 2020-09-23
> **guiverc said:**
> You gave little details as to what you configured, but be aware of what or where in the stack (mutter is a GTK program so changes made to make it nicer in KDE could of course be expected to impact GNOME as it's changing GNOME's stack) Nope, I just installed some packages and tweaked the KDE theme settings, as for Mutter I never changed any settings, just chosen KDE as DE to start on login temporarily (while logging in there is a gear button, when clicked it displays available DEs to start)
So, installing raw plasma-desktop is no good, and kubuntu-desktop should be installed instead. It is also obvious that the plasma-desktop package should be removed with sudo apt remove plasma-desktop --purge. Am I right? Please correct me if I am wrong...

---

