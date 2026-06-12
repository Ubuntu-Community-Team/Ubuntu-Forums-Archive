---
title: "boots into TTY1 instead of GUI problem"
date: 2009-03-19
forum: General Help
---

### Post by roimekoi on 2009-03-19
When i boot my computer,it will go into TTY1, wasn't like that before the hibernating problem->splash screen
link.
[http://ubuntuforums.org/showthread.php?t=1100431](http://ubuntuforums.org/showthread.php?t=1100431)

From TTY1, how do i go back to GUI mode?
I tried Ctrl+Alt+F7 and got a black screen,
and enter "startX" and it says about the log cannot move to the old log.
where can i learn the terminal commands?
Just started linux 2 months ago ^_^;;

---

### Post by roimekoi on 2009-03-19
> **roimekoi said:**
> When i boot my computer,it will go into TTY1, wasn't like that before the hibernating problem->splash screen
link.
[http://ubuntuforums.org/showthread.php?t=1100431](http://ubuntuforums.org/showthread.php?t=1100431)

From TTY1, how do i go back to GUI mode?
I tried Ctrl+Alt+F7 and got a black screen,
and enter "startX" and it says about the log cannot move to the old log.
where can i learn the terminal commands?
Just started linux 2 months ago ^_^;;

edit: im using ubuntu 7.10

---

### Post by perpetualcacophany on 2009-03-19
try this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo startx 
```

That did the trick for me when I had this problem.

---

### Post by Dr Small on 2009-03-19
You may also try:
```
sudo /etc/init.d/gdm start
```

---

### Post by roimekoi on 2009-03-20
> **Dr Small said:**
> You may also try:
```
sudo /etc/init.d/gdm start
```

it says gdm starts [ok], what to do after that? Ctrl+alt+F7 still gives me black screen

---

### Post by roimekoi on 2009-03-20
> **perpetualcacophany said:**
> try this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo startx 
```

That did the trick for me when I had this problem.

problem still exist

---

### Post by fieroboom on 2009-03-20
The first thing you should do is check the log files. Since you're able to post here, I'm assuming you have a second computer, so the ideal thing to do is SSH from the second PC to the broken one, run these commands, and copy/paste the output here.
```
egrep 'EE|WW' /var/log/Xorg.0.log
```
The purpose of that command is to search your X server's log for errors (EE) and warnings (WW).
:D
-Paul

---

