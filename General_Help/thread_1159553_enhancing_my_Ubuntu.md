---
title: "enhancing my Ubuntu"
date: 2009-05-14
forum: General Help
---

### Post by gamelord12 on 2009-05-14
I have two complaints with how my Ubuntu machine operates.  I miss instant search like I have it in Vista.  Deskbar would be great, but it freezes constantly after a few queries.  It will just hang without displaying any results, though the normal Beagle search appears to be fine.  Secondly, it's happened to both myself and my roommate: our systems froze in the middle of an update, something got corrupted, and our machines couldn't boot.  Is there any program that will automate a system restore-esque function so that we can boot to a last-known working configuration, preferably right from GRUB?  Assuming two complete back-ups are made of every file crucial to the OS, that's only an extra 10 GB of hard drive space, which I can spare.  I hate having to do a complete re-install due to a problem during a routine update.

---

### Post by deathsshadow77 on 2009-05-14
try gnome-do for searches

---

### Post by UbuntuNerd on 2009-05-14
you can add instant "search" to your top or bottom panel just right click on an empty space of your panel and press "add to panel" when the menu open type "search" in the bar you should get the instant search

---

### Post by gamelord12 on 2009-05-17
In addition to bumping my previous question, where do I find settings for the indicator applet?  It's just a bit too much on the obnoxious side, especially when I'm full-screening StarCraft or a Hulu video.

---

### Post by cariboo on 2009-05-17
With the new notification system, you only have to choices, the default or nothing. It was decided by the devs to disable the notification preferences menu just before the Jaunty release.

To get rid of the notifications just remove notify-osd, otherwise you'l have to put up with the default bevaiour until Karmic is released.

---

### Post by gamelord12 on 2009-05-18
Is there a preferences menu package I can download from somewhere?  I mean, isn't that a part of the X.org project and not specifically Ubuntu?  It should exist somewhere, right?

---

### Post by gamelord12 on 2009-05-21
When I go into synaptic to remove it, it says that gnome-power-manager, ubuntu-desktop, and update-notifier must also be removed.  Looking at the descriptions, they seem important.  Is this going to screw up anything?

---

### Post by R Clemons on 2009-05-21
yes it will, as far as the updates go if it was a kernel update you should be able to choose the previous kernel in GRUB.  Also make sure you don't have proposed packages checked in software sources as this can lead to frequent and buggy updates.

---

### Post by gamelord12 on 2009-05-21
Just to clarify, I was talking about removing notify-osd.  Booting from an old kernel doesn't help me if one of the other crucial packages, like GNOME itself, gets corrupted during an update.

---

