---
title: "jumpy videos..."
date: 2011-01-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by schrummy on 2011-01-06
when i am either watching youtube or other video host web sites, the vid jumps from frame to frame.... the video can load 100% but it will still act like it is buffering....  i am using a wireless connection but i have a "Very Good" connection....
system info
```
GNOME 2.30.2 (Ubuntu 2010-06-25)
Kernel 2.6.32-27-generic
OS type Linux
GCC version 4.4.3 (i486-linux-gnu)
xorg unknown 
```any help will be appreciated.....

---

### Post by mikewhatever on 2011-01-06
What flash player do you have installed? If you don't know, post the output of the following command:
```
dpkg -l | grep -iE "flash|gnash|swfdec"
```

---

### Post by schrummy on 2011-01-06
```
laptop:~$ dpkg -l | grep -iE "flash|gnash|swfdec"
ii  adobe-flashplugin                     10.1.102.65-2lucid1                             Adobe Flash Player plugin version 10
ii  libswfdec-0.8-0                       0.8.4-1build1                                   SWF (Macromedia Flash) decoder library
ii  swfdec-gnome                          2.28.0-1                                        Tools to play SWF files (Macromedia Flash) o

```

---

### Post by mikewhatever on 2011-01-07
You have two flash players installed, adobe and swfdec which probably is the cause of the problem. Decide which one you want to use and remove the other one.
Hint: The adobe player is usually faster.

---

### Post by schrummy on 2011-01-07
works now... thanks for the advice....

---

### Post by mikewhatever on 2011-01-07
Most welcome.:KS

---

