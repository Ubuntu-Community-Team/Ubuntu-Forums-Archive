---
title: "Monitor requires readjust on every boot"
date: 2006-05-06
forum: Desktop Environments
---

### Post by daboochmeister on 2006-05-06
Hi, i have a 19" Envision monitor, and an nVidia MX400 graphics card -- both of which are being detected correctly.  Everything works fine -- except that when after each login or X restart, I have to manually readjust my monitor settings (e.g., horizontal size, trapezoid, etc.).  By manually, I mean w/ the control buttons on the monitor itself, not any X configuration utility.  The settings aren't terrible, they're just a little bit off.

I've tried setting various screen sizes -- 18.1, 19, 20, etc.  19" gets closest, which surprised me since the actual viewable diagonal is less.  By closest, I mean the screen is the least amount off after reboots at that setting.

Do I need to manually set the millimeter settings for h and v-size in xorg.conf?  Other thoughts?

Thanks.  p.s., this is a CRT, and it doesn't have any "autocenter" or such feature.

---

### Post by RavenOfOdin on 2006-05-06
Have you tried sudo dpkg-reconfigure xserver-xorg ?

---

### Post by daboochmeister on 2006-05-07
Sorry, should have said that -- yes, have done dpkg several times, no effect.

---

