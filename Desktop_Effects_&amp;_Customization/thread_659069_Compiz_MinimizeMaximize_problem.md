---
title: "Compiz Minimize/Maximize problem"
date: 2008-01-05
forum: Desktop Effects &amp; Customization
---

### Post by explosive on 2008-01-05
Hi,

I have had this problem ever since installing ubuntu 7.10. Both with my ATI card and now with my Nvidia Geforce 7900GTX that I have just installed.

Fairly regularly when I minimize an application or switch to another application when I then try to restore it the window maximizes but everything is "out of alignment". I.e. the window is pushed halfway across 2 desktops and all the buttons/icons/links are out of alignment. For example the close button hotspot will actually be a couple of centimetres to the right of where the image of the X actually is!

Any idea what is causing this bug? - It is very annoying!

---

### Post by explosive on 2008-01-06
*bump* any ideas at all?

---

### Post by r41nz0r on 2008-01-06
Do you see an X on your cursor during startup? Cause I was thinking you may be in safe mode. If not try disabling compizfusion's effects and try and determine if its compizfusion that is causing the problem or another application. Just focus on narrowing down what is causing the problem. Sorry I cannot be of more help *Shrug :(*

---

### Post by explosive on 2008-01-06
I have disabled compiz and the problems appear to have stopped.
I used to see an X cursor during startup when I was using my ATI graphics card but not since changing to an Nvidia card.

---

### Post by explosive on 2008-01-06
Having now spent many more hours with compiz disabled it definetly appears that compiz is causing this problem...

---

### Post by explosive on 2008-01-07
*bump*

---

### Post by explosive on 2008-01-08
*bump again*
Anyone got any ideas at all?

---

### Post by battlesound on 2008-01-09
did you ensure that your xorg.conf file is configured correctly (also helpful to have up-to-date graphics card driver... you're probably all right, but check on it).  See the compiz site:
[http://www.compiz.org/Documentation/Documentation]("http://www.compiz.org/Documentation/Documentation")

The links that you want are on the top left.  Pay attention to the xorg.conf setup, though!  Hope that works or puts you in the right direction.

---

