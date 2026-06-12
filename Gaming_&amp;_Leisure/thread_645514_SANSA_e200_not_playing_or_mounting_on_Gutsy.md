---
title: "SANSA e200 not playing or mounting on Gutsy"
date: 2007-12-20
forum: Gaming &amp; Leisure
---

### Post by LegoAddict on 2007-12-20
Ok, so I'm running Ubuntu 7.10.  My mp3 player (Sansa e200) gives me grief when I try to get music from it.  It used to mess up Rhythmbox, but now it just does nothing and quietly crashes RB.

I ran rhythmbox in Terminal and here's my output:

chris@chris-ubuntu-laptop:~$ rhythmbox
Potential MTP Device with VendorID:0781 and ProductID:7420 responded to control message 2 with a response that was too short. Problems may arrise but continuing
PTP: Opening session
PTP_ERROR_IO: Trying again after resetting USB
Clearing stall on IN endpoint
Clearing stall on OUT endpoint
PTP: Opening session
Segmentation fault (core dumped)


This exact same mp3 player worked perfectly with no changes in my old Feisty installation.

Help?

---

### Post by Vadi on 2007-12-20
Oh this is not good, my e280 is just on it's way.

You might want to file a bug report in rhythmbox for this, and use exaile/amarok/vlc/mplayer for now..

---

### Post by cogadh on 2007-12-20
Not sure if the e200 is similar to my Sansa m240, but in order for it to connect correctly, I had to swith the USB setting on the player from autodetect to "MSC". Also, if the player has any DRM protected music on it, it won't connect properly at all. You'll need to delete everything off the player before you connect it.

---

### Post by Vadi on 2007-12-20
Now there's a good incentive not to use drm'd music! ;)

---

### Post by cogadh on 2007-12-20
Yeah, it took me forever to figure out that the two tracks with DRM (Napster purchase) on the player were preventing it from connecting. It was killing me because I had previously connected the player with absolutely no issues. I've got to look into FairUse4Win again, if I can get rid of the DRM on the 200+ tracks I've purchased, then that is one less thing I need Windows for.

---

### Post by software pimp on 2007-12-21
Im having the same problem as Lego 
Trying to switch to Linux but obviously such hiccups are slowing the psocess 
HELP!!!

---

### Post by cogadh on 2007-12-21
Did you check any of the things that I suggested to Lego?

---

### Post by software pimp on 2007-12-22
yeah - but MSC doesnt give you the playlist mode that i want - i'll keep looking 
thanks

---

### Post by LegoAddict on 2007-12-25
I don't have any DRMed music and I've tried both settings, and it still doesn't work. :(

---

### Post by software pimp on 2007-12-30
when in MSC mode does it show up on the desktop?
If not- 
still in MSC --> turn of your Sansa
                       connect it to your comp
if it still doesnt show up
                        restart ( do not unplug your device) 
(i know it's annoying) but it should show up then.
worked for me.
As for the music player  - i had to use amarok - rhythmbox kept on disappearing on me everytime i plugged in my Sansa

---

### Post by marcordenis on 2007-12-31
dunno if this will help, but check this out (it worked for me):
[http://ubuntuforums.org/showpost.php?p=3798461&postcount=118](http://ubuntuforums.org/showpost.php?p=3798461&postcount=118)
to be found on the Beginners Guide to a Sansa e200 thread ([http://ubuntuforums.org/showthread.php?t=312196](http://ubuntuforums.org/showthread.php?t=312196))

---

