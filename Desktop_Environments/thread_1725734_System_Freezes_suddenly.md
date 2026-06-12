---
title: "System Freezes suddenly"
date: 2011-04-10
forum: Desktop Environments
---

### Post by sandy0594 on 2011-04-10
Hi all,I am very new to Linux of course Ubuntu and this forum..I am using Ubuntu 10.10 for  now..I am poor in bookish terms..
Suddenly my System freezed(hanged)..I tried to kill all the process using terminal,the terminal opens but i couldn't type anything.What to do in such kind of situations?

The instance(freezing) which happened was when I entered the following command in terminal

```
compiz

```[FONT=monospace]

[/FONT]

---

### Post by mikewhatever on 2011-04-10
If a computer freezes after you enter a command, the logical conclusion would be not to enter that command again, unless there is a good reason to. One way to recover from such a freeze is ctrl+alt+f1. That should drop you to a terminal window, log in and restart xserver with the following:
```
sudo service gdm restart
```

...or, you can also reboot:
```
sudo reboot
```

---

### Post by sandy0594 on 2011-04-10
But the problem is i couldn't enter anything into the terminal except opening it..So,i just clicked restart button on the top right..is there any better way to do that?

---

### Post by mikewhatever on 2011-04-10
You should be able to type if the ctrl+alt+f1 works as expected, and if it doesn't, use [sysrq reisub]("http://mark.koli.ch/2009/02/linux-magic-sysrq-key-r-e-i-s-u-b-reboot-even-if-system-utterly-broken.html").

---

### Post by sandy0594 on 2011-04-10
Thanks Mike,I will check it out when again that sort of issue happens.
Thanks for the reply

---

