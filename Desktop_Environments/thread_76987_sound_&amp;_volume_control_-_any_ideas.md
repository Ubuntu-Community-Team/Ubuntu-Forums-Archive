---
title: "sound &amp; volume control - any ideas?"
date: 2005-10-16
forum: Desktop Environments
---

### Post by bionnaki on 2005-10-16
hello. I have an audigy 2 soundcard & was able to get sound by simply selecting my card in system>preferences>sound : "default sound card: Audigy 2 ZS [SB0350]"

Sound works great except for one thing - I cannot control the volume with anything but my acutal speakers and media players like Totem. Keyboard volume buttons do not work. Volume Control does nothing. 

I can increase/decrease volume in Totem, but any application external to this does nothing (i.e. Volume Control).

Any ideas on how I can fix this? Volume control worked just fine in Hoary...

Thanks!

---

### Post by Tralobyte on 2005-10-16
A workaround is to use xev, xbindkeys, and aumix. Xev lets you find out what events the volume control sends out, and xbindkeys lets you bind the event to the commands "aumix -v +3" and "aumix -v -3".

---

### Post by bionnaki on 2005-10-16
ok. thanks.
...so, what do I do?

---

### Post by bionnaki on 2005-10-16
...I also suspect the same reason why volume controls do not work is the same reason why audio in some applications do not work (while working in others)...

---

### Post by bionnaki on 2005-10-16
ok. so I've been playing around with this...

I noticed in my bios settings I had my onboard sound enabled (+ my audigy2 card). I disabled the onboard & logged into ubuntu. I can now control volume and sound works in most of the media applications, but I have no system sounds (beep, bongos, etc.). Also, I have no sound in any of the gnome games...when I go to system>preferences>sound : sound events, I cannot hear the listed .wav files either when played through gnome, but when I copy the .wav file & play directly through my media players, they play just fine.

I have audigy2 soundblaster set as my default in sound preferences.

I cannot figure out how to disable my soundcard in bios for further troubleshooting, so I am going to take it out & see what happens with just onboard sound...

anyone know how I can get my system sounds back & keep my soundcard?

thanks

---

### Post by bionnaki on 2005-10-16
ok, so I rebooted once again...
and well, everything works...all sounds play as they should :p 
I probably just had some wrong setting (wrong default card perhaps)
and needed to reboot.
having onboard sound + the soundcard both enabled screwed things up originally.

oh well
works now
later!

---

