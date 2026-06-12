---
title: "Ctrl-Alt-Bksp to restart X in 9.04"
date: 2009-05-15
forum: General Help
---

### Post by chellrose on 2009-05-15
In the past, I've been able to use Ctrl-Alt-Bksp to log out, and restart the X server.  Since upgrade to 9.04, this no longer works.

Is there something I can do to make it work again?  Or was this functionality removed in Jaunty?

Thanks. :)

---

### Post by kanikilu on 2009-05-15
[http://ubuntuforums.org/showthread.php?t=1130382](http://ubuntuforums.org/showthread.php?t=1130382)

---

### Post by binbash on 2009-05-15
[http://www.ubuntu-inside.me/2009/05/howto-enable-ctrlaltbackspace-on-ubuntu.html](http://www.ubuntu-inside.me/2009/05/howto-enable-ctrlaltbackspace-on-ubuntu.html)

---

### Post by Ms_Angel_D on 2009-05-15
1) Install the “dontzap” package
```
sudo apt-get install dontzap
```
2) Open Terminal or Konsole and type:
```
sudo dontzap --enable
```
or
```
sudo dontzap --disable
```
Where “disable” means that Ctrl+Alt+Backspace restarts the xserver while “enable” means that it won’t.

---

### Post by chellrose on 2009-05-15
Thanks.  Problem solved. :)

---

### Post by zika on 2009-05-15
or simply use Alt(left)+SysRq(PrintScreen)+K.

---

### Post by urosg3 on 2009-05-15
Problem solved.Tnx man, pozdrav prijatelju!

---

### Post by zika on 2009-05-16
nema na &#269;emu, kom&#353;ija ... :)
(not at all, neighbor ... )

---

