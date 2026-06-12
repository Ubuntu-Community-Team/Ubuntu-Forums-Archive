---
title: "[SOLVED] Login Screen Keeps re-appearing"
date: 2007-03-09
forum: Desktop Environments
---

### Post by pt123 on 2007-03-09
Now when I try to login the login screen keeps reappearing after I enter my username & password.

It's not like the login is wrong, because when I purposely enter an incorrect combination it tells it's incorrect.

Events which caused this problem:-
I tried to install my new nvidia drivers using envy but it  screwed up some where.

Then using envy I had to uninstall nvidia-drivers and may be part of kernel (not sure if this ispossible).


This left many packages orphaned, it advised me to run apt-get autoremove

Then after that I ran apt-get install ubuntu-desktop
Then when I ran startx it was all fine.


After that I had to reboot, that is when this problem occurred.

Anyone know how to fix this problem.

---

### Post by taurus on 2007-03-09
Boot into recovery mode from GRUB menu and perhaps reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```
While you are there, may as well post the output of this command here.

```
df -h
```
And if you want to reboot, just do

```
shutdown -r now
```

---

### Post by pt123 on 2007-03-09
> **taurus said:**
> Boot into recovery mode from GRUB menu and perhaps reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```
While you are there, may as well post the output of this command here.

```
df -h
```
And if you want to reboot, just do

```
shutdown -r now
```

I dont know how to copy the output to a file when I am in a terminal.

When I did this df -h

Had my linux partition /dev/hda6 100% use 0% available.

I thought I had 200MB free. 

How do you uninstall something in apt-get and also have the modules removed from disk?

Is it the same as apt-get remove openofficeorg?

---

### Post by taurus on 2007-03-09
So, your / is all max out.  From the recovery mode, clean out your cache with

```
aptitude clean
df -h
shutdown -r now
```
You should have some free space now.  Log in and it's time to clean whatever stuff that you don't need in your ~/.Trash or your $HOME directory.

---

### Post by pt123 on 2007-03-09
Thanks clearing out the space has solved the problem and I can login in now

---

### Post by imonlyhuman on 2007-03-09
I was having the same problem, although i was able to login in by pressing crtl+alt+f6, starting x after it crashed on the other screen, and logining in as root. I cleared my cache and removed some files. Fixed my problem thanks.

---

