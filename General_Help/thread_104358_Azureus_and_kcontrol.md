---
title: "Azureus and kcontrol"
date: 2005-12-15
forum: General Help
---

### Post by ohzopants on 2005-12-15
I have three questions:
1)  How do I get Azureus to start automatically at login?

2)  Whenever I make a change in kcontrol it is not saved.  It always reverts back to what it was, whether I run kcontrol as regular user or via sudo.  How can I fix this? (I must get rid of the f*cking bouncing busy cursor thing)

3)  Also in kcontrol, all screensavers are gone.  Where did they go? How do I get them back?

Thanks.

---

### Post by tabinin on 2005-12-15
> 1)  How do I get Azureus to start automatically at login?

In Konqeror, head to /home/USER/.kde/Autostart/ (where USER is your user name), Edit -> Create New -> Link to Application.  Name the link in the Gerneral tab and tell it what to start in the Application tab:

Command: ./azureus
Work Path: /path/where/you/installed/azureus/

---

### Post by ohzopants on 2005-12-16
Thanks

---

### Post by vijay03 on 2007-05-19
Hi, I need to accomplish the same thing - Could you please tell me how to do it in GNOME? Also, how to auto shut down Azureus after its finished downloading?

---

### Post by corefile on 2007-05-19
> **vijay03 said:**
> Hi, I need to accomplish the same thing - Could you please tell me how to do it in GNOME? Also, how to auto shut down Azureus after its finished downloading?

In Gnome

System > Preferences > Sessions > StartUp Programs Tab

---

### Post by vijay03 on 2007-05-19
Thanks a lot for the very quick reply! Just now i realised auto start azureus is no good for downloads since my wired connection doesnt autoconnect. Thanks anyway!

---

