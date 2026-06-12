---
title: "Totem: 'cdda:///dev/hdc' not a valid URL"
date: 2006-06-07
forum: Desktop Environments
---

### Post by jeremyk on 2006-06-07
Totem refuses to play an audio disc.

Totem->Movie->Play 'Audio Disc' is not not available.

When I do Totem->MOvie->Open, I finally get:

'cdda:///dev/hdc' not a valid URL

Same error in Nautilus (when I try to open the Audio Disc)

PLease HELP!!!!!!!!!!!!!!

Thanks

---

### Post by jeremyk on 2006-06-10
Anyone? please.

---

### Post by mgmiller on 2006-06-10
What is in your system>preferences>removable drives and media preferences under the multimedia tab for Audio CD discs?  The default entry is:
gnome-cd --unique --play --device %d

If you have more than 1 optical drive in your system, try putting the disk in the other drive.

It sounds like your totem is getting confused about the cdda database, I'm not sure how to fix that.

---

### Post by jeremyk on 2006-06-11
Thanks for your answer. The entry, I have in system>preferences>removable drives and media is: 
sound-juicer -d %d

I tried your suggesttion, but it did not change anything to the problem. BTW, gxine can read audio disc (mplayer and vlc as well). 

I would read like to solve the problem. If someone can help, thanks in advance.

---

### Post by jeremyk on 2006-06-11
Maybe someone knows why totem and nautilus do not know:
cdda:///dev/hdc/

Even more important: how to fix it????

Please:confused: 

Thanks in advance :)

---

