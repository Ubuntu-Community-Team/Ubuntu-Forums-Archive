---
title: "blk screen only cursor"
date: 2014-10-19
forum: Desktop Environments
---

### Post by alvin7 on 2014-10-19
After loggin there is a blk screen and cursor only....I can get to tty but all else is blk.

---

### Post by dry crust on 2014-10-19
Have you just installed Ubuntu Gnome?

---

### Post by davit2 on 2014-10-20
Hi, 
sudo apt-get install --reinstall ubuntu-desktop xserver-xorg

---

### Post by alvin7 on 2014-10-20
I will try that when I get home later will let you know..Thx for the help in advance....

---

### Post by alvin7 on 2014-10-20
No I have had it for about 1 month...

---

### Post by ibjsb4 on 2014-10-20
There is a big difference between Ubuntu-gnome and Ubuntu-desktop.

They are two different desktop environments and two different downloads.

[https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME](https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME)

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by alvin7 on 2014-10-20
Correct i did not install the ISO ubuntu-gnome. I added it through the terminal so I could change back and forth through the loggin screen.

---

### Post by ibjsb4 on 2014-10-20
Is this Ubuntu 14.04?  Does the Unity desktop still work?  Did you do anything that may of cause this (maybe a system update/upgrade, maybe added/removed some software)?  Are you running any third party software (PPA's).  

What happens when you try to go from tty to gui ?
> Ctrl + Alt + F7
While in tty will the startx command do anything?
```
startx
```
You can look for broken packages.
```
sudo apt-get -f install
```
If you haven't already, you can try an update/upgrade.
```
sudo apt-get update && sudo apt-get upgrade
```
We need to try to generate some error messages, give us something to go on.

---

### Post by alvin7 on 2014-10-20
Correct I think it happened after a update I am in the office and will not be home till later....I can try all then..Thx again...

---

### Post by alvin7 on 2014-10-20
Ok tried the following:

sudo /etc/init.d/lightdm stop
sudo dpkg-reconfigure lightdm
sudo etc/init.d/lightdm start


Got the following error message

+1.48s debug user /org/freedesktop/accounts/1000 changed

---

### Post by alvin7 on 2014-10-21
Anyone..Please

---

### Post by alvin7 on 2014-10-21
Anyone....

---

### Post by alvin7 on 2014-10-21
The solution was to uninstall lightdm and then install gdm.

sudo apt-get install gdm
sudo dpkg-reconfigure gdm
restart computer

problem solved no blk screen.

---

