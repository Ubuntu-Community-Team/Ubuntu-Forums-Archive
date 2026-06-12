---
title: "DVD / CD Rom issue"
date: 2008-12-28
forum: Desktop Environments
---

### Post by dareofficer on 2008-12-28
I installed Mythbuntu, and then installed the gnome gui, (8.10).  I did this on 4 computers in my house to share the mythTV.  One pc has backend/front end, the rest have front end, this is a mythtv setting.  The issue I believe is NOT Mythtv related, but Ubuntu related.  None of the computers will mount my cd/dvd's.  I can mount them via terminal, but that is it.  If this is a permissions issue, can someone explain how to give the user access?  I checked all the boxes for the users, including, cd/dvd rights.

Thanks.

---

### Post by dareofficer on 2008-12-28
I found the problem.  In mythbuntu, it does not install all the packages, when you pick the gnome gui.

In terminal: sudo apt-get install gnome-mount

That will fix the problem.

Buck

---

