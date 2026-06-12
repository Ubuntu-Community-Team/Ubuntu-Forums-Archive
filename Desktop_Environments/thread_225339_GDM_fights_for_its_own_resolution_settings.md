---
title: "GDM fights for its own resolution settings"
date: 2006-07-29
forum: Desktop Environments
---

### Post by maruchan on 2006-07-29
I have this problem with GDM (the login screen). It likes to stay at 1600x1200, when I want it to be at 1280x1024 like my GNOME desktop. I finally got the screen to only show 1280x1024 pixels at once, (somehow I achieved this using Kubuntu to change the screen res) with the result that you cannot see the entire GDM login screen. If you move your mouse to the sides of the screen, the entire image scrolls so you can see the rest of the login screen.

In other words, if you want to use the "sessions" menu, you can't see it initially. You have to move your mouse to the bottom left and wait for the sessions menu to scroll into the viewable area of the screen.

So it's like GDM is trapped at 1600x1200, even when it's in a 1280x1024 container.

Any ideas on how to fix this? Where are the resolution settings kept for GDM? Thanks for any help.

---

### Post by Fass on 2006-07-29
What resolutions are set in your xorg.conf? Removing the 1600X1200 mode in the "Screen" section should do the trick.

---

### Post by maruchan on 2006-07-29
Thanks for mentioning xorg.conf - I was hesitant to remove the option for 1600x1200 altogether, but I noticed this out of the corner of my eye:

```
  SubSection "Display"
    depth 24
    virtual 2048 1536
    modes (long list here - removed)
  EndSubSection
```

I have no idea what "virtual" is for, so I guessed it's the size of a virtual desktop. But so huge! Wow. I changed it to 1280 1024, restarted X, and *poof*, no more problems! :)

---

### Post by Leonivek on 2006-08-13
OMG!  Thank you so much for this! .oO(I learn something every day!)  This was such an annoyance for me for the past month.  I had this issue after I installed KDE in Ubuntu.

Thank you!

---

### Post by Ay Deverrick on 2006-08-13
I have this same problem, except I want to disply GDM in 1600x1200 but it's showing up in 2048x1536.  I checked my xorg.conf file and it lists only 1600x1200 and the modes below it, so deleting resolutions above 1600x1200 isn't an option.

---

### Post by Midway on 2006-08-13
A big thank you from me too!  I just came on the forum looking for the same thing.  I could barely make out what I typed on the login screen (19" with the 1600x1200 login screen, run desktop on 1280x1024).  I did not have the "virtual" setting but I did delete all references to "1600x1200" in xorg.conf and rebooted and it worked! :D

---

### Post by Leonivek on 2006-08-13
> **Ay Deverrick said:**
> I have this same problem, except I want to disply GDM in 1600x1200 but it's showing up in 2048x1536.  I checked my xorg.conf file and it lists only 1600x1200 and the modes below it, so deleting resolutions above 1600x1200 isn't an option.
Can you post your /etc/X11/xorg.conf file?

---

### Post by Joyeuse on 2006-09-16
I'm having the same problem.  The login screen is larger than my monitor, so that it scrolls around like a virtual screen, but when I log in to Ubuntu, my resolution settings work fine.  this is frustrating for me because when I edit xorg.conf with the "virtual x y" field, it applies that to Ubuntu as well (where my resolution settings are already as I want them).

---

### Post by zephyrus54 on 2007-01-05
I'm assuming there's no easy way to switch back and forth between gdm resolutions?  I'm asking this because the gdm screen shows up fine on my laptop, but the resolution is too high when it's hooked up to an external lcd.  Hopefully in future ubuntu versions, they'll be able to link the gdm and desktop resolution settings so that they can be easily adjusted together.

---

