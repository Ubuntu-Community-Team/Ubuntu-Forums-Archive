---
title: "Screen resolution...only one option?"
date: 2005-07-29
forum: Desktop Environments
---

### Post by bugz on 2005-07-29
I'm really new to Ubuntu, or Linux in general for that matter. I just finished installing it, and now I can't change my screen resolution. The only option I have is 640x480...

How can I get my resolution to 1024x768?

---

### Post by frodon on 2005-07-29
Don't forget to use the search field with good keywords (like resolution, screen or xorg in your case) to find threads which will often answer your question.
I think you will find all you need in these threads :
[http://ubuntuforums.org/showthread.php?t=46317](http://ubuntuforums.org/showthread.php?t=46317)
[http://ubuntuforums.org/showthread.php?t=45472](http://ubuntuforums.org/showthread.php?t=45472)
[http://ubuntuforums.org/showthread.php?t=47056](http://ubuntuforums.org/showthread.php?t=47056)
However if you still have problems getting a good resolution post your xorg.conf file : ```
sudo gedit /etc/X11/xorg.conf
```
good luck  ;-)

EDIT : DON'T FORGET TO BACKUP YOUR XORG.CONF FILE BEFORE MODIFYING IT
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```USE THE CONSTRUCTOR PARAMETERS OF YOUR SCREEN (for HorizSync and VertRefresh parameters)

---

### Post by djpharoah on 2005-07-29
make sure that xserver-xorg has detected that the right video card

check your /etc/X11/xorg.conf

---

