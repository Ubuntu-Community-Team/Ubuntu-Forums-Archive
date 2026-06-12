---
title: "Gnome desktop.. gone ?"
date: 2005-12-14
forum: General Help
---

### Post by Manojo on 2005-12-14
Hi,

I was as usual up and booting Ubuntu(GNOME desktop), and as soon as I entered my username and password, I arrive on a screen with only my background image, and NOTHING else. (no startup bar, no icons, nothing).
So I try then to boot in GNOME failsafe mode, and still, nothing.

So I go to boot in recovery mode, and I see that my files are luckily not deleted.

What do I do ?

Thanks,
Manojo

---

### Post by Manojo on 2005-12-15
Hi again..
please do help me ... What can I do ? Can I save it by using the install CD ??

Thanks,
Manojo

---

### Post by AlexMR on 2005-12-15
Hello Manojo,

I used to have the same problem when I had xcompmgr installed and put into the session start. Just in case you did the same remove xcompmgr with sudo apt-get remove xcompmgr.

You might also try sudo dpkg-reconfigure xserver-xorg in order to fix your X-server settings.

Greets,
Alex.

---

### Post by Manojo on 2005-12-15
Hi AlexMR,

thanks for your response..

I tried to remove xcompmgr, but it wasn't even installed, so nothing got removed.

Otherwise, I tried to reconfigure everything using dpkg(might have made a few mistakes, but I think it was correct enough), but still, nothing at all....

I ran the Live CD in Rescue mode, but the CD couldn't recognise dpkg..

What do I do ?
thanks,
Manojo

---

