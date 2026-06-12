---
title: "screen brightness auto maximized"
date: 2009-02-27
forum: General Help
---

### Post by afeasfaerw23231233 on 2009-02-27
The brightness of my notebook auto maximize whenever it boots into gnome, either in battery mode or charging mode. I changed some setting in gconf-editor but still the same. Any one can tell me how to disable the brightness auto-maximizing? Thanks!

edit: I attached a screenshot of my setting

---

### Post by fooman on 2009-02-27
do you have your video drivers installed/enabled?  if so,  there should be a settings manager by nvidia/ati/intel installed somewhere.  you will find options there for brightness/contrast/gamma, etc..

my nvida settings are under system > preferences
on my laptop,  the ati settings are in applications > accessories ...not sure about intel as i do not own one,  but i would guess they have settings somewhere as well.

---

### Post by afeasfaerw23231233 on 2009-02-27
My graphic processor is a SiS integrated 672. After doing a lot of searching I found out SiS doesn't release driver for linux. But I managed to install a 2D acceleration enabled driver for it in this forum. (sorry I forget the link). I don't know where the SiS setting manager locates. Thanks for your quick reply.

---

### Post by afeasfaerw23231233 on 2009-03-01
I have fixed it. System -> Perference-> Power Management Perferences 
Set display brightness to XX%

---

