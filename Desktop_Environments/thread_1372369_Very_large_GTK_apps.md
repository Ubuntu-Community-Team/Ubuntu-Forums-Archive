---
title: "Very large GTK apps"
date: 2010-01-04
forum: Desktop Environments
---

### Post by Bill Cosby on 2010-01-04
Hi there!

I installed Ubuntu 9.10 as a console system, basically to get a slim system.
Then I installed the **xorg** packages, and after that **Openbox** (I have tried some more, all with the same problem, so I doubt it is because of the WM).
Now, whatever GTK app I want to use, it starts with a VERY large "zoom", the first items of the menu bar basically take up all of my screen.

Does anyone know about this?

Regards,
Bill

---

### Post by lewisforlife on 2010-01-04
I don't have any information, but I wanted to add that I have been having this problem lately on my laptop.  I am running Jaunty 32 bit, I just a base Ubuntu 9.04 with Gnome, and is a dedicated Linux Box, no Virtual Box or Wubi or anything.

When I open GTK apps, they show up really big for a split second, like they are zoomed in 500%, and then they go to regular size and all is fine.  I hope someone finds a solution.

---

### Post by lavinog on 2010-01-04
What video card do you have?
It might be that it is starting in a low resolution, then switches to a higher resolution afterwards.
You might need to modify your xorg.conf file if you want to lock it in in one resolution.

---

### Post by Bill Cosby on 2010-01-10
> **lavinog said:**
> What video card do you have?
An intel card, I am using the xf86-video-intel drivers.

> **lavinog said:**
> It might be that it is starting in a low resolution, then switches to a higher resolution afterwards.
You might need to modify your xorg.conf file if you want to lock it in in one resolution.
Well, at first I didn't have any xorg.conf file at all -> didn't work.
Now, I made one with "Xorg -configure" and added a Modeline and additionally specified the screen resolution, however -> didn't work :(

Any other suggestions?

---

### Post by lavinog on 2010-01-10
can you post a screen shot, and find out what resolution it is using: system>prefs>display

---

### Post by del_diablo on 2010-01-10
> **lavinog said:**
> can you post a screen shot, and find out what resolution it is using: system>prefs>display

READ THE TOPIC

*goes back to lurking*

Edit: Lets see, whats the output of randr or xrandr in terminal?

---

