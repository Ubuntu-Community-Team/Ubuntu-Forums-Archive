---
title: "ubuntu login screen all messed up? video drivers bad?"
date: 2006-03-23
forum: Desktop Environments
---

### Post by miles_kailburn on 2006-03-23
I am running ubuntu 6.04 on an ibm r40.  Ran fine for about 2 weeks and then crashed.  Had to hold in the power button to get it out. Now whenever I boot up the spash screen is all stretched and distorted beyond readability.  I have a better windows background then I do with linux but Im guessing i need to update the video card drivers? any help would be great!

---

### Post by dcstar on 2006-03-24
[QUOTE=miles_kailburn]I am running ubuntu 6.04 on an ibm r40.  Ran fine for about 2 weeks and then crashed.  Had to hold in the power button to get it out. Now whenever I boot up the spash screen is all stretched and distorted beyond readability.  I have a better windows background then I do with linux but Im guessing i need to update the video card drivers? any help would be great![/QUOTE]
CTRL-ALT-F1, log into the text terminal, then:
```
sudo dpkg-reconfigure xserver-xorg
```
and go through the whole process.

Once finished test with:
```
startx
```
and then if it is ok, log out of the graphics screen and:
```
sudo reboot
```

---

