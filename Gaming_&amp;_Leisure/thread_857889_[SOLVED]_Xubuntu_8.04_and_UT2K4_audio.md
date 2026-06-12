---
title: "[SOLVED] Xubuntu 8.04 and UT2K4 audio"
date: 2008-07-13
forum: Gaming &amp; Leisure
---

### Post by kdorf on 2008-07-13
Did a search for this one already and saw other people had the same problem, but I didn't get any solution that worked for me.

Unreal Tournament runs just fine, but there isn't any sound. I tried installing the "libopenal0a" package but it didn't help.

I had the same problem using vanilla Ubuntu 8.04 before and didn't figure out how to get things working. However, when I was trying out Arch Linux, UT played sound just fine (I was using ALSA there, just as with this setup.)

Any ideas?

---

### Post by NovruzeliH on 2008-07-13
lol uhhm try using ALSA here :p, if not working install virtual box, with xp, then play :p the games there

---

### Post by kdorf on 2008-07-13
If you had read my post, you would see that I did say I was using ALSA. And 3D accelerated games don't work at all in Virtualbox or the current release version of VMWare.

---

### Post by kdorf on 2008-07-15
Bump. Still no ideas as to how I can get this working? Has anyone tried compiling OpenAL from source before?

---

### Post by Cappy on 2008-07-15
There are some sound libraries in UT2004's system folder. You should delete/rename them and link them to the /usr/lib versions.

Etc.
```
ln -s /usr/lib/libopenal.so.0 <ut2004 directory>/System/openal.so
```

Also, you may want to try running the game with ```
aoss ut2004
```
which is in package alsa-oss

---

### Post by kdorf on 2008-07-15
The symlink to the libopenal.so library worked great! Why didn't I think of that?

---

### Post by dennymallow on 2008-12-08
I had the same issue, and I really want to thank you for the advices!!
In my case, the second method was the answer!
:guitar:

---

