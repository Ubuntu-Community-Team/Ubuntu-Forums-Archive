---
title: "wondering if you could retrieve old computer files if you kept the old os"
date: 2009-02-16
forum: General Help
---

### Post by extravillager on 2009-02-16
im running ubuntu 8.10 and i have a nvidia geforce 6100 installed. i installed the drivers and it worked fine. but then, like a dumb#$$ i decided to mess with my desktop settings ( i wanted a cube) anyway, i can find no way to get back into my account as every time i boot (even in recovery mode) ubuntu first tells me it is running in low graphics mode, then when i say to run that way for this session it refreshes the monitor and sends me back to the box that says that. so long story short, im an idiot and im locked out of my own computer... 
but i was wondering, if i reinstall ubuntu could i select the option to keep and compress the old information and then somehow  access it and transfer it to my new ubuntu files?
i would just reinstall all my info but it would take days as i had may games installed on wine and whatnot.
thank you in advance if anyone can help me (ive been googling all day)

---

### Post by cariboo on 2009-02-16
Instead of reinstalling, why not start in recovery mode and at the menu choose xfix, this will create a default /etc/X11/xorg.conf. Once xfix is done select resume, and you should be taken to your desktop.

Jim

---

### Post by extravillager on 2009-02-16
i just ran a boot errors check thing it said the error was
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Mon Feb 16 01:06:09 2009
(++) Using config fie: "/etc/x11/xorg.conf.failsafe"
(EE) Failed to initialize GLX extension (Compatible with NVIDIA X driver not found)

---

### Post by Old *ix Geek on 2009-02-16
If you installed your data on a separate partition--as you should!--you can reinstall without losing anything.  Yes, you'll lose some things that were installed or changed in the root partition, but for the most part you'll be back in business quickly.

Here's how I do my installs:

/ -- this is where the OS gets installed
/home -- this is where the user directories go
/data -- I store data here for multiple users to access
swap -- swap space

Anyway, you should be able to fix your video problems by using a live CD so you can access files/settings and change them.

---

### Post by extravillager on 2009-02-16
i tried that, but it just sent me to the command prompt, then jerked me away to say i was running in low graphics mode again, and then continued looping me that message as discribed in my first post

---

### Post by extravillager on 2009-02-16
old *ix geek
i tried using a live CD already, but it does not allow me to log in to my account to change the settings, it just sends me to the demo ubuntu you see before you install, i can see where all of my files are stored on the HD, but i cannot access the program files things because i do not have administrative access on a live cd

---

