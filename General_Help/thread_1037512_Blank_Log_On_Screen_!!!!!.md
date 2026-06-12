---
title: "Blank Log On Screen !!!!!"
date: 2009-01-11
forum: General Help
---

### Post by scootatheschool1990 on 2009-01-11
I have Ubuntu 8.10 and I restarted it. After it booted it up (the part with the black background and text running up) the courser came on the screen. I can move it around, but it shows the busy signal(circle rotating). the screen is blank! is there something to fix my log on screen? if the answer is no, then can i log onto the GUI from a sudo or some other command?

---

### Post by minsf on 2009-01-12
i've already answered you on your other thread:
[http://ubuntuforums.org/showthread.php?t=1034766](http://ubuntuforums.org/showthread.php?t=1034766)
please answer my questions there so we can help you more.
In particular, are you using ubuntu/kubuntu/xubuntu?
In the following, I will assume that you use the regular ubuntu; that is, GNOME desktop manager.
Like I said there, I really think you should try ALT+CTRL+F1. does it give you the command line prompt? (after asking for your username and password of course)

if you do get to the command line prompt, try typing ```
sudo /etc/init.d/gdm restart
``` and press "enter". it'll ask for your password again, and then it suppose to restart your GUI (gdm=Gnome Desktop Manager).

Please let us know if this doesnt help so we can help you further.
Also what graphic card are you using?

---

