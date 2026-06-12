---
title: "Strange black box!"
date: 2008-04-02
forum: Desktop Environments
---

### Post by Mehashi on 2008-04-02
One of my friends is having a problem with his ubuntu.

A black rectangular box pops up on his screen (seems normally when he downloads) that wont go away. There is no extra entry in the taskbar either.

He has had to restart to get it to go away, Ive had a look but found no process to close. If anyone knows what it is or has any ideas help would be appreciated. I am with him now so can give feedback!

Thank you!
^_^

---

### Post by kellemes on 2008-04-02
"top" shows nothing of interest?

Sidenote: I'm a big fan of "htop".. much better..
```
sudo apt-get install htop
```

---

### Post by dannyboy79 on 2008-04-02
could we see a picture of it? Also, what exactly is he doing prior to the box coming up? We just need more details to help

---

### Post by kellemes on 2008-04-02
> **dannyboy79 said:**
> could we see a picture of it? Also, what exactly is he doing prior to the box coming up? We just need more details to help

Indeed..

Another thought..
Is he downloading from the browser?
Could it be he's getting a 'normal' popup from some site?

---

### Post by Mehashi on 2008-04-02
It seems he is downloading through 'add/remove'

What is 'top'? A command or program? Sorry I'm quite new to linux myself!

The box covers most of the center of the screen, and he can only shut down as it covers all other options in that menu.

Definately not a pop-up as no entry in taskbar.

He is trying to recreate the bug now but it not coming up, though this has happened several times before, apparently always through add/remove in applications. ^_-

---

### Post by dannyboy79 on 2008-04-03
not sure what it is but if it happens when he initiates or after he's done with add/remove programs, he could try to kill that process instead of restarting the whole computer.

he would first hit alt & f2 to bring up a run command box. then he would enter this within it,
gnome-terminal
then when the terminal came up, he would issue this command

ps aux | grep gnome-app-install

then he would see a number, that's the process number. example: 8668

then he would issue

sudo kill 8668

that should dhut down the gnome-app-install window and hopefully that black box. Not sure how to solve it from even coming up as I don't know what's causing it. sorry. good luck

---

