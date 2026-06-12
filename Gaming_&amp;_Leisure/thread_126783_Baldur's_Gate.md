---
title: "Baldur's Gate"
date: 2006-02-07
forum: Gaming &amp; Leisure
---

### Post by glassgloss on 2006-02-07
So I have istalled a full install of bg... no problems

now when I cd to the folder, and then do wine bgmain.exe it takes me to the "insert cd 1 screen" even when its in

if i do wine baldur.exe it opens the autorun thing, then I click play, and nothing happens

I think it is not detecting the disk.

Any ideas?

---

### Post by geo926 on 2006-02-07
Try a no cd patch, this has helped me a few times.

---

### Post by glassgloss on 2006-02-07
is there a walkthrough to show you how to make an iso and mount it?

isnt that a no-cd patch? or are these different things...

---

### Post by geo926 on 2006-02-07
[www.gamecopyworld.com](www.gamecopyworld.com) This site is legal as long as you own the original game. Just search for BG, and Mods sorry if this isn't allowed....

---

### Post by leech on 2006-02-08
The problem isn't that the ISO isn't there, or that the CD is there.  The problem is that Wine does not support (and more than likely will never support) CD copy protection schemes such as Safedisk, StarForce, etc.  I had to use a No-CD crack on Soldier of Fortune 2 as well under wine for this very reason.  I know one of the Unreal Tournament games had a copy protection scheme for the linux version that worked as it should, but I'm not sure if it just checked to see if the files were on the CD or not.  

Leech

---

### Post by bnutting on 2006-02-08
I fought with this same type of thing with a different game in Wine. The one thing I had to do in order to get it to work was to use winecfg or winetools (depending on what version of wine you have installed). Make sure your CD-ROM is assigned a drive letter, just doing an auto configure worked for me, and make sure it is of type 'cdrom'. I think you have to click on the drive letter and then go to Advanced to see the dropdown.

Sorry I'm not on my system right now, so I don't remember every detail.

Hope this helps.
Bryan

---

### Post by polpak on 2006-02-08
[QUOTE=leech]The problem isn't that the ISO isn't there, or that the CD is there.  The problem is that Wine does not support (and more than likely will never support) CD copy protection schemes such as Safedisk, StarForce, etc.  I had to use a No-CD crack on Soldier of Fortune 2 as well under wine for this very reason.  I know one of the Unreal Tournament games had a copy protection scheme for the linux version that worked as it should, but I'm not sure if it just checked to see if the files were on the CD or not.  

Leech[/QUOTE]
It does support SafeDisk copy protection. You just have to use winecfg to set your cdrom drive to type cdrom and it should work fine.

---

