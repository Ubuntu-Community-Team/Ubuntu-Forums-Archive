---
title: "Ubuntu freezes on text apps"
date: 2006-06-06
forum: Desktop Environments
---

### Post by zcox on 2006-06-06
I installed Dapper Drake on a Dell Inspiron 4100 laptop yesterday.  It seemed really great (love the new installer) but I'm having a serious problem.  Sometimes when I either open a file in a text editor or switch from another application to an already-opened text editor, Ubuntu totally freezes.  Only part of the text application gets repainted (rest is white) but rest of screen looks normal.  I can't move the mouse or use the keyboard and it never unfreezes (left it for several hours).  The only thing I can do is hold in the power button on the laptop for 5 seconds forcing a shut-down.

This happened like 4/5 times the same day I installed Drake!  The text apps I was using were gedit and Screem.  

Any ideas what's going on here?  Do I need some updated drivers or something?  Does Drake not work on Dell Inspiron 4100?

---

### Post by zcox on 2006-06-08
Has anyone ever experienced Ubuntu freezing on text applications or have any ideas as to what might be the problem here?

---

### Post by gwpritch on 2006-06-08
What video chip do you have and what driver?

---

### Post by zcox on 2006-06-08
I believe it's a Radeon Mobility M6 LY (looking at Device Manager).  How do I find out the driver info?

---

### Post by gwpritch on 2006-06-08
Have a look at the file /etc/X11/xorg.conf
Look in the graphics device section to find the driver. I suspect if you haven't changed anything it will either be 'ati' or 'radeon'. 
If so, you might want to try installing the ATI supplied native linux driver 'fglrx'.
There are several good how-to's on this forum.
That may solve your problem.

---

### Post by zcox on 2006-06-08
Yes in xorg.conf the driver is "ati".  I will try the fglrx driver & keep my fingers crossed...

---

### Post by gwpritch on 2006-06-08
Good Luck

---

