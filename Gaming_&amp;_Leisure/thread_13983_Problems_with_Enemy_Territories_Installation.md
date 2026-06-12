---
title: "Problems with Enemy Territories Installation"
date: 2005-02-04
forum: Gaming &amp; Leisure
---

### Post by hectorvs on 2005-02-04
Well, to install this game you need to enter your root password... the thing is that well... ubuntu has no root password, instead you have trusty sudo.

The problem is that when you install it using sudo, everytime you run it you have to run it with sudo (ie: sudo et ), if you dont, the game will not remember your settings and it will not let you write to disk (so you can't dload new maps and stuff)  #-o 

Now, whats the solution?

enable the root password? Change the permitions? (if so, how  :confused: )

Thanks!

---

### Post by DDL on 2005-02-04
Hi,

Indeed, you have to use sudo to install ET. But only to install not to play.

After installation,
When a user will run ET, a new directory (.etwolf) will be create in the user home.
All user setting will be save in the .etwolf directory.

1- Delete the .etwolf directory in the user home
2- Run ET from a consol using the user account.

Hope it will help.
DDL

---

### Post by hectorvs on 2005-02-04
I got it working.. when I checked the .etwolf dir the dir was owned by root. That's why i could not write to it.

I just made a quick chown and the problem was fixed.


=)

---

### Post by DDL on 2005-02-05
It sounds good !
Have good frags...
DDL

---

