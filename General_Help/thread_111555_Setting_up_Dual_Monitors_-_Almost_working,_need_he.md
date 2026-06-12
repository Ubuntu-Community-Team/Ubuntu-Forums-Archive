---
title: "Setting up Dual Monitors - Almost working, need help!"
date: 2006-01-02
forum: General Help
---

### Post by TDonaghe on 2006-01-02
I have 2 monitors hooked up to my Ubuntu box.  I have a 19" normal aspect LCD and a 19" Widescreen (16x10) LCD.  I have an ATI Radeon 9800XT to which both monitors are installed.  I followed the instructions [here]("http://www.ubuntuforums.org/showthread.php?t=24557") and got the ATI drivers up and running.  Then, I used fglrxconfig and went through a TON of options to set up dual monitors.  

I have both monitors working now, BUT, I'd really like to be able to set the resolution on the Widescreen monitor more precisely.  I don't see any kind of options that will let me do that.  Right now I have my screens set up to each have their own KDE sessions and the normal aspect monitor looks great, but the Widescreen one looks like crap because it's spread 1280x1024 over the whole screen.  The text is almost illegible.

Can anyone help?  I've gotten so close, yet it's still not really workable.  So far, this is one of the few places where Windows actually worked BETTER for setting something up.  It was totally painless to get the dual monitors working in Windows.

Any help is greatly appreciated!!

UPDATE:  I just right-clikced on the Widescreen's desktop and got a list of screen sizes to choose from, but the largest one is 1280x1024.  Now, I guess I need to know how to add in 1440x900, which would be perfect for this monitor.

Thanks!!

---

### Post by lisje on 2006-01-02
the best way is that you would change the resolutions in your xorg.conf.... if you haven't allready...

here's what I did for my dual screen setup:
[http://kleinewereld.be/xorg.conf](http://kleinewereld.be/xorg.conf)

hope it helps a bit...
Greets,
Lisje

---

### Post by TDonaghe on 2006-01-03
Lisje, I'm going to try to set up my widescreen monitor the way you did with your laptop screen, but only have 1440x900 as the resolution.  We'll see how that works.

Thanks for the idea.

---

