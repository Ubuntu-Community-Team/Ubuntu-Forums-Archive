---
title: "Menus look strange"
date: 2012-11-28
forum: Desktop Environments
---

### Post by Imasami on 2012-11-28
I've been trying Ubuntu again recently after going back to Windows on this same computer for a while. I've been using Unity mostly, and I have a problem where certain gtk themes cause the menus to not display correctly.

I am running Ubuntu on a Lenovo y470. It is the one with the nvidia m550 issue, fixed by [this Bumblebee hack]("https://github.com/Bumblebee-Project/bbswitch/issues/2#issuecomment-3797568"). The hack seems to have worked correctly, but I'm unsure whether it could be part of the problem.

Adwaita is the only theme that seems to display correctly, except for in the Ubuntu software center, where the text is white with a shadow on top of a white background.

I believe that there are more issues than this in my system, but I have no idea where to start investigating or fixing. 

I will try to provide any further information.

Thanks

---

### Post by zombifier25 on 2012-11-29
What is the Ubuntu version, and what themes are you using? Those themes might not be compatible with the latest GNOME.

---

### Post by Imasami on 2012-11-29
I am running 12.10, and the theme shown in the badmenu picture is on of the ones that came standard with Ubuntu(Radience maybe, I'm at work and cannot check).

---

### Post by zombifier25 on 2012-12-01
Interesting. Try logging in the guest session and see if the problem persists. If it doesn't happen in the guest session, try reseting Unity.
[http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

---

### Post by Imasami on 2012-12-02
Strange thing happened when I booted up Ubuntu this morning. I went into Unity, and there was no top bar or side panel. Just the Desktop background was showing. I logged out and in, and restarted, and in both cases it was the same.

I reset compiz and unity like it was described in the site you linked from the text terminal and it seemed to have fixed this newer problem; the panels are both back. Menus still look strange, though.

Some additional information, I tried Gnome and i3 as well, and both had the same menu problem. Is there some package that all three use that could be badly configured? Or could it be a driver problem?

Thanks

---

### Post by zombifier25 on 2012-12-04
Try checking if there's a folder names .themes in your home folder, if so, delete it.
Just to be extra sure, install myunity or ubuntu-tweak, and check the name of the theme that's being used.

If those still doesn't work, then it's possible it's a graphic problem, which is unfortunately something out of my knowledge.

---

### Post by baddnady23 on 2012-12-09
Same exact issue so I am bumping this as I have not found a fix yet...

---

