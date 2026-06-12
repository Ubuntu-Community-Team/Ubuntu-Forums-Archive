---
title: "Login Problem on 9.10"
date: 2010-06-09
forum: Desktop Environments
---

### Post by fremantle on 2010-06-09
i need an absolute solution 0o thres a LOT of thread about this, so there MUST be a solution
]

i was just chillin n using my ubuntu like evry other day thn i shut it down to get a beauty nap.. 3 hrs later i boot it up, the gdm came. i put my password thn a black screen flashed and returned the GDM AGAIN. almost 5000 times.

---

### Post by Satrio Piningit on 2010-06-11
Login to recovery system or safe mode,
put your username and password.

after login succesfull
remove or rename your xorg.conf

$ sudo rm /etc/X11/xorg.conf

or rename that file.

and then

$ startx

---

