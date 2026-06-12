---
title: "Video playback Problems"
date: 2006-09-07
forum: Desktop Environments
---

### Post by iceman504 on 2006-09-07
I been having some problems lately with video playback, its like when i go into full screen mode there will be this part of the media player that will freeze but the movie will still play also does this at normal size. Look at the attached screenshot to see what im talking about. I have compiz and XGL installed with a nvidia card also if that helps

---

### Post by iceman504 on 2006-09-07
does anybody know how to fix this problem, is it a codec i'm missing or something?

---

### Post by iceman504 on 2006-09-08
After disabling compiz from my sessions on startup using this guide [http://ubuntuforums.org/showthread.php?t=222034&highlight=XGL+Compiz]("http://ubuntuforums.org/showthread.php?t=222034&highlight=XGL+Compiz")
 the problems with playing videos stopped so im guessing i got to reconfigure my xgl/compiz setup or i got to reinstall it. I hope this helps anybody figure this out since i narrowed down the problem

---

### Post by kwalo on 2006-09-11
I noticed similar problems with wigdets, but they appeared without playing video. I solved this problem, by editing /etc/X11/xorg.conf.

I have nvidia card, so I don't know if it fixes problems with ati.

Run ```
sudo gedit /etc/X11/xorg.conf
``` Find section responsible for nvidia and add line labeled red:```
Section "Device"
        Identifier      "NVIDIA Corporation NV40M? [GeForce Go 6200]"
        Driver          "nvidia"
        BusID           "PCI:3:0:0"
[COLOR="Red"]        Option          "UseFBDev"              "true"[/COLOR]
        Option          "NoLogo"
EndSection
```This should solve problems with displaying wigdets although I'm no sure, if it helps with video playback.

---

