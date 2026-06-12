---
title: "WoW &amp; Sound"
date: 2005-05-15
forum: Gaming &amp; Leisure
---

### Post by tekwerx on 2005-05-15
Ive looked through the forums, but didnt find an answer...has anyone found a way to fix the problem with Cedega (specifically WoW) & 5.04 so you can have your normal system sounds while playing WoW?  I have to do "killall esd" to play WoW with sound, then reboot the machine after Im done to get regular system sounds & MP3s.  Was wondering if theres a fix for this or something...thanks in advance...

---

### Post by Xeppo on 2005-05-16
you could always just re-enable ESD from the terminal by typing "esd"

---

### Post by SKLP on 2005-05-16
This problem is not a wow problem but a problem with your sound card. No hardware mixing of channels is supported so therefore, only one application may access the sound card at any one time. Normally all the sound goes thru ESD and therefore it works, but since Cedega (and wine) uses ALSA or OSS directly, you have to kill esd to get it working.

Or, you could enable ALSA software mixing (dmix) :)
Search the forums for howtos... glhf

---

### Post by tekwerx on 2005-05-16
[QUOTE=SKLP]This problem is not a wow problem but a problem with your sound card. No hardware mixing of channels is supported so therefore, only one application may access the sound card at any one time. Normally all the sound goes thru ESD and therefore it works, but since Cedega (and wine) uses ALSA or OSS directly, you have to kill esd to get it working.

Or, you could enable ALSA software mixing (dmix) :)
Search the forums for howtos... glhf[/QUOTE]
 Hey thanks guys for your help!!!

I got it working!  

WOOT!  :)

---

