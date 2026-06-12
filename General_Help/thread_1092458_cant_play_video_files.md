---
title: "cant play video files"
date: 2009-03-10
forum: General Help
---

### Post by Kaneda187 on 2009-03-10
Ok fresh install, installed codecs but every time i try to open them in VLC or movie player it opens i get a second of audio then it closes...
any ideas?

---

### Post by klemens on 2009-03-10
have you already installed you're graphic drivers?

---

### Post by klemes on 2009-03-10
Try to launch vlc from the console and see what type of errors it gives you,and also try to play the files in mplayer.

---

### Post by Kaneda187 on 2009-03-10
yeah i have its an ATI Mobility Radeon X1400

this is the Error out put from the terminal...
```
Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  83
  Current serial number in output stream:  84

```
Never had this problem befor:(.... any clues?
Thanks!!:)

---

### Post by Kaneda187 on 2009-03-10
tried mplayer same problem...
it happens whatever player i use ive tried loads at this stage!

---

### Post by klemes on 2009-03-10
I've googled out the error description it gives you and although I haven't come across a solution yet I saw that others that had similar problems they occurred only when compiz had been activated and that deactivating compiz solved the problem.Well not exactly a solution but it is worthwhile to give it a try...
Also you can try to enable the XV instead of the X11 video output from the video properties of the vlc player under settings.

---

### Post by klemes on 2009-03-10
Also I came across this in launchpad:


> 
 Øyvind Stegard wrote on 2008-10-27: (permalink)

I've god Intrepid installed, and switched to EXA-acceleration in the radeon driver. It works great ! Video no longer causes crashes. I'm also pleased to see how much better the radeon-driver works compared to fglrx (for general non-gaming usage). I haven't observed any issues with corruption, yet.
 marmuta wrote on 2008-10-29: (permalink)

Please consider adding this option when switching to EXA:

   Option "AccelDFS" "true"

Without this flash videos slow down dramatically to some erratic 2 fps with 100% cpu.

Happens with EXA on a R430 [Radeon X800 XL] and
xserver-xorg-video-radeon 1:6.9.0+git20081003.f9826a56-0ubuntu2.


Hope that helps.:D

---

### Post by Kaneda187 on 2009-03-10
EXA?? probably a silly question. an alternative to flrx ati driver?

---

### Post by Kaneda187 on 2009-03-10
okay so i got it to by turning off compiz...but im not happy considering it work b4 with out doing that. I wish ther was just a Ati driver from AMD for linux that actually worked on all levels i mean i doubt for a company that size that it would be a major task!

---

### Post by klemes on 2009-03-10
> **Kaneda187 said:**
> EXA?? probably a silly question. an alternative to flrx ati driver?

Not at all.It's just an option in the driver section of the xorg.conf.
I wish someone with an ATI videocard could tell us the correct syntax for this.

---

