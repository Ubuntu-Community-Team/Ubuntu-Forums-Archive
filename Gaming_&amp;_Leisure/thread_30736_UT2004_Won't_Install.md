---
title: "UT2004 Won't Install"
date: 2005-04-30
forum: Gaming &amp; Leisure
---

### Post by mbreslin on 2005-04-30
I'm trying to install UT2004.  Copied the linux-installer.sh file to my desktop and ran it, and after agreeing to the license and typing in the product code, it unpacks itself then ask me to:

```
Please mount the Unreal Tournament 2004 Play Disc CDROM.
Choose Yes to Retry, No to Cancel.
```

I'm installing it from a DVD, which has a folder for each CD on it, e.g., cd1, cd2, cd3, etc.  It can't seem to find the DVD.  I even tried copying the contents of the DVD to my desktop and running it from there, but that did no good.

Can anyone suggest a solution to this problem?  Thanks.

---

### Post by SFN on 2005-04-30
Type

```
"sudo export SETUP_CDROM=/media/dvd"
``` 

Replace "/media/dvd" with the actual path to your DVD drive. Once that is done, try running the setup again.

---

### Post by mbreslin on 2005-05-01
Thanks!  It works now!

Next question:
    How can I get the sound to work?  The game's Audio Mode is OpenAL.  I suspect I have a general sound problem -- I've never heard a single sound since I installed Ubuntu last week.  Should I open up a new thread in a more general forum regarding sound?

Mike

---

### Post by GigaShadow on 2005-05-01
I would like to "hear" comment about this as well (no pun intended.....). My UT2004 is now totally silent, although I can play cds' and listen to online raidio without issue...can anyone help?

                 G

---

### Post by jdodson on 2005-05-02
some have reported that killing the "esd" proccess helps them get sound in games.  do a forum search for "esd" or "sound issues" and you can find info there.

only downfall is the desktop sounds will be disabled until you either reboot or run

```
esd &
``` 

 from the console.

---

### Post by mbreslin on 2005-05-03
But if I don't even have desktop sounds, doesn't that mean I have more serious issues than killing esd?  I plan to read up tonight on alsa and see if I can't get any clues as to why I have no sound.  If you can think of anything else I should look into, please let me know.  Thanks.

---

### Post by CellarDoor on 2005-05-05
1st thing to do is make sure the sound system is enabled, and/or the volume is up :razz:

( I forget exactly where that is in gnome as I'm using KDE but it shouldn't be hard to find )

 ;-)

---

### Post by obx-jdt on 2005-05-05
Ok, I'll be honest here  :roll:  I'm still waiting on my copies to get here (Been useing Mandrake for about 2-3 years, read up on Ubuntu & thought I'd give it a try).... But I assum Ubuntu uses ALSA. I'd check to make sure it's configured correctly, and ckeck over at [sourceforge](http://sourceforge.net/) for the latest version.

---

