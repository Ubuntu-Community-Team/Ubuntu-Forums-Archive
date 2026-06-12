---
title: "Characters size so big that the GUI is unusable"
date: 2015-06-20
forum: Desktop Environments
---

### Post by parl8256 on 2015-06-20
I'm trying to fix an Ubuntu 14.04 computer for someone and his Unity desktop has characters so large that it's unusable. I've gone into Settings - Display to look at the resolution, but it's already at the highest value (1920 x 1080) and I can't see below the resolution drop-down on the Display settings panel. I've looked at Settings - Appearance and I can't see enough of it to do anything useful.

Even the characters in the Terminal are huge, although I can probably see everything needed, as it wraps.

Is there a text method for resetting the desktop font size / screen resolution? It would appear that the screen resolution is OK, but the default text size may be what is messing it up.

On reflection, he may well have increased the font size himself, as he needs glasses but resists using them. Not that he'll admit doing that or even remember how he did it.

He has a huge number of family photos, many of which are irreplaceable. I'll make CD or DVD copies once the GUI is back to normal. Then there won't be the problem of losing things if a re-format is needed.

BTW, I am personally running Ubuntu 12.04 w/ Unity so I can look there for examples of what I'll try on his computer.

And IIRC, there are some "dot" files in the home directory which can be deleted to perform a reset since they are re-created, but I don't recall them.

Thanks for your help. I did look for this problem here, but found nothing. If it has been solved before, let me know what the title is and I'll go there.

Ross

---

### Post by deadflowr on 2015-06-20
It sounds like a strong possibility that they user increased the text-scaling-factor.
This can be set in the display settings page via a slider bar.
Normal size should be 1.0
From the command line use gsettings to find out what it is currently set at
```
gsettings get org.gnome.desktop.interface text-scaling-factor
```
You can then reset it to the default changing get to reset like so
```
gsettings reset org.gnome.desktop.interface text-scaling-factor
```
or change the size to something more manageable if need be
```
gsettings set org.gnome.desktop.interface text-scaling-factor X.X
```
changing X.x to any number you want, perhaps try something like 0.9 to start.
I would definitely try reset first though, as it is completely possible that the user simply skimmed the slider in the display settings page.

That's my initial 2 cents at least...

---

### Post by parl8256 on 2015-06-23
Thanks. That worked. It made the characters in the Terminal the right size and when I rebooted, the Unity DE was OK too. I was then able to use Settings Appearance and Settings Monitors to adjust things as big as I dared. I'll return the computer and advise him not to make the characters any bigger. (1.75 of normal is as big as will work well.)

The shop to which he took it for data recovery said it had a virus and would need to be re-installed. (sigh)

Ross

---

