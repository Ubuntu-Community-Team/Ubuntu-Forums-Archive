---
title: "automatically run X program as root"
date: 2017-07-02
forum: Desktop Environments
---

### Post by bjlockie on 2017-07-02
After I boot, I get a lubuntu desktop.
I want to automate the running of:
sudo echo 0f >/sys/kernel/debug/dri/0/pstate

---

### Post by CatKiller on 2017-07-02
I don't think you do. sudo echo doesn't do what you probably think it does.

What is it that you're trying to achieve?

---

### Post by bjlockie on 2017-07-03
Ya, sudo doesn't work, I need a root shell.
The echo as root in X sets the performance mode of the video card using the nouveau driver.

# cat /sys/kernel/debug/dri/0/pstate
07: core 324 MHz memory 648 MHz
0a: core 540 MHz memory 1620 MHz
0f: core 1058 MHz memory 5000 MHz
AC: core 324 MHz memory 648 MHz

# echo 0f >/sys/kernel/debug/dri/0/pstate

# cat /sys/kernel/debug/dri/0/pstate
07: core 324 MHz memory 648 MHz
0a: core 540 MHz memory 1620 MHz
0f: core 1058 MHz memory 5000 MHz AC DC *
AC: core 1058 MHz memory 5000 MHz

---

### Post by CatKiller on 2017-07-03
OK, so when do you want that to be ran? Are you forcing fullpower all the time? In which case, you can just add the command to some script that gets run at boot, or when X starts, or whatever. If you want it to be interactive, then to use echo with sudo you need to also use tee, like so:
```
echo 0f | sudo tee /sys/kernel/debug/dri/0/pstate > /dev/null 
```

Is there a particular reason why you aren't just using the automatic performance-related stuff that you get with the proprietary driver?

---

### Post by bjlockie on 2017-07-04
> **CatKiller said:**
> OK, so when do you want that to be ran? Are you forcing fullpower all the time? In which case, you can just add the command to some script that gets run at boot, or when X starts, or whatever. If you want it to be interactive, then to use echo with sudo you need to also use tee, like so:
```
echo 0f | sudo tee /sys/kernel/debug/dri/0/pstate > /dev/null 
```

I tried adding the command to /etc/rc.local
It didn't work (I checked the permissions on that file).

> **CatKiller said:**
> 
Is there a particular reason why you aren't just using the automatic performance-related stuff that you get with the proprietary driver?

Because I don't want to install it.
Convince ubuntu to make the proprietary nvidia drivers the default and I'll use it.

---

### Post by CatKiller on 2017-07-04
> **bjlockie said:**
> I tried adding the command to /etc/rc.local
It didn't work (I checked the permissions on that file).

Does rc.local get run automatically by default these days? Honest question; I know there's a switch to systemd (I think) in progress around now, but I don't know the ins and outs of it.

> Because I don't want to install it.
Convince ubuntu to make the proprietary nvidia drivers the default and I'll use it.

They can't.

The proprietary drivers will do what you're trying to do automatically, but if you don't want to install them then that's fine. You'll just have to carry on doing it automatically.

---

