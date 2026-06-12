---
title: "update killed xbox 360 controller"
date: 2007-12-19
forum: Gaming &amp; Leisure
---

### Post by MEGAMANULTIMATE on 2007-12-19
I own a Dell M1210 laptop.

I used the xpad360 driver to install the controller, and it was working well up until my last system update via Update Manager. I have no idea what went wrong. Any suggestions? Any help at all would be appreciated.

---

### Post by cluepon on 2007-12-19
yeap. Today's 12/19/2007) kernel update killed my USB XBox 360 controller functionality. The module is there. Removing and re-inserting the module does nothing. 

Left plugged in, the controller's center button just flashes on and off. 

Anyone have any ideas?

EDIT: Problem solved. I recompiled the xpad module, dropped the new one in the proper module directory, and one insmod later, working again. 

Annoying. =/

---

### Post by MEGAMANULTIMATE on 2007-12-19
Cluepon, could you show me exactly what you did? I don't trust myself particularly well right now, considering I'm still a newb at this.

---

### Post by po0f on 2007-12-20
MEGAMANULTIMATE,

When the kernel gets updated, you have to recompile modules you custom built.  In a terminal, navigate to the directory where the xpad sources are installed, and just run `make && sudo make install` again.

---

### Post by MEGAMANULTIMATE on 2007-12-20
Thanks a lot, po0f. I reinstalled the driver and it works great.

---

