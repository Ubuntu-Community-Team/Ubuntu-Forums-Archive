---
title: "KDM problems.."
date: 2005-05-12
forum: Desktop Environments
---

### Post by scrooge on 2005-05-12
I want to try out the XP Desktop Environment ([www.xpde.com](www.xpde.com)) and I want to be able to choose it from the KDM (the Session Type list). But I can't find where I can add to that list (or change it in any way).
Please help me out...

---

### Post by wvslkr on 2005-05-13
If you installed it and it wasn't picked up the file to edit is /usr/share/xsessions.  Look
at your other entries; syntax is st-forward. Just add an entry for xpde and you 
should be good to go.  Problem post back.  :)

---

### Post by scrooge on 2005-05-13
Thank you for your answer, but...
I already created a file in the /usr/share/xsessions folder named 09XPde.desktop (by some instructions I found on the internet) and the content is:

[Desktop Entry]
Encoding=UTF-8
Name=XPde
Comment=XP Desktop Environment
TryExec=/usr/share/spde/bin/xpde
Exec=/usr/share/xpde/bin/xpde
Icon=
Typepe=application

which I also copied from the net. Is there something more I need to add to the file or do I have to do something else to activate this?

---

### Post by wvslkr on 2005-05-14
The only thing I can see off-hand is the last line should read 
Type=application

I have seen also, Type=xsession,also if that doesn't work check your
xinitrc is pointing to the correct directories.
If you have tryed to run and get errors please post them.

Other than this I am at a loss. Luck.
I just noticed an error in TryExe= you have spde not xpde.

---

### Post by scrooge on 2005-05-15
Well, now I feel lika a total idiot  ](*,) 
I fixed these typeos and everything worked perfectly  ;-) 
I got to slow down on the keyboard, or read things over... Anyway, if someone is having the same trouble and for some strange reason ends up reading this it should be
TryExec=/usr/share/xpde/bin/startxpde
Exec=/usr/share/xpde/bin/startxpde
or else XPde will complain over missing libborqt...
But many thanks!

---

### Post by wvslkr on 2005-05-16
Happy you got it working. I know what you mean about typos.
I am not a good typist.  Cheers  :)

---

