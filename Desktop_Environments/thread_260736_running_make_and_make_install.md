---
title: "running make and make install?"
date: 2006-09-19
forum: Desktop Environments
---

### Post by onegear on 2006-09-19
i'm stumped.  i'm trying to install menumaker so i can populate icewm.  i ran tar xvzf on the tar.gz package and that seems to have unpacked it okay.  the problems start when i try to run 'make' on the package.  i receive the following error:

root@ridulcam1:/home/mcculloc/dl/menumaker-0.99.7# make
bash: make: command not found

is my install of ubuntu simply missing 'make' and 'make install'?

for the life of me, i can't figure out what i'm doing wrong.  i know that ubuntu includes a tool that does all this for me but i would like to do it from the CLI.

thanks for your help?

---

### Post by nikhilk on 2006-09-19
You probably have not installed the "build-essential" package. Install it and you will be able to run make and make install.
But then again I suggest instead of doing "make install" use "checkinstall". The advantage of checkinstall is that it creates a .deb package and installs it, very helpful if you need to remove it in the future. You probably will need to install checkinstall as well.

---

### Post by someguyouknow on 2006-09-19
edit: what the guy above said.

---

### Post by onegear on 2006-09-19
excellent!  thanks for the info!

i thought i was going crazy.......  :-)

---

### Post by onegear on 2006-09-19
checkinstall is very nice......

---

### Post by nikhilk on 2006-09-19
> **onegear said:**
> checkinstall is very nice......
Yup :)

---

