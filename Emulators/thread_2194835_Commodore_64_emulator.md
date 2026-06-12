---
title: "Commodore 64 emulator"
date: 2013-12-20
forum: Emulators
---

### Post by michael-piziak on 2013-12-20
ok.  I get the Commodore 64 emulator from the software center - C64 shows up on my dash to the left.
I download and unpack the .zip file for the "4th & inches" rom; however, double clicking the file "4th.inches.d64" doesn't start the game.  Neither can I click on the c64 on the dash to get it started.
I then download "hardball" rom and have the same problem.

help please

---

### Post by QIII on 2013-12-21
*Moved to **Emulators***

---

### Post by kostkon on 2013-12-22
I will only give you a hint: you need to get the roms for the various Commodore 8-bit systems (the ones supported by Vice, that is) and place them into the hidden folder named *.vice* that should be in your home folder (otherwise, just create it yourself).

Also, it's not necessary to unzip your games before loading them.

Hope that helps.

---

### Post by michael-piziak on 2013-12-22
I created a folder named .vice.  It disapeared.  So I created a folder named .vice on desktop, dragged 2 roms into it, then put it in my home folder.  It disapeared again.  Now, all I have is C64 on my dash to the left.  Clicking it does nothing.
Maybe my problem is I'm getting the C64 from the Ubuntu Software Center ?

---

### Post by kostkon on 2013-12-22
> **michael-piziak said:**
> I created a folder named .vice.  It disapeared.  So I created a folder named .vice on desktop, dragged 2 roms into it, then put it in my home folder.  It disapeared again.  Now, all I have is C64 on my dash to the left.  Clicking it does nothing.
Maybe my problem is I'm getting the C64 from the Ubuntu Software Center ?
You need to select *View -> Show Hidden Files* from Nautilus' menu to be able to see the hidden folders.

Have you downloaded the right files? My .vice folder looks like this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=248816&d=1387745528&stc=1[/IMG]

I have the version from the USC and it runs games just fine (you might need to fiddle with the keyboard/joystick controls a bit, though)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=248817&d=1387745529&stc=1[/IMG]

---

### Post by michael-piziak on 2013-12-22
ok I can see the hidden folder I created called ".vice"   However, double clicking them does nothing.  Also, c64 on dash to left is all I have, and I can't drag that to the .vice folder

---

### Post by kostkon on 2013-12-22
Sorry, my mistake; when I said "roms" I meant the copies of the ROM chips that contained the Operating System, BASIC, etc. that those machines came with, not your copies of disks or tapes. I can't give you the download url because that would be against the forum rules, so you need to google for "vice commodore roms" or something similar.

Unpack those rom files in the .vice folder, then search in the dash for "commodore", run Commodore 64, for example, then select File -> Smart Attack disk/tape from the menu and choose the .zip file of the game or app you want and it will load it for you.

Hope that helps.

---

### Post by michael-piziak on 2013-12-22
Perhaps someone could tell me the url that is n00bsonubuntu in this video

[https://www.youtube.com/watch?v=giSot42sK5I](https://www.youtube.com/watch?v=giSot42sK5I)


I'm going to have to give up on getting c64 to work if I can't find some easier instructions.  I'll try another emulator.

---

### Post by mips on 2013-12-23
[http://www.thelinuxguy.nl/how-tos/how-to-emulate-the-commodore-64-on-debianlinux/](http://www.thelinuxguy.nl/how-tos/how-to-emulate-the-commodore-64-on-debianlinux/) Scroll down to the section wrt the *zimmers* web site.

---

### Post by michael-piziak on 2014-11-18
Much thanks to **kostkon**.  I revisited this today and following his instructions and studying his screenshot, I was able to get Commodore 64 from the software center to work!   

The load time, for game roms, almost reminds me of how long it took to load games back then!  Patience is a necessity.  Now I just need to figure out how to get my digital gravis gamepad pro to be recognized by the emulator.

Marking this thread as solved.

p.s. Thanks **mips **also, I was going to try your solution next.

p.s.s. It's really fairly simple to get this running.  Download Commodore 64 from the software center. Then go to " http://www.zimmers.net/anonftp/pub/cbm/crossplatform/emulators/VICE/old/vice-1.5-roms.tar.gz" which downloads vice-1.5-roms.tar.gz to your download folder.  A few double clicks on the vice-1.5-roms.tar.gz get you to a folder named "data"    Move the "data" folder to your home folder.  Then, rename the "data" folder to ".vice"   The .vice folder will disappear and Commodore 64 emulator works !

---

