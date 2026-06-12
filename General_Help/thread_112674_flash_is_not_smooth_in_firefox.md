---
title: "flash is not smooth in firefox"
date: 2006-01-04
forum: General Help
---

### Post by minimidgy on 2006-01-04
Flash playback in firefox is jerky on my computer. It kinda freezes every once in a while for about a second, and then it works fine again until it freezes once again. Any ideas?

---

### Post by aysiu on 2006-01-04
Are you using the regular mozilla Flash plugin or the non-free plugin?

How did you install Flash? What version of Firefox are you using?

---

### Post by minimidgy on 2006-01-04
I am using firefox version 1.0.7

I installed flash from the macromedia website.

---

### Post by aysiu on 2006-01-04
Try this.
Close Firefox
Follow the directions in the first link of my sig.
Then ```
sudo apt-get update
sudo apt-get install flashplayer-mozilla flashplugin-nonfree
firefox
``` The terminal to paste commands into is in Applications > Accessories > Terminal

---

### Post by minimidgy on 2006-01-05
I tried that and I still have the same problem.

I think it has to do with the sound because it works fine when my computer is on mute.

---

### Post by Mattj on 2006-01-05
is it possible that flash is requesting things of the sound system and then sound system is papping out, causing flash to freeze for a moment?

I have had the same problem. Niggled me for a while but formatted before i got around to looking at it. Wasnt ubuntu either so im guessing its not a problem with anything ubuntu is doing, just firefox/flash/alsa.

Anyone?

---

### Post by minimidgy on 2006-01-06
any ideas?

---

### Post by neoflight on 2006-01-06
try reinstalling using automatix... when iwas using it it even kept my extensions (whatever is compatible) and book marks....automatix can be used to install both 1.0.7 and 1.5 ....apt-get update before u use it...

with all the plugins i mean....

---

