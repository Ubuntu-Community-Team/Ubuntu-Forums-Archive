---
title: "corrupt user profile?"
date: 2010-06-14
forum: Desktop Environments
---

### Post by redstarmachineworks on 2010-06-14
Hi.

I have an Ubuntu 9.10 box that's behaved perfectly until yesterday. I have several user accounts for Gnome and all but one works correctly. When I log into on particular account the screen flickers and settles on a low resolution setting. There is no taskbar at the top of the screen, and I cannot launch any programs from the desktop icons. Additionally, half of the time I try to login as this broken user the system tries to log in but then it dumps me back to the initial screen where I can choose which user to be. If I do log in, I cannot log out. I have to CTRL-F1 and restart Xorg instead.

Every other user profile works perfectly. 

I've never seen this behavior before and I'm quite perplexed. Is there any help for this?

Thanks!

---

### Post by quixote on 2010-06-17
Sounds like the gnome desktop config for that user has been corrupted.  I've never had any luck trying to fix that type of issue, and the one time it happened I wound up reinstalling.  (I only had one user.)  The easy answer here is to delete that user, and then set up the account again.  Or do you have a lot of customizations you'd like to save?

---

