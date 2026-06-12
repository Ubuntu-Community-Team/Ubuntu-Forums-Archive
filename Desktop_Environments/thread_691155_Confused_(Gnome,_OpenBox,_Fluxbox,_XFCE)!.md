---
title: "Confused (Gnome, OpenBox, Fluxbox, XFCE)!"
date: 2008-02-08
forum: Desktop Environments
---

### Post by TenPlus1 on 2008-02-08
After using Ubuntu for over a year I thought it was time to try and change the desktop environment and play with the other window managers out there, so I did...  but...  After installing each of the 4 listed and setting them up for my own specific needs, I found out that they actually used more memory than my basic Gnome setup.

OpenBox = 152mb
Fluxbox = 149mb
XFCE = 156mb
Gnome = 115mb

???  I really cannot figure out why this is, but hey, I'm sticking to Gnome if this is the case...  My only problem seems to be that PcManFM no longer runs in Gnome after the last linux-image update, but works fine in all of the others...  Any ideas folks ?

---

### Post by kerry_s on 2008-02-08
hmm?
maybe you added to much stuff to get what you have in gnome?
for example:
openbox & fluxbox you would probably grab a background setter, maybe something to do icons, maybe some sort of panel, etc...
ditto for xfce4

if gnome does it for ya stick with gnome. i use jwm on a debian custom install, 24mb on boot, grows as i browse in firefox(cacheing)

---

### Post by TenPlus1 on 2008-02-08
I pretty much leave each window manager as a basic install, apart from the needed screensaver/volume-manager...  Does your setup auto-mount volumes ? or do you use a separate prog ?

---

### Post by ejket on 2008-02-08
> **TenPlus1 said:**
> OpenBox = 152mb
Fluxbox = 149mb
XFCE = 156mb
Gnome = 115mb

???  I really cannot figure out why this is, but hey, I'm sticking to Gnome if this is the case...  My only problem seems to be that PcManFM no longer runs in Gnome after the last linux-image update, but works fine in all of the others...  Any ideas folks ?

Where are you getting your numbers from?

Top gives me:

```

Gnome   = 603516k used
Openbox = 528856k used
```

I also find it odd that you'd use a trivial difference in memory use (assuming your numbers are good to begin with) to determine what you use.

Openbox, Fluxbox, and Xfce4 are all leaner and faster than Gnome, and they're all nice to use IMO.  I like Gnome, too.  Now, I completely understand the "I'm bored and want to try something else" feeling.  Just go with that and quit making excuses :)

---

### Post by kerry_s on 2008-02-08
> **TenPlus1 said:**
> I pretty much leave each window manager as a basic install, apart from the needed screensaver/volume-manager...  Does your setup auto-mount volumes ? or do you use a separate prog ?

no, no auto mounting here,i use pmount. when i want auto mounting i use ivman for that. also no screen saver here, i turn off the screen or it turns off on it's own in 5min. sound control is done by amixer, part of alsa-utils, i use alsa for sound.

examples:
pmount /dev/sda1   <-mounts my drive
pumount /dev/sda1  <-unmounts
(just setup rox, to do the mounting/unmounting, so now i just click on it)
requires fstab entry and a folder in media and change the rox mount options to pmount/pumount
/dev/sda1       /media/sda1     auto    user,noauto     0       0



amixer sset PCM 5- unmute  <-lowers volume by 5
amixer sset PCM 5+ unmute  <-raises volume by 5

sleep 5;xset dpms force off  <-gives me 5sec's to take my hand of the mouse then turns the screen off

sound and display control is part of my wm settings, mount i usually just use my launcher(gmrun) much faster than opening a terminal.

---

### Post by TenPlus1 on 2008-02-09
I use the Gnome-System-Monitor and the Resources tab and User Memory to determine how much memory is being used by a particular Wm...

---

### Post by Nythain on 2008-02-09
well... loading a useless gnome app and im assuming teh gnome libraries to run it, inside of another wm/de could probably be why they are reporting more ram usage... thats like running gnome and fluxbox together, of course its going to use more ram

---

### Post by macogw on 2008-02-09
> **Nythain said:**
> well... loading a useless gnome app and im assuming teh gnome libraries to run it, inside of another wm/de could probably be why they are reporting more ram usage... thats like running gnome and fluxbox together, of course its going to use more ram
+1

I don't have anything GNOME installed on my Fluxbox system.  There are GTK libraries for Pidgin and Gimp, but everything else I use is DE-independent.  I use mrxvt for my terminal, irssi for irc, and Sunbird for my calendar.

According to the "resident memory" column in top, Fluxbox is using 4696K of memory.

---

