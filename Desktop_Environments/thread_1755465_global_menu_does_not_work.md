---
title: "global menu does not work"
date: 2011-05-11
forum: Desktop Environments
---

### Post by stijnblommerde on 2011-05-11
os: ubuntu 11.04

issue: global menu does not function as it should.

issue description: global menu shows title, not menu. menu is shown on second line. firefox add on (global menu bar integration) installed.

image:

[attach]191822[/attach]

---

### Post by kostkon on 2011-05-11
Try installing or re-installing the following package:
```
firefox-globalmenu
```
and then restart firefox.

---

### Post by stijnblommerde on 2011-05-11
> **kostkon said:**
> Try installing or re-installing the following package:
```
firefox-globalmenu
```and then restart firefox.

uninstalled and re-installed firefox-global menu in ubuntu software center > restarted firefox > no result

---

### Post by stijnblommerde on 2011-05-11
the global menu does not work well in any program: firefox, libreoffice, banshee etc.

---

### Post by Frogs Hair on 2011-05-11
In Firefox , navigate to add-ons and disable the Global menu extension and this will give the old menu back.

For Libre Office see the low bar menu on this page [http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

---

### Post by stijnblommerde on 2011-05-11
> **Frogs Hair said:**
> In Firefox , navigate to add-ons and disable the Global menu extension and this will give the old menu back.

For Libre Office see the low bar menu on this page [http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

i don't want to disable the global menu. i want to enable it!

---

### Post by stijnblommerde on 2011-05-11
solved!

solution: I uninstalled and re-installed indicator-appmenu. i guess the file was corrupt.

thanks all for replying

---

### Post by Frogs Hair on 2011-05-11
> **stijnblommerde said:**
> i don't want to disable the global menu. i want to enable it!
 
Sorry about that , beyond doing what you have already done you could try to reinstall
the Global menu package for Firefox in the Synaptic Package Manager  or Firefox its self. Sometimes creating a new  profile for Firefox can help so the application doesen't keep reloading the same configuration. I have gone back to Rythmbox as my default music player , so I only used Banshee for a day.

---

