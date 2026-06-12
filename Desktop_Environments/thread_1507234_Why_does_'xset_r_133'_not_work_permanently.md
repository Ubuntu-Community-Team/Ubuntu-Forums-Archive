---
title: "Why does 'xset r 133' not work permanently?"
date: 2010-06-11
forum: Desktop Environments
---

### Post by jogeba on 2010-06-11
Hi,

I use 'xset r 133' to set autorepeat for the 'Windows key'.

But somehow after a while autorepeat does not work any longer and I have to redo the 'xset r 133'. I don't log out or so.

What could be the cause?

Greetings

Josef

-- 
Ubuntu 10.04, gnome, compiz

---

### Post by mr_hangman on 2010-06-11
Hi Josef,

Do you have a keyboard with multimedia keys? Does it happen every time you press one of those keys?
If yes, it could be this bug [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/554839](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/554839).

I also have this problem with caps lock set as backspace and haven't found any solution so far :|.

---

### Post by jogeba on 2010-06-14
Hi,

indeed that is the cause. :-(

I will try to vote for that bug.

Greetings

Josef

---

