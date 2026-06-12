---
title: "Beryl install causes menues and new windows to appear as solid black boxes(HP dv9000)"
date: 2007-06-08
forum: Desktop Effects &amp; Customization
---

### Post by diablo75 on 2007-06-08
I am trying to get an install of Beryl working on a HP Pavilion DV9000, which has a 64-bit AMD processor and an nvidia graphics card in in (I think it's a GeForce Go 6150).

Anyway, the install went fine with the "noapic" option added to the boot of the live CD (I don't know if that line is still present during normal booting now and possibly causing problems; not sure how to check this).

After the install, I got all the updates on.

I tried the "Desktop Effects" in the Preferences menu, and that didn't work.  On someone else's computer, when I did this, it notified me that restricted drivers would have to be installed, and it did this (installed the nVidia drivers) automatically for me.  But this was not the case for the dv9000, which caused the screen to turn solid white for about 20 seconds before returning back to normal, desktop enhancements still disabled.

So I then installed automatix and used it to install the nVidia drivers, and restarted the computer.  No problems so far.

I then followed the guide posted here...

[http://technowizah.com/2007/02/debian-how-to-aiglx-beryl.html](http://technowizah.com/2007/02/debian-how-to-aiglx-beryl.html)

...to install Beryl, and to remove compiz.

Restarted, and this time, the nVidia logo shows up just before the login screen (which was a good sign to me at first).

Then I started beryl, and the cube would work and rotate good.  But if I opened a menu from the task bar, or an instance of firefox, the window or menu would be solid black and you couldn't see anything.

On a second reboot, and retry of beryl, I had a window open when I started it, and the window continued to display just fine after beryl loaded.  So did the menus.  But the desktop background was replaced with solid black...

So, I'm not sure where to go with this problem.  Any ideas out there gang?

---

### Post by Soybean on 2007-06-08
It's a standard problem with the NVidia drivers. The workaround is to right click on the Beryl icon (you may have to relog a couple of times to get this menu to come up not-black), click Advanced Beryl Options-Rendering Path-Copy, and you should be set. More or less. For some people, the problem will still crop up from time to time on a smaller scale; if/when that happens, you have to right click the icon and "Reload Window Manager."

---

### Post by mooha on 2007-06-09
Many thanx to you.. I appreciate your help... worked for me... nice:D

---

### Post by jusmurph on 2007-06-13
Thanks. This also helps me out!

Scartch that... it didn't :(

---

### Post by diablo75 on 2007-06-14
Works for me too!  Thanks.

---

### Post by ededycker on 2007-06-16
same here !
thx

Erik
:)

---

