---
title: "Doom3+Alsa+libasound.so.2"
date: 2006-01-16
forum: Gaming &amp; Leisure
---

### Post by tszanon on 2006-01-16
Hi people!

I'm having this problem with Doom3: no sound when I select ALSA. I checked the messages and Doom3 says:
```
------ Alsa Sound Initialization -----
dlopen(libasound.so.2)
dlopen(libasound.so.2) failed: libasound.so.2: cannot open shared object file: No such file or directory
WARNING: sound subsystem disabled
```

So, I checked where I could find this file, and I found it at /usr/lib/libasound.so.2, which is a link to /usr/lib/libasound.so.2.0.0. I created a link in /lib, in /usr/local/games/doom3, in /usr/local/lib, but nothing worked.

What I ask you is: could you please tell me where, in your system, is this file? All I ask you is to run ```
find / -iname libasound.so.2
``` in Terminal and send me the results.

---

### Post by tszanon on 2006-01-19
Oh yeah. Forget about what I asked.

The problem is very simple: Doom3 has 32bit binaries, and my libasound.so.2 is a 64bit library. They won't match.

Thanks to chroot, I've got the 32bit version of libasound.so.2. I tell Doom3 to use surround51, but it can't, because of the frequency rating (surround51 can't use 44.1 KHz). Ok, as aplay told me, I tried to use plug:surround51 instead. I gave me these results:
```

------ Alsa Sound Initialization -----
dlopen(libasound.so.2)
asoundlib version: 1.0.9
opened Alsa PCM device plug:surround51 for playback
buffer size select failed: Invalid argument
close pcm
dlclose
WARNING: sound subsystem disabled

--------------------------------------
----------- Alsa Shutdown ------------
--------------------------------------
```
It's much better than before, but it's still not ok. As I still don't have any idea of how I can fix that "buffer size select failed", I still don't have surround sound working in Doom3.

---

### Post by pentadrago on 2007-06-22
I had the same problem trying to get doom 3 to use my alsa configuration. 
I'm using a Terratec Aureon 5.1 Sky with the .asoundrc from [http://http://ubuntuforums.org/showthread.php?t=400268]("http://http://ubuntuforums.org/showthread.php?t=400268") (it's the same chip) and solved it by increasing buffer_size from 5120 to 6652. After that I had no more problems with the sound.

---

### Post by Cappy on 2007-06-22
or
```
sudo apt-get install lib32asound2
```

---

