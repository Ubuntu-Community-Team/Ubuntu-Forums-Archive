---
title: "warcraft 3?"
date: 2006-01-05
forum: Gaming &amp; Leisure
---

### Post by akurashy on 2006-01-05
wondering if warcraft3 runs in linux? any installer or at least info from WINE?

---

### Post by Lord Illidan on 2006-01-05
It should work in cedega. In wine there is support but not too great.

---

### Post by kaamos on 2006-01-05
> In wine there is support but not too great.

I have it running almost perfectly on wine 0.9.x. Had to do a small dll-fix to get campaign mode going, but otherwise it worked great out of the box. The only thing that doesn't work are the movies, but they can be played with mplayer anyway..

---

### Post by Lord Illidan on 2006-01-05
[quote=kaamos]I have it running almost perfectly on wine 0.9.x. Had to do a small dll-fix to get campaign mode going, but otherwise it worked great out of the box. The only thing that doesn't work are the movies, but they can be played with mplayer anyway..[/quote]

But the cursor remains like a crosshair? And the sound? And the speed?

---

### Post by kaamos on 2006-01-05
Cursor is normal, sound works (also character sounds that were messed up with pre-beta wine). Speed is just about the same as in windows when running with -opengl.

Has been like this for be since wine went to beta. Now running 0.9.5.

---

### Post by Aramil on 2006-01-05
Where can i find a HOWTO for installing Warcraft 3?Because i installed it with Wine but when i try to run it the programm asks for the CD although the CD is in the drive....Plz dont link me to wine's URL cause I m a bit noob and  i dont understand what they say...

---

### Post by kaamos on 2006-01-06
Make shure (by running winecfg ) that your cd-drive is recognised as that and not a harddrive by wine. I had to set mine by hand.

Other than that, I suggest renaming the movies folder so the game won't try to play them, and remember to use the -opengl flag when starting the game. Like this: wine "Warcraft III.exe" -opengl

---

### Post by Aramil on 2006-01-06
How can I set winecfg to recognise my CD rom drive?

---

### Post by kaamos on 2006-01-06
open a terminal and type "winecfg". Then choose to drives tab. Find the drive that points to /dev/cdrom0 (mine was F:) and click an "show advanced". Change the type to CD-ROM if it is says something else.

The names might be a bit different as I just translated from the finnish names. Hope this helps!

---

### Post by stratotak on 2006-01-06
just launch winecfg..go to drives tab..auto detect..if it dosent set it up correctly you can enter the correct path for cd/dvd-rom..

---

### Post by frodon on 2006-01-06
This thread may help you : [http://ubuntuforums.org/showthread.php?p=284312#post284312](http://ubuntuforums.org/showthread.php?p=284312#post284312)

---

### Post by Aramil on 2006-01-06
Thx a lot!!!!I managed to start Warcraft!But now i cant see the cursors?Is that because of Wine?Also the graphics r a bit choppy...And I think there is no sound as well......

---

