---
title: "Choppy sound in Beyond the Red Line"
date: 2007-04-22
forum: Gaming &amp; Leisure
---

### Post by rapha on 2007-04-22
Hi all,

I'm trying to play Beyond the Red Line ([www.game-warden.com/bsg/](www.game-warden.com/bsg/)) but the sound is unplayably choppy. I tried alsa, native, esd, sdl, oss in my .openalrc and even started the game with "aoss" or "esddsp" prepended, which mostly only makes it worse. Setting ```
(define speaker-num 2)
``` appears to have made it a tiny bit better. The fun thing is, all other games work just fine (including DOOM III for which switching to OSS has done the job or Chromium which is an OpenAL game as well).

Any ideas what this could be cause by?

Cheers,
Raphael

---

### Post by mbradlcu on 2007-05-18
this is a fix for that problem but with q2 based games,, you'll need to run them sudo,, hope it helps!
replace quake2 with what ever executable you're running

echo 'quake2 0 0 direct' > /proc/asound/card0/pcm0p/oss
fuser -vk /dev/dsp

---

### Post by DarkDead on 2007-10-29
Hi everyone. 
I've just the same problem.
Trying to follow the mbradlcu's advice I got:
```
david@david-desktop:/usr/local/games/btrl$ sudo echo 'btrl_demo 0 0 direct' > /proc/asound/card0/pcm0p/oss
bash: /proc/asound/card0/pcm0p/oss: Permission denied
```
So I opened the root terminal and run the commands there:
```
root@david-desktop:/usr/local/games/btrl# echo 'btrl_demo 0 0 direct' > /proc/asound/card0/pcm0p/oss
root@david-desktop:/usr/local/games/btrl# fuser -vk /dev/dsp
```
I didn't get any error or confirmation and the sound stayed as choppy as before.
Am I doing anything wrong? Anyone has got another idea?

---

### Post by DarkDead on 2007-10-29
Hi again. Searching a bit more I found the solution here: [http://www.game-warden.com/forum/showthread.php?p=61787]("http://www.game-warden.com/forum/showthread.php?p=61787&highlight=post61787").
What you have to do is (assuming that you use ALSA):
Open the terminal and input ```
gedit .openalrc
```
this will create (and open) a file named .openalrc in your home dir.
Now place the following inside it and save
```
(define devices '( alsa native ))
(define speaker-num '( 2 ))
```
Done.

---

### Post by mbradlcu on 2007-10-29
Hi Dark..
thanks for the followup solution!
I just wanted to know that the fix you found replaces the /proc call fix. if so it seem more proper.

thanks!

---

### Post by DarkDead on 2007-11-02
Hi. When using the fix I found you don't need to use the /proc call fix. So, yes, it replaces it.
Cheers.

---

### Post by sammydee on 2007-11-05
Hiya 

I have the same problem, sound is unplayably choppy. I have tried both fixes in this thread and neither worked for me :-(

Any other ideas? I'm running ubuntu gutsy and I have the same problem with sound in chromium as well so it is probably a generic openal problem rather than a problem specific to BTRL.

any ideas? help?

sam

---

### Post by sammydee on 2007-11-05
Well fixed the openal problem by telling it to use oss not alsa as a backend.

The MAJOR choppiness in red line is gone now, but there is still a bit of garbling with the voices. I suspect that this is a different problem altogether and probably the fault of btrl itself because chromium has perfect sound now.

sam

---

### Post by mbradlcu on 2007-11-05
thanks for the update,,
when you say "it" do you mean you changed the setting in the gnome sound control settings or did you change the settings in the individual game config files?
I think I should have done a clean install and not an upgrade because I keep running into issues with old config files... 

thanks!

---

### Post by FG123 on 2007-11-05
> **sammydee said:**
> The MAJOR choppiness in red line is gone now, but there is still a bit of garbling with the voices. I suspect that this is a different problem altogether and probably the fault of btrl itself because chromium has perfect sound now.
If it's what I think you're referring to, the garbling with the voices is intentional. They're suppose to sound like they do in the series, so they're processed to be a little garbled intentionally.

---

### Post by Scottanon on 2007-11-20
I'm having all the same problems.  I tried mbradlcu's solution, no change, and when I edit the .openalrc file I lose sound altogether.  Stumped.  And it's such a good game too.

---

### Post by mbradlcu on 2007-11-20
ok, although the other fix still seems to be needed it wasn't complete to fix my issue on the power-mac I'm using.. Digging through[ this site]("http://www.warsow.net/forum/viewtopic.php?pid=1101521293") with tons of cool info about setting the SDL env var,, seems the following was the money,, just installing  libsdl1.2debian-all
```

sudo apt-get install libsdl1.2debian-all

```

note I still needed to run 
```

sudo "echo 'quake2 0 0 direct' > /proc/asound/card0/pcm0p/oss"
sudo fuser -vk /dev/dsp

```

hope this helps!

---

### Post by chensamurai on 2008-03-26
Yup, that fixed my problem of sound choppiness in Beyond the Red Line!
Thanks for sharing!

---

