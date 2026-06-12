---
title: "Strange Video Annoyances"
date: 2006-06-30
forum: Desktop Environments
---

### Post by kabronkline on 2006-06-30
First and foremost, let me start off by stating that this problem is not affecting any functionality of my system; however, I am compelled to make this post as I have never seen it happen on another machine, including the same machine with   older versions of Ubuntu. Further, there are never any error messages displayed.

I am running Ubuntu 6.06 on a Gateway mx3560 with integrated Intel video. The video runs smooth as day light in comparison to Windows. However, when I start my machine up, just after the very first Ubuntu initialization screen (not the grub or gnome splash screen), my monitor displays multiple images of my initial Gateway boot screen just before POST. This is very odd. After it is displayed my screen goes blank and my Gnome login window appears as normal.

Also, whenever I log out gnome slightly shrinks in the horizontal direction and at the top and bottom of the screen I see purple pixelation. After that my screen goes blank and I see the Gnome login Window. Should I reinstall/upgrade my integrated Intel graphics or is this possibly a hardware issue? If so, could somebody please post instructions, or a link to a good tutorial, I would be most appreciative.

---

### Post by atoponce on 2006-06-30
[quote=kabronkline]First and foremost, let me start off by stating that this problem is not affecting any functionality of my system; however, I am compelled to make this post as I have never seen it happen on another machine, including the same machine with   older versions of Ubuntu. Further, there are never any error messages displayed.

I am running Ubuntu 6.06 on a Gateway mx3560 with integrated Intel video. The video runs smooth as day light in comparison to Windows. However, when I start my machine up, just after the very first Ubuntu initialization screen (not the grub or gnome splash screen), my monitor displays multiple images of my initial Gateway boot screen just before POST. This is very odd.

Also, whenever I log out gnome slightly shrinks in the horizontal direction and at the top and bottom of the screen I see purple pixelation. Should I reinstall/upgrade my integrated Intel graphics or is this some other issue? If so, could somebody please post instructions, or a link to a good tutorial, I would be most appreciative.[/quote]

Might be hardware, might be software.  For software, there are a couple of things you can do.  First, do you know what video driver you are running?  It might not be very "friendly" to your card.  Second, you might want to try a different driver.  You can achieve this through:

```
sudo dpkg-reconfigure xserver-xorg
```

See what driver it selects by default, and try the vesa driver if the selected gives you any troubles.  Resart your X, and see what happens.

About the Gateway screen just before POST, your X driver has not been called at the point, so that leads me to believe that it may be a hardware problem.  The horizontal shrinking leads me to believe you just need a better or different driver to handle X.

Just curious, but what are the specs for your system?

---

### Post by kabronkline on 2006-06-30
I am using the i810 driver. I executed the above command and went through the wizard and it appears to have resolved my issues! A big **WOOT** goes out to you!

---

