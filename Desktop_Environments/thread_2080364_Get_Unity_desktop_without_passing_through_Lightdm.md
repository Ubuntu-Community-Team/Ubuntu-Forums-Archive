---
title: "Get Unity desktop without passing through Lightdm"
date: 2012-11-03
forum: Desktop Environments
---

### Post by chipi92 on 2012-11-03
Thats all.

I want to boot my Ubuntu like everyday but replacing Lightdm with Console login (i think getty)

In Grub cofniguration file write "text" in the right place  to get into tty1 when boot.
This will make lightdm not show.

Then we can run ```
xinit -- :1
``` and ```
unity --replace
```
or
startx


Everything I have tried to reach Unity takes it but slowed down so much, unusable. I dont know why.

When launching lightdm and login through, Unity starts perfectly and run smooth.


Clues?

Thanks in advice ;)

---

### Post by ibjsb4 on 2012-11-03
No display manager = nodm

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=nodm&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=nodm&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by chipi92 on 2012-11-03
Near answer, but Im not looking for autologin.
I dont want lightdm but I have some accounts.

With console (ttyx) I can login into one of those accounts and then run X server with Unity as window manager.

Gotcha? Maybe what im saying is impossible :(

---

### Post by ibjsb4 on 2012-11-03
I say possible, but like you, I don't know how.  NoDM works for me, but I am the only user so that will not do for you.  Keep on hunting, good luck  :)

---

