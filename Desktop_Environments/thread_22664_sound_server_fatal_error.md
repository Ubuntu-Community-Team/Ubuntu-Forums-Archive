---
title: "sound server fatal error"
date: 2005-03-28
forum: Desktop Environments
---

### Post by fizgig on 2005-03-28
Sometimes when I boot into KDE I get an error message that states: "Sound server fatal error: cpu overload, aborting"

Anyone know how to fix/troubleshoot this?

---

### Post by henla464 on 2005-04-02
I had this problem but solved it somehow. Recently I deleted my kde settings and now I have this problem again.

I think I found the solution in this forum somewhere but I can't find it anymore  :sad: 

Please report back if you find a solution.

---

### Post by Misogynist on 2005-04-29
[QUOTE=henla464]I had this problem but solved it somehow. Recently I deleted my kde settings and now I have this problem again.

I think I found the solution in this forum somewhere but I can't find it anymore  :sad: 

Please report back if you find a solution.[/QUOTE]
 I'm currently randomly experiencing the same issue in Hoary, running artsd 1.4.0 with esd as its output.

---

### Post by fizgig on 2005-04-29
It's still an issue with me.  If I play some music with Amarok (I think that's the program) my cpu temp goes critical.  If I play with XMMS, I have the ability to change outputs so I select ALSA and the cpu temp drops back to 53 or something (wherever it usually is) so it's a problem with the default playback filter kde, amarok and perhaps others use.

---

### Post by branco on 2005-07-21
I've had this very same issue. Finally, I've realised that if I turn off 'Full Duplex' option in the Sound preferences I don't get the error anymore.

---

### Post by AndreAPL on 2005-08-03
hi there. having ame problem  :-x  with or without Full Duplex, in a my laptop, with intel i810 audio :( :( :( 
with full duplex can't get any sound, without it sometimes sound crashs.

---

### Post by jetpeach on 2007-03-24
try
echo "options snd-via82xx dxs_support=2" |sudo tee -a /etc/modprobe.d/alsa-base
as described in this bug
[https://launchpad.net/ubuntu/+source/arts/+bug/66982](https://launchpad.net/ubuntu/+source/arts/+bug/66982)

---

