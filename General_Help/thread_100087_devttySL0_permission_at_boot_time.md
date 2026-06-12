---
title: "/dev/ttySL0 permission at boot time"
date: 2005-12-06
forum: General Help
---

### Post by howlerbr on 2005-12-06
Hi,

I've finally could get my modem working!!!! I've read almost all threads in this forum about the subject!!!

I'm using gnome-ppp for dialing but every time I need to do:

sudo chmod 666 /dev/ttySL0 so the modem is reconized by gnome-ppp. Without this I got no modem found.

How can I put put this at boot time? I've tried to put in slmodemd script but it did not work.

Any ideas?

---

### Post by funkydan2 on 2005-12-06
I think you need to add your normal user to the group "dip".

If you run "sudo pppconfig" you can do this as a setting in the advanced options.

---

