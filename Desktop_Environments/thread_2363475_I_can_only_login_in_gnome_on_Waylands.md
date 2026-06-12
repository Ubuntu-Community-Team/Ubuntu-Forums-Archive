---
title: "I can only login in gnome on Waylands"
date: 2017-06-10
forum: Desktop Environments
---

### Post by bikerviking on 2017-06-10
Hi

I'm pretty new to linux, in general. I don't even know the difference between on waylands or not. But I want to know why can't i Login in plain gnome.


When I try to login in plain gnome or gnome classic, i get a black screen that leads me back to login screen. Is something broken? How can I repair?

---

### Post by wildmanne39 on 2017-06-10
I suspect you are using a nividia card correct?, if so it is a bug but it was fixed with the new driver 375.66.

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1559576](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1559576)

---

### Post by bikerviking on 2017-06-10
I've installed thexserver-xorg-legacyand still happening. I'm confused with this bug report you send me, is there anything else I'm supposed to do?

---

### Post by wildmanne39 on 2017-06-10
You were supposed to install 375.66 driver if you are using a nividia card because as I stated the issue was fixed in this driver version according to the bug report, you were not supposed to do anything else unless that does not fix it.

---

### Post by bikerviking on 2017-06-10
I am using GPU: Intel HD Graphics 5500.

---

### Post by wildmanne39 on 2017-06-10
Okay then this does not apply to you at all, that is why I said if you are using a nvidia card then you need the new driver, honestly I have seen a lot of these issues recently but they all used nvidia cards, I will research with your card and see if I find anything.

---

### Post by wildmanne39 on 2017-06-10
Do you have hybrid graphics, an intel and a nvidia card?
Please run by typing CTRL+ALT+T, and it will open a terminal then copy and paste the command into it and hit enter:
```
lspci | grep VGA
```
post the output here.
Thanks

---

### Post by bikerviking on 2017-06-10
Here's the output

fredo@Renraku-Tsurugi:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 5500 (rev 09)

---

### Post by wildmanne39 on 2017-06-10
Are you using two monitors?

---

### Post by wildmanne39 on 2017-06-10
Please do:
```
sudo apt update
sudo apt dist-upgrade
```
Then reboot if you get looped back to the login screen do:
```
sudo rm ~/.Xauthority
```
does that help?

---

