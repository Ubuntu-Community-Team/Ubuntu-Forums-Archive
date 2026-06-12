---
title: "cursor problems - screen saver causes change in colour"
date: 2005-04-01
forum: Desktop Environments
---

### Post by deviantlnx on 2005-04-01
anytime the screen saver activates my mouse cursor becomes monochrome, often disappearing against white or black screens. this is very frustrating and i dont know how to solve it.

i am using the preview release up to date running gnome with an ati rage 128 card.

any ideas on how to keep the cursor from losing its colour without disabling the screen saver?

---

### Post by kamstrup on 2005-04-02
What graphics driver are you using? Look in the file /etc/X11/xorg.conf in the Device section. If it  is not "vesa", then try changing it to that.

IMPORTANT: When messing around with graphics drivers, it is important to know the basics about managing stuff from pure console. If you are not familiar with it, post back for some hints.

Cheers!

---

### Post by deviantlnx on 2005-04-03
no, it is using the ati driver.

i have my screen saver disabled now and it still happens.

---

### Post by kamstrup on 2005-04-04
Does this happen if you use the "vesa" or "fbdev" driver?

---

### Post by deviantlnx on 2005-04-05
havent tried that yet.. will look into that

---

### Post by jonrkc on 2005-05-29
Deviantlnx, until I read your initial post I never thought about the screensaver causing this.  My cursor changes to an ugly (non-antialiased?) shape and either blue or black, becoming often invisible.  It does seem to be the screensaver at fault.  I tested it.  The cursor was OK (freshly logged in).  I locked the screen using xscreensaver and then unlocked, and the cursor was bad.  

So then I ran xscreensaver-demo and chose "File > restart daemon" and killed the xscreensaver-demo window (it wouldn't let me use the "quit" option) and the cursor was then back to the normal, good one.

So a workaround is to restart the xscreensaver daemon, though that's a real nuisance.  I will now read some of the xscreensaver documentation (again) and see if I can find reference to this kind of problem and how to fix it without a workaround.

P. S.  I also tried loading the vesa driver and ended up, with my Princeton VL1916 LCD display, having to manually restart the computer and change back the xorg.conf file to "ati" driver.  The vesa driver resulted in "out of range" error message flashing on my monitor.

I'm glad you pointed out the screensaver connection!

---

### Post by jonrkc on 2005-05-29
OK, here's a link that is suggestive:

[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=129924](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=129924)

Update: I tried putting the ```

Option    "SWcursor"

```
 in my xorg.conf file, as suggested in that link, and so far no cursor problem after using screensaver.  That might be the solution for my setup, at least.  Worth a try!

The option makes the system use a software cursor instead of the hardware one provided by the driver chip.

---

