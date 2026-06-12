---
title: "Problems getting Emerald to run"
date: 2007-11-28
forum: Desktop Effects &amp; Customization
---

### Post by cronk on 2007-11-28
I've just installed emerald and I am having problems getting emerald to start. I can import themes using the merald theme manager no prob just can't get emerald to actually start. I've been searching for information on my error but can't find much here.

THis is what I get when I try to start emerald:

```
 
ian@ubuntu-box:~$ emerald
emerald: Could not acquire decoration manager selection on screen 0 display ":0.0"
ian@ubuntu-box:~$ 


```

THanks.

---

### Post by PatrickFisher on 2007-11-29
> **cronk said:**
> I've just installed emerald and I am having problems getting emerald to start. I can import themes using the merald theme manager no prob just can't get emerald to actually start. I've been searching for information on my error but can't find much here.

THis is what I get when I try to start emerald:

```
 
ian@ubuntu-box:~$ emerald
emerald: Could not acquire decoration manager selection on screen 0 display ":0.0"
ian@ubuntu-box:~$ 


```

THanks.

I get the same error, but emerald works fine from System>preferences>Emerald Theme Manager

Or, run:

```
emerald-theme-manager
```

---

### Post by cronk on 2007-12-01
Thanks for your help, got it working now.

---

### Post by norferatu on 2008-01-03
I have the same problem here!.. I always had emerald working fine with compiz, but after i upgraded to the new kernel, my window decorations are gone...
And typing "emerald-theme-manager" doesn't solve anything... (Although it works, i cannot load any window manager)

Help please! Any ideas?

---

### Post by Mr Greencastle on 2008-01-03
You could try pressing Alt+f2 and typing this into the box.
```
emerald --replace
```

Hope that helps, Mr Green

---

