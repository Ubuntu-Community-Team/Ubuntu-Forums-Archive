---
title: "System freezes shortly after startup"
date: 2009-04-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fakecafe on 2009-04-27
Hi, I installed Ubuntu 9.04 the other day on my dell dimension 4300. I like Ubuntu... except the system freezes shortly after the desktop loads, rendering the computer useless. I suppose it would be handy to have some symptoms:

*Mouse works, but cannot select or click on anything
*Keyboard is dead, and the caps/num lock doesn't light up.
*Has frozen when loading GIMP, when and after attempting to type in the WEP key for my wireless connection, when trying to set a password for the keychain, and when doing nothing at all.

I looked around for similar problems and solutions, tried some, and none of them worked.

Can anyone help me?

---

### Post by coffeeaddict22 on 2009-04-28
If you have some system function, open a terminal and type in ```
dmesg
```That should give you all the messages the kernel has sent to its log file.  If that doesn't show something complaining, then look in the folder with the system message logs.  open a terminal, then ```
cd /var/log/
```
followed by ```
gedit dmesg.0
```
which should document the last fail; there's a lot of stuff to scroll through, but if you don't have any idea what's causing it you're kindof stuck.

---

