---
title: "unexpected large screen resolution!!"
date: 2007-08-30
forum: Desktop Environments
---

### Post by kaushis on 2007-08-30
hi all,
i have 2 issues with ubuntu 7.04 
1)   when i login to ubuntu7.04, i get a large resolution screen(640X480) by default(sometimes). i cant change it to 1024x768 after logging in because the utility shows that 640x480 itself is the largest possible value. all i have to do is restart my system. 
i get normal(1024x768) resolution login if i try restarting my system 2-3 times. :-(
i get this problem almost every alternate time i login(restart) my PC.  why do i get this problem very often? or  why dont i get this error always? why only some times?

2)  i also have another problem, during ubuntu booting, there is a status bar(orange colour). sometimes this status bar never increments. it is always stuck in the initial 5%. why does this happen?
is ubuntu 7.04 still unstable? 

Thank you,

Kaushis

---

### Post by kaushis on 2007-09-02
please some one look into this issue!!! F1!!  F1!!

---

### Post by elderbuy on 2007-09-02
Re your first problem, I had a similar problem (nothing but 640x480), but it was consistent.  That turned out to be that Ubuntu install was overly optimistic and set the default color depth to 24.  My ancient Trident video card does not have enough memory to handle anything over 640x480 at that depth, so I edited
    /etc/X11/xorg.conf
to set the default color depth to 16, and it now consistently comes up with 1024x768 as the default.  Your problem may be entirely different, of course.  By the way, I had the same problem with both Edgy and Feisty Fawn.

As for your second problem, I frequently get the same behavior.  However, 1 or 2 reboots has always gotten past the stall point.  I have not tried to figure it out because of lack of time.  It could be the old AT-based PC that I run Ubuntu on.  But overall, Ubuntu runs well on the old machine.

---

### Post by kaushis on 2007-09-02
thanks elderbuy for a reply.
> **elderbuy said:**
> Re your first problem, I had a similar problem (nothing but 640x480), but it was consistent.  That turned out to be that Ubuntu install was overly optimistic and set the default color depth to 24.  My ancient Trident video card does not have enough memory to handle anything over 640x480 at that depth, so I edited
    /etc/X11/xorg.conf
to set the default color depth to 16, and it now consistently comes up with 1024x768 as the default.  Your problem may be entirely different, of course.  By the way, I had the same problem with both Edgy and Feisty Fawn.

yeah, but the problem in my case is not consistent. if it were consistent then i would also doubt my video card. but unfortunately the case seems to be more complicated. :-(

> 
As for your second problem, I frequently get the same behavior.  However, 1 or 2 reboots has always gotten past the stall point.  I have not tried to figure it out because of lack of time.  It could be the old AT-based PC that I run Ubuntu on.  But overall, Ubuntu runs well on the old machine.
the problem remains for 2-3 reboots as you said. but sometimes if im lucky, i will get it in the first boot itself. 
i feel it very unstable.
any ubuntu gurus to though some light on this problem?

---

### Post by s26c.sayan on 2007-09-02
Try editing the xorg.conf file and put in the correct Horizontal Sync & Vertical Refresh rates  for your monitor.

'sudo dpkg-reconfigure xserver-xorg' is another way.....an interactive method to set up xserver.

---

### Post by kaushis on 2007-09-03
> **s26c.sayan said:**
> Try editing the xorg.conf file and put in the correct Horizontal Sync & Vertical Refresh rates  for your monitor.
how do i know what is the correct refersh rates for my monitor?
> **s26c.sayan said:**
> 'sudo dpkg-reconfigure xserver-xorg' is another way.....an interactive method to set up xserver.
what option to choose in this utility.
sorry for asking so many qquestions. im a beginer. :confused:

---

### Post by s26c.sayan on 2007-09-03
Can you provide the name, make  and model of your graphics card and your monitor?

You can find the refresh rates for your monitor from your hardware manuals. Also, these info could be there at the back of your monitor on a sticker.
It will be a range of values.

---

