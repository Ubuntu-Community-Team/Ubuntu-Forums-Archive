---
title: "Lovin ubuntu 10.10 but got problems"
date: 2010-10-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by donantlers on 2010-10-28
Ubuntu is kicking total but on my dimension 2400 its a hell of a lot faster than xp and iam loving it. Currently i have a clean install all updates are current but like every so often my keyboard and mouse lock up and i cant do anything but restart, it sucks when iam in the middle of transcodding something. anyone no whats the problem and possibly an answer. I am a newb to linux but that much of a newb ive used puppy pretty dam small linux, ubunt 10.04 and now 10.10 .  If this problem persists its gonna realy suck!

---

### Post by sanderd17 on 2010-10-28
I hope it's not your keyboard that locks up, but your xorg. When it locks up, can you press CTRL+ALT+F1, then you'll come into terminal mode. Login with your username and password and run "top" to see if there are processes that are using to much CPU or RAM.

---

### Post by donantlers on 2010-10-28
the whole screen and mouse and keyboard freeze
i was watching a video on youtube, the video stoped all of a sudden lagged and skiped what the person was saying over and over and then the whole screen froze and sound went away.:confused:

---

### Post by Rodnox on 2010-11-02
Try the following: 


type ```
sudo gedit /etc/default/grub
``` into the terminal.

search for the line: ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```.

And change to the following: ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nohz=off"
```

Then run ```
sudo update-grub
``` in your terminal 

and reboot. 

Tell us what happens.

---

### Post by gibbylinks on 2010-11-02
Just curious whats does the "nohz=off" mean/do

thanks

---

### Post by Rodnox on 2010-11-02
It's turning off the kernel effects. 

The Problem described sounds a lot like a current bug, that affects some intel processors. 

I had it too and setting nohz=off fixed it. It also has a downturn: The battery life is shorter, the cpu get hot faster and other things that are regulated by the efficiency effects. But since the system doesn't run at all, it seems to be the better solution.

---

### Post by gibbylinks on 2010-11-03
Thanks. Would you know of a web page that has all these options listed ? Just curious.

Cheers

---

