---
title: "Helios screensaver makes my computer freeze/crash - why?!"
date: 2009-02-07
forum: General Help
---

### Post by PsychedelicWonders on 2009-02-07
I am running the default, Ubuntu Helios screensaver.

But after so long, the two monitors I have right now completely freeze up and I have to hard boot my computer down & then up again.

WHY is this doing this?!

This is a brand new, self built computer that is maxed out as far as hardware for performance.

This is quite sad that it cant even run a simple screen saver with out freezing.

So what is the issue?

---

### Post by PsychedelicWonders on 2009-02-09
bump

---

### Post by PsychedelicWonders on 2009-02-10
here is the video card I have...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814121242](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121242)

specs are pretty good arent they?

Why would a simple screen saver, left running on 2 19" monitors crash the computer?

---

### Post by PsychedelicWonders on 2009-02-11
bump

---

### Post by PsychedelicWonders on 2009-02-12
bump

---

### Post by PsychedelicWonders on 2009-02-13
bump

---

### Post by PsychedelicWonders on 2009-02-16
bump

---

### Post by PsychedelicWonders on 2009-02-17
bump

---

### Post by ashwinhgtx on 2009-02-17
Try disabling the screen lock function. It won't ask you for a password when you disrupt the screensaver. 
Doing that fixed it for me.

---

### Post by SamNSane on 2009-02-17
It's possible that the OpenGL support in the driver for that card is really bad.

I'm running a Quadro 1400 Go in a notebook. It's supposedly optimized for OpenGL. Helios will lock the system every time if I try to run it without the restricted drivers. Even with restricted drivers in place, the card seems to have a hard time with Helios.

Desktop special effects are pretty wonky with this card, too.

The cheapie integrated Intel display subsystem on my other laptop may run the OpenGL screensavers slowly and jerkily, but they don't cause the system to lock up. And the desktop effects work better on the cheap subsystem than on the expensive one.

You don't always get what you want...or what you pay for, to paraphrase the song.

You might be able to find some help in the nvnews forums ([http://www.nvnews.net/vbulletin/](http://www.nvnews.net/vbulletin/)). If you post there, do some reading of their posting guidelines. If you post about something like this without providing all of the required info up front they usually won't even bother to respond.

---

### Post by PsychedelicWonders on 2009-02-18
hmm.

so is there any fix for this?

I know the driver I have now is screwed up and I have to install a new set of drivers because I am having multiple problems with Ubuntu and my video card...

So I suppose I should install this new driver (I already have a walk through from another thread)

and then see if the problem persists?

---

