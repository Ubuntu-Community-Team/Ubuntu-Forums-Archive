---
title: "Splash sceen background colour."
date: 2007-12-08
forum: Desktop Environments
---

### Post by lodravah on 2007-12-08
Hey gang.

Thought this issue would fit well in here.. I'm running 7.10 on my Compaq - laptop, and I have a problem with the login-process. after GDM, the image I want to use for splash screen is preceeded by a nasty orange-light brown background which I am unable to change or remove. I have changed the colour in "login window" to black, but it will not change. I have StartUp Manager installed, but that did not help at all. 

Any thoughts, dudes and dudettes?

---

### Post by Rui Pais on 2007-12-08
Hi
It's a gdmsetup bug on Gutsy. Try:
```
sudo gedit /etc/gdm/PreSession/Default
```
On
```
if [ "x$BACKCOLOR" = "x" ]; then
BACKCOLOR="#dab082"

``` change to
```
if [ "x$BACKCOLOR" = "x" ]; then
BACKCOLOR="#000000"

```

hth

---

### Post by wtigerks on 2007-12-08
[CENTER]***i wish i know it is on mine to i hope some can fix this or have idea on changeing it :)***[/CENTER]

---

### Post by Rui Pais on 2007-12-08
> **wtigerks said:**
> [CENTER]***i wish i know it is on mine to i hope some can fix this or have idea on changeing it :)***[/CENTER]

sorry?

---

### Post by lodravah on 2007-12-08
Cool, thanks a bunch!

---

### Post by Rui Pais on 2007-12-08
> **lodravah said:**
> Cool, thanks a bunch!

you 're welcome 
:)

---

### Post by TheTrueGeek on 2007-12-09
Hey Lodravah - i had the same issue until I was directed to this thread. All sorted me out now.

Rui Pais - thanks for the help. An annoying little bug, gone! :-)

---

### Post by mi.mao on 2007-12-10
Great, thanks for this tip.
It was quite annoying.

---

### Post by Rui Pais on 2007-12-10
> **TheTrueGeek said:**
> Hey Lodravah - i had the same issue until I was directed to this thread. All sorted me out now.

Rui Pais - thanks for the help. An annoying little bug, gone! :-)

> **mi.mao said:**
> Great, thanks for this tip.
It was quite annoying.

subliminal publicity, after 50 logins you only be able to use Ubuntu and eat peach as fresh fruit :lol:


(Glad you find it useful)

---

