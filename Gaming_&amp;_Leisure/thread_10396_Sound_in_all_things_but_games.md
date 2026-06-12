---
title: "Sound in all things but games"
date: 2005-01-07
forum: Gaming &amp; Leisure
---

### Post by pmshoop on 2005-01-07
Hey there,

I know I read something about this but can't find it...

I've got sound in all applications but the games I install.  In order to get sound on them I need to be in root.  If I start the games from  a root terminal I get sound.  

Any ideas what I'm missing here?

---

### Post by fng on 2005-01-07
maybe your user isnt in the audio group?
```
fng@butters:~/series/family guy (complete) $ cat /etc/group | grep audio
audio:x:29:fng
fng@butters:~/series/family guy (complete) $
``` 
If your user isnt printed, add it by editing the /etc/group file

---

### Post by Yekrats on 2005-01-07
[QUOTE=fng]maybe your user isnt in the ausio group?
```
fng@butters:~/series/family guy (complete) $ cat /etc/group | grep audio
audio:x:29:fng
fng@butters:~/series/family guy (complete) $
``` 
If your user isnt printed, add it by editing the /etc/group file[/QUOTE]

Hmmm... I'm getting the same problem. I hear the inital drum beats and WAV files when logging in, and some sounds work (like in "ktuberling"). But I do not get sound in more complex games like Frozen Bubble or Neverball.

My user is in the audio group.  Any further ideas?
Thanks,
Scott S.

PS: As a bit of a follow-up: In some investigation, I've found that only .WAV files will work, but others don't seem to. Does that give anybody a hint of how to help?  :D

---

### Post by fng on 2005-01-07
I had that problem 2.
My soundcard didnt support hardware mixing.
This means you can only play 1 sound at the same time.
If you start frozen-bubble, a gnome sound is played, and therefore frozenbubble can,t play its sound.

Solutions
---------
1. Try starting frozen bubble from the console
2. Configure your soundcard for software mixing -> search for dmix
3. Buy a new soundcard that supports hardware mixing, like i did.

---

### Post by Dylanby on 2005-01-07
For Frozen Bubble I need to kill **esd** to get sound.

Do a search on esd & you'll see there are issues with it & other apps sharing resources (i.e., if your soundcard doesn't support hardware mixing).

---

### Post by Roger Dunder on 2005-01-14
i had the same problem, i had sound in all aplications but the games ( ET, Q3)
and in the consol i had this. 

sound initializition: /dev/dsp input/output error, could not mmap /dev/dsp



I did this!!!!

in the game consol : i just wrote

snddevice "/dev/adsp"

and after i have restarted the game i had sound.

---

### Post by doni on 2005-02-14
hmm i did the same, but i still don't have sound in et.... :(

any other ideas?

---

### Post by Dylanby on 2005-02-14
> hmm i did the same, but i still don't have sound in et....

Are you sure that ET/Q3 are set to use OSS & not ALSA?

For Doom 3 (another id game) I had to edit /.doom3/base/DoomConfig.cfg

---

### Post by piedamaro on 2005-02-14
Use software mixing, there is an howto about it.

---

### Post by wondering_jew on 2005-04-18
Heres what worked for me, found it in this thread  [http://www.ubuntuforums.org/showthread.php?t=25548](http://www.ubuntuforums.org/showthread.php?t=25548)

The long and short of it is opening a terminal and typing

"sudo apt-get install libsdl1.2debian-all"


and since then my sound in both games and applications have worked :)

---

### Post by rolfp on 2006-08-27
> wondering_jew:    	
Heres what worked for me, found it in this thread [http://www.ubuntuforums.org/showthread.php?t=25548](http://www.ubuntuforums.org/showthread.php?t=25548)

The long and short of it is opening a terminal and typing

"sudo apt-get install libsdl1.2debian-all"


and since then my sound in both games and applications have worked 
Thanks for that!  Worked for me in Debian Etch wrt Frozen Bubble when I found your post via Google.

---

