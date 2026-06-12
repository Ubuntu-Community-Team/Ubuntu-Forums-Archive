---
title: "Server X not found"
date: 2009-03-19
forum: General Help
---

### Post by shank286 on 2009-03-19
My version of ubuntu was working fine until i rebooted into windows and when i went back to use ubuntu, it boots up and tells me it can't find server x for graphical display. From there i am just stuck.  Windows updated itself over the internet while i was working in it, if that may have something to do with it. Any help would be much apprciated.

---

### Post by spcwingo on 2009-03-19
Try rebooting into recovery and running x-fix.

---

### Post by shank286 on 2009-03-19
sorry, kind of new to linux, how do i run x-fix and what do i do with it? and if anyone is confused its x server, not server x.

---

### Post by spcwingo on 2009-03-19
When you boot press "ESC" to enter the Grub OS selection list.  Select the one that ends in "recovery console".  This will bring up a list to select different options from.  From that list select "xfix".  When it's done select "resume normal boot".  If everything went okay you should now have a working x server.  If not, post back and we'll try something else.

---

### Post by shank286 on 2009-03-19
that still didn't work, any other suggestions would be great, otherwise i'll have to pull it out and reinstall and i really want to avoid doing that. Thanks in advance.

---

### Post by fieroboom on 2009-03-19
Boot back into recovery mode again, and this time, instead of running xfix, select the option that drops you to a root prompt. From there, run:
```
dpkg-reconfigure xserver-xorg
```
That will lead you through a series of steps, and *should* reconfigure your X server just like it was when you first installed Ubuntu.
:D
-Paul

---

### Post by spcwingo on 2009-03-19
> **fieroboom said:**
> Boot back into recovery mode again, and this time, instead of running xfix, select the option that drops you to a root prompt. From there, run:
```
dpkg-reconfigure xserver-xorg
```
That will lead you through a series of steps, and *should* reconfigure your X server just like it was when you first installed Ubuntu.
:D
-Paul

This was the next thing I was going to run you through.  If, for some reason, this doesn't work, let us know and I have one more trick up my sleeve.  ;)

---

