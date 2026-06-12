---
title: "login resolution"
date: 2006-01-17
forum: General Help
---

### Post by tbobo05 on 2006-01-17
how do i change the resolution of the login screen? as of right now, i see double vision when i log in until my desktop comes up.

---

### Post by o_fortuna on 2006-01-17
[QUOTE=tbobo05]how do i change the resolution of the login screen? as of right now, i see double vision when i log in until my desktop comes up.[/QUOTE]
I think (I may be wrong) that you can change the system value by going through System-->Preferences-->Screen Resolution, selecting the proper resolution and refresh rate, and making sure "make default for this computer only" is checked. Post back if this doesn't work.

---

### Post by tbobo05 on 2006-01-17
yea, it doesnt work....thats what i tired when i first installed with Hoary, i was hoping with breezy that there would be some apparent option to change it but there is not (at least that ive seen).  I've even seen posts like this one before, but can't seem to find them.  When I hook my box up on my girlfriend's setup (she has a dell 15'' LCD), the resolution is fine, but with my Samsung 19'' CRT (I think it is a sync something, not sure) i get the double vision on first login....does anyone know any other way of setting this?  which config file should i look in to manually set resolutions?

---

### Post by ferebee on 2006-01-17
I had a similar problem with my Samsung Syncmaster 900 monitor,except it was triple vision.
Was it sort of like three copies of the screen overlaying each other but 
offset, with white lines sort of flowing down where they split? (I know I'm describing this badly. I couldn't get a screenshot though.) I thought it was my video card, a very old Ati rage 128, but now I'm wondering if it's the monitor itself.

After looking through the forums I found a thread that helped, though I can't find it at the moment, but it suggested editing xorg.conf to change Default Depth in the Screen section from 24 to 16. I backed up the working xorg.conf first, then went to terminal.
> sudo gedit /etc/X11/xorg.conf
 
In Section "Screen" I changed DefaultDepth to 16 and saved.

> Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage 128 (RF/SG AGP)"
	Monitor		"S/M 900NF"
	DefaultDepth	16
	

This worked for me, and boy was I surprised! At the next boot I got a nice non-divided login screen I could actually read. I should warn you that
I've actually managed to break X
twice :rolleyes: (Yes I am a n00b!) but I've always managed to get it up and running again with advice from the forum.

Just make sure you **back up** xorg.conf and you know how to get it back if something goes screwy.

---

### Post by thespazzz on 2006-01-17
You may also need to make a change to your Gnome Config to reflect the new Resolution and Refresh Rate.

---

