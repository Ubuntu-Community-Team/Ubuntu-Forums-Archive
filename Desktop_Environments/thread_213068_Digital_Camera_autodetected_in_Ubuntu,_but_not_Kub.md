---
title: "Digital Camera autodetected in Ubuntu, but not Kubuntu"
date: 2006-07-10
forum: Desktop Environments
---

### Post by Kimm on 2006-07-10
I recently made the switch from Xubuntu (xfce) to Kubuntu (KDE).
When I was using XFCE (or Gnome for that mather) my Digital camera would just automount when i plugged it into the computer. In Kubuntu nothing happens at all...

I found a configuration area of KDE where I could set up a digital camera, but my camera was not listen and I see not use to set up the camera in KDE when it was auto-detected (as mass storage) by Gnome and XFCE.

am I doing something wrong?

I'm using a Fujifilm EX-20

---

### Post by Kimm on 2006-07-11
/bump

---

### Post by RAOF on 2006-07-11
I don't suppose this is what you want to hear, but I found Gnome's support for removable stuff far superior to KDE's.  This was also a camera (a Canon in this case).  Gnome just worked (tm), KDE would always error out with something suitably cryptic.

I suppose you could install and run gnome-volume-manager - that's what deals with hotplugging in Gnome, from what I can tell.

---

### Post by Kimm on 2006-07-11
I figured it out! (or well... I asked at the gentoo forums..)

Right click on the desktop, and select "Configure Desktop" -> "Behaviour" -> "Device Icons"

Then select anything that might solve the problem (I dont know what it was in my case :-P )

---

### Post by PhilB on 2006-07-11
Used to have similar problems myself.
Basically KDE sucks at this.
I ran various flavours of Suse and later Mandrake, with the default KDE desktop and was always frustrated in that although they would mount my card readers, displaying the contents was either incredibly slow (one time it estimated about 90 minutes to read 30 one meg images over firewire ! -then it crashed).
Tried posting this problem many times to various newsgroups and forums but never got any useful answers  and was resigned to keeping my windows machine going for photography. 
Eventually found out more by accident than anything else that Gnome had no trouble with my card readers and cameras, and have been running it for the last 18 months or so as my main desktop.
(Actually that was one of the reasons for switching to Ubuntu for me, that and no more RPM hell).
Phil

---

