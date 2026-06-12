---
title: "MY Ubuntu 7.04 freezes when it starts up!"
date: 2007-08-05
forum: Dell  Ubuntu Support
---

### Post by Elliot_M on 2007-08-05
Hi i was wondering if someone could help me out im running Ubuntu 7.04 on a DEll Inspiron E1505 (ATI Graphics card)and everything was working great i had no errors i got everything working just fine ive been using ubuntu for about 3 months now and only this morning it loads up to the orange default background and loads Nautilus and then just stops loading is frozen right in the middle of the things starting up and the mouse is frozen and i cant do anything but stare at the screen! PLEASE HELP!!

---

### Post by RHorse on 2007-08-05
Sounds like might be a video driver problem.

You can try getting into rescue console at boot and then
typing sudo dpkg reconfigure xconfig-xorg and see if you can tweak the video setup and shake things up.
??

---

### Post by Elliot_M on 2007-08-05
> **RHorse said:**
> Sounds like might be a video driver problem.

You can try getting into rescue console at boot and then
typing sudo dpkg reconfigure xconfig-xorg and see if you can tweak the video setup and shake things up.
??

do you know of any video tweaks that i should change?

---

