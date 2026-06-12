---
title: "Mplayer jumpy"
date: 2005-12-26
forum: General Help
---

### Post by docmanny on 2005-12-26
I installed Mplayer with the automatix script, but videos are playing very choppy. the sound is too. 

On the same machine, I can play the same videos with Mplayer with another distro (vector) without this problem.

How do I troubleshoot this?

---

### Post by Perfect Storm on 2005-12-26
If it's when playing DVDs you properly needs to enable DMA on your DVD-driver(s)

---

### Post by docmanny on 2005-12-26
Its avi and mpg files. Doesn't seem to matter what th e format is. Some of the files play ok on Totem, some don't.

---

### Post by irv on 2005-12-26
In your setting in the Mplayer, try different sound drivers until you get one to work without the jumpies. I had the same problem, and this fixed my problem.

---

### Post by docmanny on 2005-12-26
That did the trick! ESD rather than ALSA.
Thanks!

---

### Post by Odinist on 2005-12-26
This doesn't really apply to your problem, since you said you fixed it, but I wanted to add (in case anyone else has experienced this) that MPlayer was being choppy for me when playing embedded videos on website. Disabling IPv6 in Firefox for some reason cleared that up for me.

---

