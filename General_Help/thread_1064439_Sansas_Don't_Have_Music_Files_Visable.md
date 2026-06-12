---
title: "Sansas Don't Have Music Files Visable"
date: 2009-02-08
forum: General Help
---

### Post by Lexda on 2009-02-08
In short, I can't get the music files on my Sansas (a 2gb Clip and an e280) to appear in Intrepid. When I'm trying either one I get it successfully mounted, and can see the top level files. However, when I enter the "music" folder, nothing appears. I know there is something there, however, as there isn't any room on the e280, and only 200mb free on the Clip.

I've tried opening a Root Nautilus window, showing hidden files, and checking through all of the other system folders, but nothing shows up.

The first time I plugged the e280, I could view the music files. I wanted a clean wipe to throw more on with updated metadata, so I deleted them all. That's when the problems started. Eventually I deleted the ".Trash-1000" folder, but even that didn't help; it was still shown as being full. Unfortunately, no music file will play when the player is turned on normally; database refreshing continues indefinitely.

The Clip has never worked. I've never seen any music files in them. However, I can still listen to the music I originally put on there in XP.

Both players are in MSC mode.

Any help would be greatly appreciated!

---

### Post by pbotros1234 on 2009-02-08
Try this, assuming your sansa is mounted at /media/sansa

```
find /media/sansa/.
```

That should list everything on your mounted sansa. If this does not work, then it is probably a hardware-specific problem.

---

### Post by inigomontoya on 2009-02-08
check to see if the files are hidden in xp, if so unhide them

---

### Post by Lexda on 2009-02-08
All I get from the output is 

```
/media/Sansa
/media/Sansa/MUSIC
/media/Sansa/SYS_CONF.SYS
/media/Sansa/version.sdk
/media/Sansa/RECORD
/media/Sansa/RECORD/FM
/media/Sansa/RECORD/VOICE
/media/Sansa/RECORD/VOICE/VORC001.WAV
/media/Sansa/AUDIBLE
/media/Sansa/MTABLE.SYS
/media/Sansa/RES_INFO.SYS

```
, so there are no hidden files on there.

Any clue if a reformat could work, if I copied off the system files and put them back on one at a time looking for the culprit? Or would that completely bork the player?

---

### Post by pbotros1234 on 2009-02-08
Personally, I wouldn't reformat the MP3 player, because with MP3 players they might have different partitions / special files / specific different things that might make it unusable afterwards.

You can try looking at Sansa documentation to find your music? If you can't see the songs on Windows then it is definitely a SANSA problem.

---

### Post by inigomontoya on 2009-02-08
I have a sansa e200v1, if i remember correctly there is a format option in the settings.  You may want to try that.  If that doesn't help, try heading over to the folks at [http://anythingbutipod.com](http://anythingbutipod.com) they are sure to know what the problem is.

---

