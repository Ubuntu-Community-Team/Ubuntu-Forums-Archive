---
title: "Unable to edit xorg.conf using 'sudo'"
date: 2006-08-23
forum: Desktop Environments
---

### Post by sixsecondsleft on 2006-08-23
I am trying to edit my xorg.conf to fix my 640x480 screen resolution on a fresh install.

I am opening terminal and typing: sudo gedit /etc/x11/xorg.conf

It opens gedit with a blank page and the header "xorg.conf (/etc/x11)". So, I copy and paste everything from my original xorg.conf, make my changes, and get this message when I try to save:

Could not save the file /etc/x11/xorg.conf.
Unexpected error: File not found

In my terminal, I get the following message:

** (gedit:8794): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.

I am very much a newb, and I hate to ask for help, but I have searched and searched, and I have not figured out what I am doing wrong. Thanks in advance for any help!

---

### Post by firebadger on 2006-08-23
the directory name is X11 - upper case X.

---

### Post by sixsecondsleft on 2006-08-23
Firebadger, you are awesome!  Works perfect... looks amazing!  Thanks a lot!!!

---

