---
title: "Error when install Xfce 4.2... need help (Solved)"
date: 2005-12-01
forum: Desktop Environments
---

### Post by tOpEzz on 2005-12-01
well... this few day i trying to install Xfce in my Ubuntu 5.04, but always fail.. i need help from those that success install xfce, any tips or guide for me or others?? 
here is my problem;
> checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
[b][COLOR="Red"]!! Failed to configure libxfce4util, see the errors above
!! for details on the problem.[/COLOR][/b]

PLS, I NEED HELP...

---

### Post by aysiu on 2005-12-01
Yeah, it looks as if you're trying to compile it from source. Why?

Follow the instructions in the first link in my sig. Then, follow the instructions in the second link in my sig--except, instead of marking Blender for installation, find all the XFCE components you want.

---

### Post by tOpEzz on 2005-12-01
owh... thanks aysiu... i'm still newbie, because i follow one guide from [www.tuxme.com/node/358](www.tuxme.com/node/358) for installing Xfce... i'll try your guide...

thanks a lot dude.

---

### Post by tOpEzz on 2005-12-03
3d & Blender for what?? how bout my Xfce?? i still want to install it...

---

### Post by timw on 2005-12-08
How I love ubuntu!

Thanks aysiu, great guide, solved a lot of head scratching by just apting:

apt-get install build-essential

phew!

---

