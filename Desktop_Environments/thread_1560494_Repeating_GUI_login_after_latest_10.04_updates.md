---
title: "Repeating GUI login after latest 10.04 updates"
date: 2010-08-24
forum: Desktop Environments
---

### Post by srich on 2010-08-24
I have an MSI U100 Winbook with Ubuntu Workstation 10.04 LTS newly installed (about 4 days ago).

The update manager displayed about 15 or so updates for my 10.04 installation which I installed.  Upon reboot, I can not successfully login to the desktop.  It will take my username/password, the screen will go black for a couple of seconds, then the error sound, and back to the login dialogue.

A tail on /var/log/messages displays:

atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0)
atkbd.c: Use 'setkeycodes e077 <keycode>; to make it known.
composit sync not supported

These messages keep repeating.  I am able to login at the console just fine.  I have enabled root login but get the same issues logging in as root.  I have googled and found several articles and postings involving these messages but they are all in reference to upgrading from 9.x to 10.04.  I did not upgrade and did not experience the freezing of applications as noted in those posts.

I'm kinda dead in the water unless someone can help.

---

### Post by srich on 2010-08-28
No one has seen this?  Do I just need to reinstall?

---

