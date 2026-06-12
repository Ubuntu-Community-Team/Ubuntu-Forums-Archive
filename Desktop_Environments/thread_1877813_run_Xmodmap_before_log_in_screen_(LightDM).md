---
title: "run Xmodmap before log in screen (LightDM)"
date: 2011-11-08
forum: Desktop Environments
---

### Post by MyKal on 2011-11-08
for reasons mostly irrelevant to this post i need to change certain keyboard keys around BEFORE logging in 

i have a custom .Xmodmap file in my home folder and it works fine but it only kicks in after i have left my log in screen and started n to gnome 

my question is would it be possible to make my .Xmodmap file run before lihtdm loads so that it is ready when i need to put in my password or alternatively is there something else i need to o to change me keys in the login manager?

---

### Post by matt_symes on 2011-11-08
Hi

Open a terminal and type

```
sudo nano /etc/rc.local
```Enter your password. It will not be echoped to the screen.

Add the line

```
/usr/bin/xmodmap /path/to/your/.Xmodmap
```before the *exit 0;* command. Add any extra switches you want.

Press ctrl + o to save and ctrl + x to exit.

Test it by rebooting.

Kind regards

---

### Post by MyKal on 2011-11-08
awesome thanks for the speedy response i will try this out now and let you know if it works

---

