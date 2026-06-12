---
title: "Making desktop larger than screen"
date: 2009-04-01
forum: General Help
---

### Post by Ububurns on 2009-04-01
I would like to make my desktop larger than my actual screen, so that when I move my mouse to the edge the screen scrolls.

I'm having trouble trying to work out how to do this!  Any ideas?

---

### Post by ryanhaigh on 2009-04-02
The feature you are trying to enable is associated with virtual resolution settings for X/xorg.conf. I haven't done this myself so I can't offer any more advice but hopefully knowing what you are actually looking for will get you a little further. [Google brings up a few results that might be useful to you.]("http://www.google.com/search?q=ubuntu+virtual+resolution+scroll")

---

### Post by mocoloco on 2009-04-02
If you're using desktop effects (compiz) then there's a zoom function when you hold superkey (the winkey, which I like to call tuxkey :) ) and scroll your mouse wheel.

---

### Post by ryanhaigh on 2009-04-02
The OP is trying to get a higher resolution than the display device natively supports. While the zoom function of compiz is very useful its essentially the opposite of what they are trying to achieve.

---

### Post by Ububurns on 2009-04-02
No luck so far.  I have specified a larger virtual desktop in xorg.conf, but it doesn't seem to be the solution.

(I'm trying to make a 2048 * 768 virtual desktop, and then will VNC the half of the screen that doesn't actually exist to another computer.)

Interestingly increasing virtual screen size slows down my framerate quite substantially.  It doesn't however achieve what I would like - to have a desktop larger than my screen size.

Funny enough most of the threads I find on this subject involve people asking how to turn the scrolling of their oversized desktop off...

Does anyone else have any ideas?

---

### Post by ryanhaigh on 2009-04-02
[http://forum.eeeuser.com/viewtopic.php?id=8242&p=2](http://forum.eeeuser.com/viewtopic.php?id=8242&p=2)

---

