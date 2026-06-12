---
title: "Wine and ALSA"
date: 2005-08-09
forum: Gaming &amp; Leisure
---

### Post by und3rdog on 2005-08-09
Thanks to all the fellow nerds on this forum I've finally been able to play sounds in gnome.  <SHOUT OUT to the ubuntu guide here> However, now I'm trying to get sound out of games run with Wine <back port available version>, specifically Diablo 2 Classic.  Has anyone successfully edited thier wine config file to do this?  Cheers.

-Luke

BTW - Another interesting fact is I've only been able to run things in "DESKTOP" mode, and while I define my desktop to be 1024x768 in the config file, in Diablo 2 it shrinks itself back to 640x480 :roll: .  Any thoughts?

---

### Post by und3rdog on 2005-08-11
Bmp

---

### Post by varunus on 2005-08-11
Diablo 2 can only be run in 640x480.  (Or 800x600, if you have LoD.)  This isn't a Linux problem; ask blizzard for higher resolution if you want.   :) 

To get sound to work, you have to enable Hardware sound emulation under the directx section. Some option that's commented out, just uncomment it.  And use the ALSA driver.  I know it works, but I can't remember the config options since I don't have wine right now...

---

### Post by und3rdog on 2005-08-15
Thanks for the info!  I tried both the oss and alsa drivers w/ the [dsound] hardware option uncommented.  Sound in D2 is still no go.  I'll keep fiddling and post if I find the answer.

---

### Post by dtessier on 2005-09-28
[QUOTE=und3rdog]Thanks for the info!  I tried both the oss and alsa drivers w/ the [dsound] hardware option uncommented.  Sound in D2 is still no go.  I'll keep fiddling and post if I find the answer.[/QUOTE]

If you ever figure it out, please let me know. I used to have sound going in Hoary, but now that I've installed Breezy I lost it, and I don't remember exactly what I had done to get it going. Or it may simply be that I'm now using a different version of Wine...

---

### Post by DarkKnight on 2005-12-11
[QUOTE=dtessier]If you ever figure it out, please let me know. I used to have sound going in Hoary, but now that I've installed Breezy I lost it, and I don't remember exactly what I had done to get it going. Or it may simply be that I'm now using a different version of Wine...[/QUOTE]

You need a form of MIDI emulation for sound, search around the forums for some killer guides.

And for desktop, you'll need to set it to Manged="N"

---

