---
title: "WTF does this happen?"
date: 2005-04-04
forum: Desktop Environments
---

### Post by denzilla on 2005-04-04
First, let me say that Kubuntu is shaping up to be a very nice Linux Distro. Thanks for all the hard work, thus far :)

Okay, now that I've paid repect to the Kubuntu Devs, there is an annoying issue that plagues Kubuntu at the moment. Why does Konqueror decide to crash so much? It just decides to crap itself on me for no reason at all. I will browse to my home folder or go to my storage media or the control center and BOOM!!! Crash error message (SIG11) If I enable view of hidden files and go within a hidden file and back out to the beginning, it shows a duplicate folder for every folder I have in the directory until I completely exit the dir or de-select hidden file view. My Kubuntu installation was so unstable last night that I had to re-install the OS again just to get it usable. I have it fully updated using Kynaptic. There is nothing wrong with my hardware.

Kubuntu is the distro I plan on sticking with because its the first distro that my unclocked brain is finally clicking with. The random crashes are just ruining the experience for me :( I know that its still beta, but please look into this before the final release.

Thanks again

---

### Post by Frustration on 2005-04-04
I'm getting the same crash error at the home folder.  Its gradually getting better but its unpredictable. 
Hopefully it'll get sorted.

---

### Post by denzilla on 2005-04-04
It got better for me at one point but last night, it all went to hell. Didn't change anything, so not sure what the problem is. I'll post the error text if its wanted.

---

### Post by Glanz on 2005-04-04
I do not use KDE but I have found while helping others straighten out those initial crashes, that one login as root, or rather "File Manager Super User Mode" and then mucking around a bit WITHOUT CHANGING ANYTHING BUT THE PREFERENCES for that mode, will help out sometimes. Why, I don't know, but it has worked for me with older versions of KDE on several occasions. When you do this, be really careful not to move or delete files. Just look around. That's all. In the past I have done this as root system login, without being connected to the net of course. So if you have the ability to log in to the system as root, try that. Just for a little tour in the file manager and nothing more. If not, try the SU mode via sudo perhaps or gksu. 

Remember to DO NOTHING in the way of changes when in SU mode or as system root, but to configure a few file manager preferences via the drop-down menus. And always take a deep breath before hitting "enter"....

---

### Post by bosteen on 2005-04-05
Denzilla, a couple of bits of info needed...

1) Do you have windows/other partitions that you access through KDE? (ie Networked/NTFS/FAT32)
2) Do you have file previews set to on? konqueror - "Settings -> Configure Konqueror ->Previews"
3) Does it crash with any pattern? (from earlier posts, I'd guess not, but I have to ask)
4) Do certain folders give you problems?
5) Do you web-browse with konqueror?

And really the first question on the heap should have been -
6) Do you use an ATI card with the drivers installed? If so, you might want to try adding - *Option      "nodri"     "yes"* into your ati device section in /etc/X11/xorg.conf.
ie something like :
```

Section "Device"
        Identifier  "ATI Graphics Adapter"
        Driver      "fglrx"
        Option      "nodri"     "yes"
       ..... etc.

``` 

[Edit]
This turns off the acceleration from the ATI card. If this stops the crashing, then well, you at least know what it is...
[/Edit]


Good luck!
Ben

PS I agree that Ubuntu rocks. I feel I can say 'Linux is ready for the desktop' with certainty now!

---

### Post by aramazan on 2005-04-05
[QUOTE=denzilla]Why does Konqueror decide to crash so much?[/QUOTE]KDE 3.4 is too fresh. AFAIK KDE is known to re-release a stable update usually a month or so after each major release. So I wish Kubuntu would postpone the final Hoary release date just a bit to include soon to be updated KDE. It might set it back a month or so from Canonical Hoary (Gnome), but it would provide a stable distro for the next 5 months.

---

### Post by neighborlee on 2005-04-05
[QUOTE=aramazan]KDE 3.4 is too fresh. AFAIK KDE is known to re-release a stable update usually a month or so after each major release. So I wish Kubuntu would postpone the final Hoary release date just a bit to include soon to be updated KDE. It might set it back a month or so from Canonical Hoary (Gnome), but it would provide a stable distro for the next 5 months.[/QUOTE]
-------------
agreed 100%...I did not know this was the case but surely safely first <G>

that is the debian way afterall and in this case clearly warranted ;-)

cheers
nl
------

---

### Post by denzilla on 2005-04-05
[QUOTE=bosteen]Denzilla, a couple of bits of info needed...

1) Do you have windows/other partitions that you access through KDE? (ie Networked/NTFS/FAT32)
2) Do you have file previews set to on? konqueror - "Settings -> Configure Konqueror ->Previews"
3) Does it crash with any pattern? (from earlier posts, I'd guess not, but I have to ask)
4) Do certain folders give you problems?
5) Do you web-browse with konqueror?

And really the first question on the heap should have been -
6) Do you use an ATI card with the drivers installed? If so, you might want to try adding - *Option      "nodri"     "yes"* into your ati device section in /etc/X11/xorg.conf.
ie something like :
```

Section "Device"
        Identifier  "ATI Graphics Adapter"
        Driver      "fglrx"
        Option      "nodri"     "yes"
       ..... etc.

``` 

[Edit]
This turns off the acceleration from the ATI card. If this stops the crashing, then well, you at least know what it is...
[/Edit]


Good luck!
Ben

PS I agree that Ubuntu rocks. I feel I can say 'Linux is ready for the desktop' with certainty now![/QUOTE]



1.No
2."Local protocols" and "File" is checked only. Never changed it so its default.
3.No pattern other that just moving about Linux, and starting apps. No pattern to what app, either. Just whatever it thinks I should experience a crash with ;)
4.No, all areas/folders experience the same issue.
5.I installed FF through Kynaptic and it works fine. I used konqueror for awile, but missed FF. 

The machine tends to shit itself most when attempting to execute apps. If the app starts okay, it appears to work while its up. The odd folder issue is pretty much guaranteed to happen everytime though. 

ATI question:

Yes I am running an ATI card. Its an old ATI Xpert2000 Pro 32meg AGP (Rage128 chipset). No 3-D Acceleration is enabled because none of the OpenGL screensavers work. Can 3-D even work with this card? I am about to replace it with an Nvidia Geforce4 MX440 just to get some basic 3-D. Will I have to go through hell since Kbuntu is already configured with this POS ATI card?


*Crashed twice in less than 2 hours opening FireFox. Yay :(

*Heres that damned annoying folder glitch:

---

### Post by J. S. Jackson on 2005-04-06
[QUOTE=denzilla]Okay, now that I've paid repect to the Kubuntu Devs, there is an annoying issue that plagues Kubuntu at the moment. Why does Konqueror decide to crash so much? It just decides to crap itself on me for no reason at all. I will browse to my home folder or go to my storage media or the control center and BOOM!!! Crash error message (SIG11) If I enable view of hidden files and go within a hidden file and back out to the beginning, it shows a duplicate folder for every folder I have in the directory until I completely exit the dir or de-select hidden file view. My Kubuntu installation was so unstable last night that I had to re-install the OS again just to get it usable. I have it fully updated using Kynaptic. There is nothing wrong with my hardware.[/QUOTE]

I was having the same problem with Ubuntu installed, and KDE added on top.  So I thought I would try to reinstall, with Kubuntu only.  The problem still persisted.  Out of frustration, I switched back to Ubuntu/Gnome only.  :(

---

### Post by denzilla on 2005-04-06
I can't handle Gnome. Its just too basic looking too me, or at least it was when I tried Ubuntu a while back. KDE just appeals too me. I hope someone can fix this issue!

---

### Post by denzilla on 2005-04-06
Well, the system is now entering the unstable zone again :( Wants to crash every damn time I browse to home folder and storage media area. I disable memory conservation and turned everything off in the previews section of Konqueror. 

Pretty much at the end of my rope here. When is Kubuntu to be finalized again?

---

