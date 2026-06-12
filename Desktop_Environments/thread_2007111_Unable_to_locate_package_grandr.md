---
title: "Unable to locate package grandr"
date: 2012-06-20
forum: Desktop Environments
---

### Post by dennus on 2012-06-20
Just did a fresh install of Xubuntu 12.04. 
I want to use both the screen on my laptop and an external display.
To set this up I was looking for grandr. 
But when I type  sudo apt-get install grandr I get

Unable to locate package grandr

I did an update with  sudo apt-get update

But NO LUCK

---

### Post by dentaku65 on 2012-06-20
What is the output of:
```
apt-cache search grandr
```

by

---

### Post by dennus on 2012-06-20
The output is

lxrandr - simple monitor config tool for LXDE

---

### Post by LewisTM on 2012-06-20
Grandr appears to no longer be in the repos, try arandr instead.

Cheers!

---

### Post by dennus on 2012-06-20
Thanks, I did that.
New problem...  I can save a CONFIG in /home/xxx/.displaylayout
but, everytime I boot the laptop I will have to run the script.
I have tried adding it to the STARTUP with   . /user/.displaylayout/script.sh  but it won't start  :-(

And ... I need a fallback in case my second screen, which holds the desktop bar, is not connected.

---

