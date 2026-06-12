---
title: "DVD Player Locks Up"
date: 2006-03-10
forum: Desktop Environments
---

### Post by russ1960 on 2006-03-10
I get the following error when trying to play a DVD movie in Totem:

*The audio device is busy. Is another application using it?*

The DVD starts - gets thru all the previews and the FBI warnings then just as it is about to start the above error pops up.  I have no other applications that I know of running.

Let me know

Thanks

Russ

---

### Post by akiro.yamamoto on 2006-03-11
See this link for info ;)
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

Welcome to Ubuntu Linux....

---

### Post by russ1960 on 2006-03-11
Thanks for the tip - I have downloaded everything on that page - tried Xine and got the same result - there must be some setting wrong on my sound card causing this - no matter which media player I use this happens.

I used Automatix and downloaded supposedly everything I needed.

Let me know

Thanks

Russ

---

### Post by Svictor on 2006-03-11
Not a solution but two suggestions : 

1) Before launching totem, try ```
lsof /dev/dsp
``` and ```
lsof /dev/snd/*
```. It reports whatever program uses the /dev/dsp /dev/snd/* devices. Kill whatever you see ("esd" for ex., it loves to hang onto the sound card and block it all for itself ; so that would be "killall -9 esd").

2) Use ogle instead of totem (or xine) : it is specialy designed for dvd playing and has a nice menu support.

---

### Post by russ1960 on 2006-03-11
Where do I get Ogle at?  I'm a newbie that is just fed up with windows xp.

Thanks

Russ

---

### Post by russ1960 on 2006-03-11
Ok I got Ogle installed and now the DVD plays but no sound - Sound works in other applications and in all other media apps I still get the busy error but sound.

How do I fix this?

Thanks

Russ

---

### Post by Svictor on 2006-03-11
It's in the repositories. Look for it through synaptic. or ```
sudo apt-get install ogle
``` I think there was another package named ogle-gui, that you needed to install in order to get the gui (graphical interface). Once you have what you need, run```
ogle
```

Edit : 
Sorry, didn't see your last post

---

### Post by Svictor on 2006-03-11
See my other post (about lsof).

---

### Post by russ1960 on 2006-03-11
How do I got sound?

---

### Post by brainwrinkle on 2006-03-11
I had this same problem but Ogle works for me.  I made sure to kill all of the esd processes first, though.

---

