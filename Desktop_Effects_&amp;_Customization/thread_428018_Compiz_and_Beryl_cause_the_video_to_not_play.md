---
title: "Compiz and Beryl cause the video to not play"
date: 2007-04-29
forum: Desktop Effects &amp; Customization
---

### Post by CSMatt on 2007-04-29
Ever since I upgraded to Feisty, I can't seem to play videos while either Compiz or Beryl (the ones in the repositories) are running.  The audio plays fine, but the player just displays a blank screen.  Maximizing and then restoring the window can sometimes coax the player to redraw the video and thus cause it to appear, but nothing other than switching to Metacity seems to allow me to view video right away.  This occurs regardless of the codec used (it even happens with Theora videos) and the player used (Totem/GStreamer and VLC both do this).  This never happened when I had Beryl installed from the Beryl-project's repositories while I was using Edgy.  I made sure to uninstall Beryl and remove their repository list before upgrading, although I left the .beryl folder in my /home/username folder.  I haven't used Compiz from another location or at all on Edgy, so it seems that the Compiz and Beryl versions that are in the Ubuntu repositories are to blame.  Is there any way I can fix this?  Compiz and Beryl are using the free ATI driver (ati, not radeon) with AIGLX.

---

### Post by nexx on 2007-04-30
alt f2
start:    gstreamer-properties
Choose x window system in the video output, same for VLC but the you have to do it in the VLC menus.

---

### Post by CSMatt on 2007-04-30
That fixed it (I had to choose the "(no Xv)" option for GStreamer and the "X11 video output" option in VLC).  Thanks for the workaround.  However I still don't see why it didn't automatically detect to use these to begin with when it seemed to detect to use them under Edgy with the official Beryl.

---

### Post by whistlerspa on 2007-05-05
I had the same problem and the your help enabled me to fix the video problem - thanks. 

You lost me on the VLC thing though. What is this and how do I access it exactly?

---

### Post by dmjones500 on 2007-05-07
Open VLC, go to Video->Output Modules and change to "X11 Video Output".

---

### Post by litmus on 2007-05-08
Hi, this is a bit of a flawed solution because when choosing X11 instead of XV for video playback you lose all the hardware acceleration, scaling etc. That is, you lose a lot of quality when playing a video and its extremely CPU consuming (just try to play on x11 fullscreen and you'll know what i mean). 

Has anyone found a way of fixing this black video problem WITHOUT having to downgrade the video to X11 (ie. keeping the XV driver????)

Thanks in advance!

---

### Post by taj151 on 2007-07-06
Good temp fix for now till I find a way to turn the settings back on. Thanks a lot.

---

### Post by reacocard on 2007-07-06
> **litmus said:**
> Hi, this is a bit of a flawed solution because when choosing X11 instead of XV for video playback you lose all the hardware acceleration, scaling etc. That is, you lose a lot of quality when playing a video and its extremely CPU consuming (just try to play on x11 fullscreen and you'll know what i mean). 

Has anyone found a way of fixing this black video problem WITHOUT having to downgrade the video to X11 (ie. keeping the XV driver????)

Thanks in advance!

I've never been able to get VLC to work under beryl with anything other than X11, but xine (package xine-ui) works perfectly with xv under beryl/compiz for me, as does totem-xine.

---

### Post by Nikitas350 on 2007-07-25
I tried this solution that you offered (to select X Window System (no Xv)) and the video works fine. But when I am trying to play an .avi video with subtitles in full screen there subtitles are not appeared properly. Thanks for the help and if anyone knows the answer i would like to hear of it. Thankssss

---

