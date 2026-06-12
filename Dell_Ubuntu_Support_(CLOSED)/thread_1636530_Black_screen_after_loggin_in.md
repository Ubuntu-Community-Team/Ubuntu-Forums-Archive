---
title: "Black screen after loggin in"
date: 2010-12-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by xagutxu on 2010-12-03
Hi:

I have a Dell laptop with a docking and the corresponding monitor. Ubuntu did not detect any screen resolution for the monitor, and I tried to change it, unsuccessfully, because now I have a black screen which arises after logging in.
I have read something in Internet about changing the xorg.conf file, but it does not exist in these newer Ubuntus. So, how can I put the screen back?

Thanks a lot,

Xagutxu

---

### Post by sikander3786 on 2010-12-03
Welcome to the forums :-)

Which version of Ubuntu is this?

Some more details regarding hardware, RAM, graphics card etc.

---

### Post by xagutxu on 2010-12-03
The CPU is: Intel(R) Core(TM)2 Duo, and 1,40 GHz, 2,95 GB RAM.

I would like to know if a way to recover my initial configuration exists...

Thank you for your interest.

---

### Post by sikander3786 on 2010-12-03
Press Ctrl + Alt + F1 at your login screen. Log in to the tty1 using your credentials.

First of all check if you are not running out of space on any of your partitions (free space is necessary).

```
df -h
```

For backing up xorg.conf,

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Reconfigure graphics,

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot,

```
sudo shutdown -r now
```

See if you can get to the desktop this time.

P.S: You didn't list your graphics card make and model? And you get the black screen after you type your password and try to login? You can actually get to the GDM login screen?

---

### Post by wojox on 2010-12-03
If you can get to a terminal run

```
lspci | grep VGA
```

---

