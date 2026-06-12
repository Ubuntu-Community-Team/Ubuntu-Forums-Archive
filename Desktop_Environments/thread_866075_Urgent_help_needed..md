---
title: "Urgent help needed."
date: 2008-07-21
forum: Desktop Environments
---

### Post by mirchichamu on 2008-07-21
I reinstalled ubuntu because of my mistake but now my display is only 800 * 640. My graphics accelerator is ATI mobility Radeon.I need help how to correct that?

---

### Post by evertmantel on 2008-07-21
Try to reboot in Recoverymode; then once booted start xfix.
This makes it possible to define mouse, keyboard AND screen.

---

### Post by mirchichamu on 2008-07-21
> **evertmantel said:**
> Try to reboot in Recoverymode; then once booted start xfix.
This makes it possible to define mouse, keyboard AND screen.

Thanks for your support. I did what you asked but unfortunately it freezes at log on. I restarted again froze at log on. Now I logged on from windows at this forum. What to do now?

---

### Post by rogier.de.groot on 2008-07-21
Does it freeze when you do a normal boot?

---

### Post by mirchichamu on 2008-07-21
> **rogier.de.groot said:**
> Does it freeze when you do a normal boot?

Thanks. Yes. As I mentioned above, after I did the above procedure. I cannot log on to ubuntu anymore.

---

### Post by nickdbliss on 2008-07-21
Login to terminal session. And edit ur xorg.conf file.
Do, sudo nano /etc/X11/xorg.conf

Or u can just type this at terminal:

sudo dpkg-reconfigure xserver-xorg, it ll reconfigure ur xorg file. 
You will be able to login then.

---

### Post by nickdbliss on 2008-07-21
When u are done loggin in. Try to check the box in Restricted Hardware Drivers dialog box. It ll install ur graphic drivers.

---

### Post by mirchichamu on 2008-07-21
> **nickdbliss said:**
> Login to terminal session. And edit ur xorg.conf file.
Do, sudo nano /etc/X11/xorg.conf

Or u can just type this at terminal:

sudo dpkg-reconfigure xserver-xorg, it ll reconfigure ur xorg file. 
You will be able to login then.

THANKS NICKDBLISS!
But how can I log on? I told that it freezes at log on.

---

### Post by rogier.de.groot on 2008-07-21
Let me clarify - does Ubuntu hang when doing a recovery mode boot - and more importantly - where in the process does it hang? If your X configuration (the one you made with the "xfix" option) is screwed up your machine might just hang because of it. Can you boot into text-only mode? If you can, try logging on and checking for old xorg.conf files in the /etc/X11 directory (e.g. "ls /etc/X11/xorg*"). Maybe restoring your older xorg.conf file would make it work again.
If you can't log on even in text mode, something is seriously wrong...

---

### Post by nickdbliss on 2008-07-21
> **mirchichamu said:**
> THANKS NICKDBLISS!
But how can I log on? I told that it freezes at log on.
Can u go to terminal mode? Those commands i posted above ll be posted from terminal.Try hitting:
Ctrl+Alt+F1.

And u can click on thanks button if u want to thanks.

---

### Post by nickdbliss on 2008-07-22
Hope ur problem is solved by now.Cheers

---

### Post by mirchichamu on 2008-07-22
> **nickdbliss said:**
> Hope ur problem is solved by now.Cheers

Thanks nickedbliss for your continuous support.
My problem is not only not solved but increased. When I tried everything, and failed, I decided to install ubuntu again. But surprisingly, once I succeeded but again when I installed the driver ATI, it stopped working again. After that I tried to reinstall but not re installing.
I invite all the big brains to help me.

---

