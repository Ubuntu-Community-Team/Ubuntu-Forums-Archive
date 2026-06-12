---
title: "Taskbar gone; screen out of whack"
date: 2014-11-04
forum: Desktop Environments
---

### Post by redking2 on 2014-11-04
Hey everyone,

I've been using the newest version of Lubuntu on my netbook for a couple of weeks now and was really happy with it. Yesterday, however, something changed:

Upon booting up, I noticed that that the lubuntu logo on the loading screen was lower than normal, now appearing in the lower third of the screen instead of the center. That in itself wouldn't bother me, but the problem persisted as the system booted up -- my taskbar is completely gone -- I assume out of reach, basically -- and my wallpaper seems to extend downwards beyond the screen. I hope I'm making sense here. Basically, it all looks like my screen was suddenly missing its lower third or quarter. I have no idea what could've caused this or how to undo it. 

My first idea was that I might've accidentally switched the screen resolution, but I then proceeded to cycle through all options to no avail. If I choose a low resolution, the picture goes big and grainy, but the task bar remains gone. I also checked for updates, wondering if maybe some driver needed an update. Alas, the system seems to be completely up to date. As an Ubuntu newb, I'm at a loss now.

Any help would be much appreciated!

---

### Post by JohnnyComeL8ly on 2014-11-05
I think that as you boot, if you press Shift, you will get a grub menu, from there choose "Advanced options for Ubuntu."  In the menu that follows, you choose the closest to the top entry... something like "ubuntu-generic-kernel(recovery mode)." When you choose that one you should see a white square-of-a-menu on top of a blue background, like [this]("http://cdn5.howtogeek.com/wp-content/uploads/2014/09/ubuntu-recovery-menu.png"), choose "resume" first, if that doesn't fix your problems, then go through the whole loop again and choose failsafex (if it exists for Lubuntu)... I have never tried that option, but it might be a way to fix it.:neutral:
(I don't remember it being there, and part of it might be that I use Lubuntu...:popcorn:)

I pulled the picture link from [http://www.howtogeek.com/196740/how-to-fix-an-ubuntu-system-when-it-wont-boot/](http://www.howtogeek.com/196740/how-to-fix-an-ubuntu-system-when-it-wont-boot/)
It might help to look at it all...  
I do have a [SIZE=4][FONT=comic sans ms]Q[/FONT][/SIZE] for [FONT=comic sans ms][SIZE=4]U[/SIZE][/FONT]: did you recently install any kernel updates, or similar types of things?

---

### Post by Bucky Ball on 2014-11-05
When you say you cycled through the various resolutions, where did you do this? How did you get to the Display settings with no taskbar? I'm presuming by right clicking on the desktop>Applications>Settings>Display? 

When you boot the recovery mode you could also try 'Fix broken packages' option. Never know.

---

