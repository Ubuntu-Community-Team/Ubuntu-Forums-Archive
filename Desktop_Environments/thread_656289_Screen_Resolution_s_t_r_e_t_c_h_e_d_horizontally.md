---
title: "Screen Resolution s t r e t c h e d horizontally"
date: 2008-01-02
forum: Desktop Environments
---

### Post by lastps on 2008-01-02
I have a Samsung SyncMaster 216bw widescreen monitor with 1280x1024 resolution and have upgraded to Gutsy.

I was able to check 1280x1024 under System-->Preferences-->Screen Resolution.

However, everything is s t r e t c h e d horizontally.  For example, circles look like ellipses laying on their sides.

Weird thing is that I didn't have this problem with Feisty.

Any ideas?

---

### Post by (((X))) on 2008-01-02
do you have propriatory drivers enabled?
what videocard are you using

---

### Post by lastps on 2008-01-02
pretty standard Dell choice:
Intel 82945G/GZ

i don't think i'm using any proprietary drivers.  how do i check?

---

### Post by (((X))) on 2008-01-02
system->administration->restricted drivers manager

---

### Post by lastps on 2008-01-02
"Your hardware does not need any restricted drivers."

Thanks for working on this...

By putting a ruler on my screen and looking at a known square I calculate the stretching at approximately 22%.

---

### Post by (((X))) on 2008-01-02
In windows I could choose what monitor I am using, widescreen or normal.
not shure if there is such option in ubuntu.

---

### Post by hns on 2008-01-02
Setting screen resolution in Ubuntu desktop does not work properly.
I fixed it by going to console (ctrl-F1) log in as user, then sudo to root.
Closed gdm by giving the command /etc/init.d/gdm stop.
The X server is then closed and not in the way.
Then i run the command dpkg-reconfgure xserver-xorg.
Follow the screens and watch for the option "wide screen"
This i did with Ubuntu and Debian and my 20 inch widescreen is working.
Make a copy of your xorg file for security before you start
Succes

Hans

---

