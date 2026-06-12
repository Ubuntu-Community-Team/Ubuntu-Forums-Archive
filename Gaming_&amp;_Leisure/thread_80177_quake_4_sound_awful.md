---
title: "quake 4 sound awful"
date: 2005-10-21
forum: Gaming &amp; Leisure
---

### Post by jamesford on 2005-10-21
i got really bad sound with quake 4, sounds like a scratched record and it makes the graphics worse too. i mean in scenes with no or little sound the graphics are smoooth but the more scratchy sound the worse graphics, almost unplayable. ive tried the quake4 +set s_device oss suggestion but it makes no change...

any other suggestions ?

---

### Post by arcanistherogue on 2005-10-21
:D

I had this exact same error when I installed yesterday.  Just switch to oss, it fixes most things for  me with the Doom 3 engine.

run the switch "+set s_driver oss" after quake4 when you boot it from command lline, and then it will use OSS every time.

I actually like oss for games, people say its bad but it is much easier to configure IMO.

---

### Post by jamesford on 2005-10-21
if you read my post ud see that i did try the oss engine

---

### Post by arcanistherogue on 2005-10-21
crap.  Sorry, i didn't read that at all, i just noticed the scratchy part.  My mistake.  :(

There is a guide on quake 4 and doom 3 on linux made by id software, but i dont have a direct link to it.  I found it if you go to [www.planetquake.com](www.planetquake.com) and hit quake 4, then look for the news post about the linux client, there is a link to the quake 4 one which has a link to the doom 3 one. 

Sorry again for acting so fast, i have a bad habit of doing that :(

---

### Post by jamesford on 2005-10-21
thats allright. actually i noticed now in terminal that it looks like its using alsa despite the oss command:

snd_pcm_writei short write: 1881 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 1881 out of 2048
snd_pcm_writei short write: 1881 out of 2048
idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 1881 out of 2048
snd_pcm_writei short write: 1881 out of 2048

---

### Post by arcanistherogue on 2005-10-21
Well... I run all of my games in the failsafe terminal, they seem to run slower and have alot more errors while KDE is running. 

That might work, try it.

---

### Post by jamesford on 2005-10-21
actually this time i misread you. you said 'quake4 +set s_driver oss' i said 'quake4 +set s_device oss'

with 'driver' instead of 'device' it works beautifully :D

my fault entirely, your fix worked

---

### Post by arcanistherogue on 2005-10-21
Oh, my pleasure to help :KS

---

### Post by XVampireX on 2006-07-08
Sorry for resurrecting such an old topic, but I'm trying to run doom 3 and I'm having the same problem, I used the fix here and it worked, but the problem is: Why not ALSA? Can we fix ALSA to work well?

---

### Post by hotani on 2006-07-29
I'm having the same problem, just trying to get Doom3 and/or Quake4 demos to work. 

Setting to oss does nothing. I still get these errors:
```

idAudioHardwareOSS::Write: 4096 frames overflowed and dropped

```

with alsa it's the same error. "...4096 frames overflowed and dropped"

The game has NO sound at all. At first it had garbled sound and voices, but now after "fixing" it, I have no sound.

I have also tried the fixes on [this page](http://zerowing.idsoftware.com/linux/doom/#head-8c36163f1dfc3a253ef72c0f821b0b0dd2fc17b1) but still no change.

EDIT: sound fixed!
I was pointing to the wrong device, so switched it back to "default" then ran quake4 with oss like so:
```

shell> quake4-demo +set s_driver oss

```
which did the trick.

---

### Post by geoff123 on 2006-10-28
Note that this also works with doom3 on edgy
doom3 +set s_driver oss

i have the alsa-oss package installed, but i'm not sure if it's needed
i had lots of problems with doom3 sound on dapper and resolved them by installing the non-free version of OSS from [www.opensound.com](www.opensound.com).  These worked great for doom3 and several other progams such as RealPlayer, plus had a very nice mixer.  However, some programs now use ALSA exlusively such as Adobe's flash 9 beta.  Anyway i finished doom and tried to go back to ALSA - the OSS uninstall did not go well and and I ended up doing a fresh install of edgy and i'm sticking with ALSA for now if possible. so far so good.

---

### Post by boltronics on 2006-12-16
Thanks for the post - I installed alsa-oss and ran
```
aoss doom3 +set s_driver oss
```
Finally, I had sound in Doom 3 that wasn't a scratched record. I just wished that it was in 5.1. I might give the 4Front OSS drivers a chance.

---

### Post by MetalMusicAddict on 2006-12-16
What probably happened is that you ran it as root right after you installed. There was probably a .quake4 folder created in the root dir. Delete that and rerun as a normal user with **quake4** and you should be cool. This has been the case alot on many linux forums.

---

### Post by neo2k on 2007-04-28
Here's what ended up working for me (using my usb-headset on feisty), using the aoss wrapper:
file: /usr/local/quake4-demo
```
#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd "/usr/local/games/quake4-demo"
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
aoss ./quake4.x86 +set s_driver oss $*
exit $?
```

Make sure you install the alsa-oss wrapper for this to work:
```
sudo apt-get install alsa-oss
```

haven't tried this on the retail version, but should be the same.

---

