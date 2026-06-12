---
title: "Ubuntu boots with very strange theme"
date: 2011-01-07
forum: Desktop Environments
---

### Post by sarabisan on 2011-01-07
This problem just started today. I booted into Ubuntu (10.10) and for some reason it took about thirty seconds for the background and panels to show up. The graphics were okay, the drums started when they should have, just that everything else didn't load immediately. When the panels did appear, they had a very strange theme that looked a bit like Windows 95 with strange noises and an inability to copy and paste. I browsed to Theme, and changed it back to Ambiance. It was already selected on "Custom", before I changed back. The panels changed, but the following didn't:

1. The File Manager.

2. 2 of the mounted file systems.

3. Some of the right click menus. When I right click on the desktop, it's still box like.

By the way, when I changed back to the Ambiance theme, the Custom theme disappeared. I'm not used to configuring Gnome, so any help would be appreciated.

EDIT:
The custom theme changes to look a lot like ambiance when I open up Change Desktop Background. Even before I change anything.

[IMG]http://img267.imageshack.us/img267/8433/desktoptk.png[/IMG]

---

### Post by sarabisan on 2011-01-07
Wow, fixed it. Turns out it was my virtual machine. I deleted the virtual harddrive and everything's back to normal.

:)

---

### Post by spoon_ on 2011-01-20
I'm having the same problem!

It appeared after I installed some new components into my system:

Intel Core i7 2600K CPU
Asus P8P67 Pro Motherboard
8GB G.Skill RAM

Upgraded from a Core2 Duo.

System always boots with that hideous default theme. Ugh.

---

### Post by Kalimol on 2011-01-20
Is it related to [this]("http://ubuntuforums.org/showthread.php?t=1575703&highlight=nautilus+theme")?

I've had your problem (not the more extreme one described in the linked thread) since some particular software update. The things you're describing that still display in the chunky skinless style are all parts of Nautilus, the file manager, since it draws the desktop as well; run killall nautilus to fix it (in a given session.) It happens to me on my every third boot or so. I haven't found it troublesome enough to research....

---

### Post by bluewanders on 2011-01-20
Ive seen this as well... several times.  I dont even have any virtual machines installed by the way.  

Wanna know something really strange?  I actually kind of like theme that pops up every once in a while... but I cant find anything even remotely close among the themes available in "Appearance" nor just trying withing the customize options.  The icon set... the window border... even the sound scheme... they simply arent an option.

---

### Post by spoon_ on 2011-01-20
Hmm, it looks like people are having this problem with all kinds of hardware then. But for me it seems to have been triggered by the upgrade to Sandy Bridge. Even persists after a fresh install.

Edit: The fix proposed in the linked thread (adding gnome-settings-daemon to startup applications) doesn't solve the problem for me. I'm resorting to killing nautilus & gnome-panel after every reboot.

---

### Post by spoon_ on 2011-01-20
Ok, maybe it does have to do with the hardware upgrade. This bug is reported [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809/+index?comments=all"), and everyone who experiences it has an i7 with an SSD. As do I.

---

### Post by Kalimol on 2011-01-20
Atom with an SSD here.

---

### Post by KapteinPyn on 2011-03-26
AMD Phenom II X6 + SSD same problem

---

