---
title: "Possible to disable login splash?"
date: 2011-12-30
forum: Desktop Environments
---

### Post by audeshmukh on 2011-12-30
[FONT="Verdana"]Hi,

Is it possible to disable/replace the blue colored login splash image (*one with xubuntu written on it with animation of bunch of fireflies underneath*) in Xubuntu?

If yes, how?

Thanks,
-Abhijit

**_P.S._** - I have a running version of Xubuntu Karmic on a ARM development board. I understand, Karmic is outdated, but this is the version I received along with the ARM development board...so have to live with it.

Here it is --> 
[IMG]http://www.dedoimedo.com/images/computers_new_2/xubuntu-9-10-splash.jpg[/IMG]

[/FONT]

---

### Post by audeshmukh on 2011-12-30
Bump ... to keep this thread up in the list. ;)

Any suggestions on this?

---

### Post by azertyh on 2011-12-30
hello,
try
```
sudo mv /usr/bin/xsplash /usr/bin/xsplash.disabled
```

---

### Post by audeshmukh on 2011-12-31
> **azertyh said:**
> hello,
try
```
sudo mv /usr/bin/xsplash /usr/bin/xsplash.disabled
```

HI,

Yes, this did the trick. 

However, I found this post if anyone is interested to deep dive into the customization of Grub, xsplash & usplash.

[http://ubuntuforums.org/showthread.php?t=1337381]("http://ubuntuforums.org/showthread.php?t=1337381")

---

