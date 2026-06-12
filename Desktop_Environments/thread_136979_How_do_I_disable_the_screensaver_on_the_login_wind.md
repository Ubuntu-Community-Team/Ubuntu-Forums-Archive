---
title: "How do I disable the screensaver on the login window?"
date: 2006-02-27
forum: Desktop Environments
---

### Post by diamondsw on 2006-02-27
I need to stop GDM from going to screensaver after a period of inactivity. Not only do others think the computer is off (the monitor switches off), but it also puts up a huge "X" logo when I try to VNC in, making remote login impossible.

Once logged in the screensaver and display blanking are disabled, so all is fine there. This is specifically on the GDM greeter screen.

---

### Post by svref on 2006-02-27
I'm assuming you thought to look through /etc/gdm/gdm.conf .
Sounds like you should write the -dev mailing list for gdm with this question.

---

### Post by diamondsw on 2006-02-27
Yup, been through gdm.conf, various x11 config files, played with xset options - just generally been around the block. I'll try the discussion lists, but after no real responses here or on IRC, I'm not too hopeful.

---

