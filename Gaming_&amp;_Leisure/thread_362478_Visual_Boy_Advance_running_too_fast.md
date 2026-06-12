---
title: "Visual Boy Advance running too fast"
date: 2007-02-15
forum: Gaming &amp; Leisure
---

### Post by Wertigon on 2007-02-15
Hi all!

I'm having a problem with VBA - it's running at twice the speed it's supposed to. Tried Googling around for this problem since I know some friends've had similar problems, but I couldn't find much of an answer anywhere.

Anyhow, anyone know why my VBA runs at 2x the speed, and how to fix it? It ran fine mostly before I upgraded to Edgy. Right now I'm running Edgy Eft on a Centrino 1.8 GHz w/512 MB RAM and Intel 915 chipset. It also appears to be a problem with Debian.

---

### Post by feest on 2007-02-15
try this: 
```
sudo etc/init.d/powernowd stop
```

it should disable a kind of cool 'n quiet technique that fixes the problem for cedega to start it again use
```
sudo etc/init.d/powernowd start
```

---

### Post by Wertigon on 2007-02-15
That did not solve it,  the vba is still running on 200% speed. Thanks for the suggestion though. Any other takers? :neutral:

---

### Post by zerosystem on 2007-02-15
Are you running it on wine/cedega or did you get it from synaptic?

---

### Post by Wertigon on 2007-02-16
Sorry, guess I should have clarified that one. It's the native version (i.e. got it from the repositories). Why emulate something that you can get in native mode? :)

---

### Post by ryuko2002 on 2007-02-16
I had tried VBA both in windows xp and ubuntu. In windows XP you have a throttle option to control speed but it doesnt work in linux. I'm not in front of my computer right now but I think that I opened the cfg file that its created in your home directory and change set the throttle to 50 or 60 instead of 0 (auto).

---

### Post by Wertigon on 2007-02-16
Yes, that did the trick, mostly. Now if I could just fix the garbled sound that appears, that'd be super schweet, but atleast now I can play the darn thing. Thanks! :)

---

### Post by rolando2424 on 2007-02-16
> **Wertigon said:**
> Yes, that did the trick, mostly. Now if I could just fix the garbled sound that appears, that'd be super schweet, but atleast now I can play the darn thing. Thanks! :)

Yeah, the sound is really crappy :(

---

### Post by conjur3r on 2007-02-16
The method I got the speed back to somewhere around 100% was to change the sound quality to the highest available.  I think it was 44 or 48khz.

---

### Post by arbrandes on 2007-03-22
An alternative is to use [Mednafen]("http://mednafen.sourceforge.net").  It emulates GBA well, among other systems (NES, etc.).  I found it to be more flexible in terms of screen resolution than VisualBoyAdvance, and it has no throttle or sound problems.

---

