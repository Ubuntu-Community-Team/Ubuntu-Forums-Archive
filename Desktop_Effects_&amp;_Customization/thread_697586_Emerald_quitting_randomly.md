---
title: "Emerald quitting randomly"
date: 2008-02-15
forum: Desktop Effects &amp; Customization
---

### Post by bg1256 on 2008-02-15
Title says it all, really.

Running compiz fusion on Gutsy with an Nvidia card and nvidia-glx-new driver.

Every now and again, emerald just stop randomly.

I can get it back by running:
```
compiz --replace
```

but as soon as I close the terminal, emerald dies again. For the record, compiz is still running fine -- I have everything but a window border.

Here's a screenie:

[http://i123.photobucket.com/albums/o299/bg1256/Screenshot-8.png](http://i123.photobucket.com/albums/o299/bg1256/Screenshot-8.png)

---

### Post by aashay on 2008-02-15
This is a known issue with no solution (that I know of)

---

### Post by FuturePilot on 2008-02-15
I think it's just Emerald being a bit buggy. That happened to me once. I hit Alt+Tab and Emerald just crashed.

---

### Post by bg1256 on 2008-02-15
For now, it seems that running emerald from the terminal gets it back up and runinng. i haven't had another crash yet, but I'm sure it's possible.

---

### Post by NightwishFan on 2008-03-02
Yes I have this problem too. It seems to be an emerald issue, so for the time being I am not going to use emerald.

---

### Post by camini on 2008-03-27
Happens to me too now.
Problem did not occur before I:
- upgraded nVidia driver
- re-compile kernel
- auto-updated ubuntu

..so no clue what it really is.

Is there a way to have it automatically restart when it dies?

I usually type "compiz &" in a terminal but I find this somewhat ackward.

cam

---

### Post by NightwishFan on 2008-03-27
In Hardy it auto restarts. In Gutsy you have to open a terminal and type:
```
emerald --replace
```
Then press alt+f2 and close the terminal and type the same command in the run dialog.

---

