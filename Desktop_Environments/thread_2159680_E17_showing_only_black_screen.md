---
title: "E17 showing only black screen"
date: 2013-07-04
forum: Desktop Environments
---

### Post by aryoadhi on 2013-07-04
I've installed E17 on my Ubuntu 13.04. After selecting 'Enlightment', it shows me some options. I forget what did I choose, but I think it's suits for my Acer Aspire V5-471.
Then, after E17 loaded successfully, I got nothing but black screen. I'm able to open terminal usually (Ctrl+Alt+T). What should I do to make E17 working properly?
[[IMG]http://imageshack.us/scaled/medium/802/ro66.png[/IMG][SIZE=2]click image to enlarge[/SIZE]]("http://imageshack.us/photo/my-images/802/ro66.png/")
*edit: * Also I can control my cursor, and sometimes could select some icons on 'black desktop'.

---

### Post by TenPlus1 on 2013-07-04
It sounds like something is wrong with your settings, you could try and delete the .e directory from your home folder and log out and back in again, this will restart the e17 wizard and let you set it up again...

---

### Post by gnugen on 2013-07-04
What commands did u use to install e17. Did you try logging out and logging back in.

---

### Post by aryoadhi on 2013-07-04
> **gnugen said:**
> What commands did u use to install e17. Did you try logging out and logging back in.
I'm just use this:
```
$ sudo apt-get install e17
```

> **TenPlus1 said:**
> It sounds like something is wrong with your settings, you could try and delete the .e directory from your home folder and log out and back in again, this will restart the e17 wizard and let you set it up again...
Worth for a try for me, for now I'm running Windows...

*edit:* Tried, and still blank, even resetting it's options... :(
*edit 2:* Solved, disabling OpenGL fixes my problem :)

---

