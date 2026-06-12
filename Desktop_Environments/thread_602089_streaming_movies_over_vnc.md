---
title: "streaming movies over vnc"
date: 2007-11-03
forum: Desktop Environments
---

### Post by skydemon on 2007-11-03
Hi, not sure if this should go in here or networking...but anyway I am trying to stream movies from my PC (running gutsy) to a winxp laptop over a wireless LAN using vnc, however I have tried x11vnc, vino, tight vnc etc, plus a few different vnc clients and when ever I try to play a movie all I get is a black screen within the movie player on the laptop even though the movie is playing on the pc (the rest of the desktop is displayed as normal on the laptop). I have also tried totem and vlc with the same problem.

Can anyone help?

Cheers

Mick

---

### Post by krunge on 2007-11-03
For x11vnc try adding the option: ```
-noxdamage
``` to work around a bug in compiz, etc.

Are you sure you want to stream video with VNC?  Isn't there much better software & compression algorithms for this?  Also, if sound is required, how will you be handling that?

---

### Post by skydemon on 2007-11-03
ah dont worry about it, im an idiot :)

I used to do it over a sole win network and just open the file over SMB for local playback but for some reason I thought I did it using vnc (didnt even think about the fact it wouldnt play sound), sorry about that thanks anyway

---

