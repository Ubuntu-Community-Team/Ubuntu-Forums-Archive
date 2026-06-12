---
title: "Wierd Issues"
date: 2005-04-14
forum: Desktop Environments
---

### Post by ghettobanana on 2005-04-14
I hope this is in the right section and if not please advise, but I have noticed some two issues that I wondered if others have as well.

When I restart or shutdown in either gnome or fluxbox I get this weird pixel bar line thing in the upper left hand corner. It's about 2 inches wide by 10 inches long.

There is no issue with my video driver and never had this issue when running gentoo so I assume it's something with ubuntu.

When fluxbox is loading I get this UPS brown background until my screen loads which then loads my wallpaper and all is good. I need to get rid of that doo doo brown.  \\:D/ 

Any Ideas on the 2?

Thanks

---

### Post by ghettobanana on 2005-04-14
anyone anyone??

---

### Post by speedman on 2005-04-14
The first issue sounds like a video driver problem.  Perhaps your adaptor was not identified properly and the Ubuntu installer configured the X server with the generic vesa driver, or perhaps another driver, which isn't optimal.  Have a look at /etc/X11/xorg.conf to determine what driver has been declared.

WRT your second question, the background colour is being parsed by /etc/gdm/PreSession/Default, which is actually setting the variable from /etc/gdm/gdm.conf by default in Ubuntu.

Edit /etc/gdm/gdm.conf and navigate to this line:

BackgroundColor=#523921

... and change it to whatever suits you.

HTH


Regards,

SM

---

### Post by gunnyman on 2005-04-15
I get a red bar at the top of my screen as well.
I'm running the ubuntu packaged driver on my Nvidia Geforce 4.
Doesn't seem to be effecting (affecting?) anything.

---

### Post by ghettobanana on 2005-04-15
speedman,

You da man on the background color...the video card is not it...it has something to do with ubuntu...i think.  :???:   Are you running fluxbox? I have everything all nice with my v-card.

---

### Post by speedman on 2005-04-15
[QUOTE=ghettobanana]You da man on the background color...[/QUOTE]

Good deal.  :) 

> the video card is not it...it has something to do with ubuntu...i think.  :???:

Perhaps it's a specific X.org issue then.  What is your video card chipset?  Maybe there are other reports out there that could shed some light on your problem.

> Are you running fluxbox?

Nope.  I flirted with fluxbox for several weeks a few years ago, but other than that I have been a Gnome user since the pre 1.0 days.


Regards,

SM

---

