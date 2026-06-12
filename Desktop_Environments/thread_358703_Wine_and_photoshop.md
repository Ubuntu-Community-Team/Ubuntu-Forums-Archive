---
title: "Wine and photoshop"
date: 2007-02-11
forum: Desktop Environments
---

### Post by chrome101 on 2007-02-11
Hi folks,

I have installed Wine cause I prefer to use Photoshop (used it from LE version), I cannot get on with GIMP and time consuming when all I want to do is design something quickly. Wine installed ok, but Im stuck on how to install photoshop.

Can anyone help please?

Satellite Pro 
Ubuntu 6.10
and loving it!!!

---

### Post by jincast90 on 2007-02-11
What version of Photoshop are you trying to run?

---

### Post by chrome101 on 2007-02-11
Version 7

---

### Post by chrome101 on 2007-02-11
Ive done it...

A bit of surfing led to this website: [http://frankscorner.org/](http://frankscorner.org/)
Photoshop 7 install: [http://frankscorner.org/index.php?p=ps7](http://frankscorner.org/index.php?p=ps7)

The install was then straight forward...

Hope this helps others in the same boat as me,

Now to test.

---

### Post by chrome101 on 2007-02-11
Tesr failed...

I have just followed the instructions from franks corner. Now this is the error message I get when running from terminal:

arty@oyarsa:~$ wine photoshop.exe
wine: could not load L"c:\\windows\\system32\\photoshop.exe": Module not found


I have tried opening from the Application>Wine>Programs>Photoshop menu, but nothing happens.

Any Ideas?

---

### Post by machoo02 on 2007-02-11
Check out the page on Photoshop 7 at the [WINE AppDB]("http://appdb.winehq.org/appview.php?iVersionId=1336") to see if there are any tips/special instructions.  Also, if you *really* need to get it working, I think that [Crossover]("http://www.codeweavers.com") lists Phtotshop 7 as one of their supported apps.

---

### Post by alextj on 2007-02-11
Try starting photoshop with:
[COLOR="RoyalBlue"]wine "c:\program files\adobe\Photoshop 7.0\Photoshop.exe"[/COLOR]
Of course, change path to where you installed your photoshop to.

But I am still having troubles with the latest version of Wine (0.9.30). The Layers window doesn't function properly! Layers are essential for an effective work flow.
They used to work with Wine 0.9.8, but I still haven't figured how to install older version of Wine on Ubuntu Edgy. Bummer.

---

### Post by chrome101 on 2007-02-19
Thanks Alex... I just copied & pasted the code in terminal and photoshop worked. Tested and everything looks ok so far....

---

### Post by chrome101 on 2007-02-19
> **alextj said:**
> Try starting photoshop with:
[COLOR="RoyalBlue"]wine "c:\program files\adobe\Photoshop 7.0\Photoshop.exe"[/COLOR]
Of course, change path to where you installed your photoshop to.

But I am still having troubles with the latest version of Wine (0.9.30). The Layers window doesn't function properly! Layers are essential for an effective work flow.
They used to work with Wine 0.9.8, but I still haven't figured how to install older version of Wine on Ubuntu Edgy. Bummer.

Maybe you should try reinstalling the the older version. Everything seems ok in the new version at the moment. Need to find a shortcut to launch photoshop, instead of command line

---

