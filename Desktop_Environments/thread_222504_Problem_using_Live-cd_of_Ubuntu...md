---
title: "Problem using Live-cd of Ubuntu.."
date: 2006-07-25
forum: Desktop Environments
---

### Post by Frappe051 on 2006-07-25
Hey..

The problem I have is that my computer only has 128mb RAM, and whenever I try to run the Desktop Install CD, it gets to the screens where it's loading everything, then goes back to the plain orange background, and about a minute later it freezes.

Now, I've already tried installing Ubuntu on that same HDD using my other computer that has 2GB of RAM, and It installed fine but when I transported it back to the other computer, the X window server wouldn't start becasue xorg.conf was looking for the other computer settings.

Will I have to buy more RAM, or is it possible just to edit some of the options in xorg.conf to make it work?

Thanks!
-Frappe051

---

### Post by 3rdalbum on 2006-07-25
I thought Ubuntu Dapper required more than 128 megs. Maybe you should try Breezy, or Xubuntu Dapper.

---

### Post by Frappe051 on 2006-07-25
Edit: I changed some options throughout xorg.conf and apt-getted the nvidia-glx drivers, and was able to load GDM and X server perfectly.

I think that it only needs 192MB for loading a LiveCD into RAM, if it's installed onto the HDD, it requires very little RAM.

Regardless, an upgrade to 512MB is something I will be investing in.

---

### Post by lamego on 2006-07-25
128mb is not sufficiente for the LiveCD. You will need to install it from the Alternate CD (text mode).
You should use Xubuntu instead for such a low memory system. The Ubuntu default window manager (GNOME) does use a lot of memory.

---

