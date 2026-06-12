---
title: "can't log in after install the Ubuntu Cd.."
date: 2007-06-20
forum: Dell  Ubuntu Support
---

### Post by kay_role7 on 2007-06-20
after finish install i cant log in.. i use DELL Optiplex 320... and i have build in garfic card using ATI Radeon Xpress 1100.

---

### Post by scrooge_74 on 2007-06-20
does it give you an error message and then drops you to the command line? Is that is so you need to change your driver 

login and then do sudo dpkg-reconfigure xserver-xorg  and pick another driver for the card either ati (if there is one) or just playing VESA so you get your GUI back until you can figure things out

---

