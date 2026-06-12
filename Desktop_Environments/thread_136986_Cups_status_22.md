---
title: "Cups status 22"
date: 2006-02-27
forum: Desktop Environments
---

### Post by Cybercool on 2006-02-27
Hello,

I have installed a ubuntu.
And i was trying to install my Canon mp110 with the ip1500 driver that works on a other ubuntu machine.

First i tried it with the cups webgui, but everytime i got in to problems the it just wont start printing. 
So i thought, let's install ubuntu-desktop and try it that way.

But unfortionaly i can't get the printer to work.

With lsusb I see the printer.
When i install the printer using gnome it's see's it, and i can select the driver and it installes it.
In cups webgui it also see's it. 
But al my print jobs are aborted with the /var/log messege:
stopped with status 22


Does anyone know what this can be??

---

### Post by Cybercool on 2006-02-28
Is there no one who can help me please?

---

### Post by councilor on 2006-03-31
I just overcame a status 22 error by installing the **foomatic-filters** package.  If that doesn't work, perhaps expound on what packages you've installed/other steps taken?

---

