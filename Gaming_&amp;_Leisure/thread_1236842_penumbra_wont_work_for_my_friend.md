---
title: "penumbra wont work for my friend"
date: 2009-08-10
forum: Gaming &amp; Leisure
---

### Post by ELD on 2009-08-10
Okay basically my friend tries to run penumbra episode 1 and this happens:
```

souch13@rickypc:~$ '/home/souch13/PenumbraEp1/penumbra' 
open /dev/[sound/]dsp: Device or resource busy
Segmentation fault
Penumbra exited unexpectedly, please check
/home/souch13/.frictionalgames/Penumbra Overture/Episode1/hpl.log
for any error messages
Also try running
ulimit -c unlimited
And re-running Penumbra and try and recreate the error
then submit the generated core file or stack trace

```

Any ideas?

---

### Post by Dark Aspect on 2009-08-10
> **ELD said:**
> Okay basically my friend tries to run penumbra episode 1 and this happens:
```

souch13@rickypc:~$ '/home/souch13/PenumbraEp1/penumbra' 
open /dev/[sound/]dsp: Device or resource busy
Segmentation fault
Penumbra exited unexpectedly, please check
/home/souch13/.frictionalgames/Penumbra Overture/Episode1/hpl.log
for any error messages
Also try running
ulimit -c unlimited
And re-running Penumbra and try and recreate the error
then submit the generated core file or stack trace

```

Any ideas?

Do a quick search [here]("http://www.frictionalgames.com/forum/forumdisplay.php?fid=32"). Also I noted that it complains about audio in the output. Have you tried 

```
sudo killall pulseaudio
```

If that worked that nuke pulseaudio to oblivion with

```
sudo apt-get purge pulseaudio
```

Posting

```
/home/souch13/.frictionalgames/Penumbra Overture/Episode1/hpl.log
```

Would be nice too.

---

### Post by Dark Aspect on 2009-08-11
> **jamie168168 said:**
> i am a newer, just read and learn more thing.i hope i can be a good new user.

lol

Thread theft

---

