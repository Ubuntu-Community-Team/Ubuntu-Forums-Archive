---
title: "Enemy Territory: can only start with sudo"
date: 2006-07-19
forum: Gaming &amp; Leisure
---

### Post by Onyros on 2006-07-19
Hi there, guys.

I'm having a few problems with Enemy Territory. I installed it tonight, and whenever I try to play it, I get gfx card rubbish UNLESS I start it with sudo.

And also, I'm getting no sound whatsoever (started as superuser or not).

I have the correct ATi drivers (and the game runs perfectly when started as su, good resolution, nice speed and all, just no sound as well).

Can anyone help me here? Any idea what's happening there?

---

### Post by goobers on 2006-07-19
Did you install it as sudo? Where has it installed to?

---

### Post by Onyros on 2006-07-19
Nope, I didn't install it as su. I actually solved that problem, by changing a few permissions (enabled execute on all ET files, which was disabled) and it's working fine and dandy now.

I chose to install it to a local home folder I have just for games.

Now, regarding the sound... I read elsewhere running as su enabled sound for some people. Not only it isn't safe running something like that as su, but it didn't enable sound for me...

What shall I be looking at?

Thanks in advance, guys (that was an ultra-quick reply, btw, thanks, mate).

---

### Post by goobers on 2006-07-19
Is there a log of the ET console that you can post up?

Edit::

If it doesn't automatically generate a log, i think you can output the console to a file with this console command:

/condump "filename.txt"

---

### Post by Onyros on 2006-07-19
------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp
------------------------------------

It think this is the "interesting" part. Any ideas? I'm pretty much clueless regarding this :P (proudly a noob)

I have no sound problems with other games (Tremulous, for instance), I play music in amaroK, VOIP is working flawlessly... Only thing I'm having problems in terms of sound is ET.

---

### Post by goobers on 2006-07-19
I know this sounds stupid, but have you got anything open that uses the sound card (i.e. is amarok still open in the system tray?)

Its always better to try the obvious things first :p

---

### Post by goobers on 2006-07-19
another thing you could try is running it through artsdsp... i found some posts and that seemed to solve it for some people...

```

artsdsp -m et

```

---

### Post by Onyros on 2006-07-19
It wasn't stupid at all, but it wasn't the case, any way. I'm using ALSA, also heard it may be less problematic with OSS. (edit: it's the other way around, actually, more problematic with OSS)

I'll try it through arts as you suggested, thanks, mate ;)

edit: In the end, "killall esd" just worked ;)

---

