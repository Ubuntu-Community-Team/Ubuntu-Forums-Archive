---
title: "Compiz?"
date: 2007-02-18
forum: Desktop Environments
---

### Post by ayed on 2007-02-18
Ok, I was just searching the synaptic manager, and I found compiz. Is that the like the 3D compiz stuff? And if I install it what happens, and how can I activate it? 

Thanks!

---

### Post by ButteBlues on 2007-02-18
> **ayed said:**
> Ok, I was just searching the synaptic manager, and I found compiz. Is that the like the 3D compiz stuff? And if I install it what happens, and how can I activate it? 

Thanks!
Unless you're using Feisty Fawn (not recommended by the way), the version of Compiz in the repositories is very old.

To install a more recent version, go [here](http://www.go-compiz.org). Check out the Documentation Central for instructions regarding getting graphics card drivers, installing, and running Compiz.

---

### Post by ayed on 2007-02-18
Ok, I installed the compiz. But when I put in the terminal:
[B]ayed@ayed-desktop:~$ compiz
ayed@ayed-desktop:~$ compiz.real: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz.real: No manageable screens found on display :0.0[/B]
What's wrong?

---

### Post by ButteBlues on 2007-02-18
> **ayed said:**
> Ok, I installed the compiz. But when I put in the terminal:
[B]ayed@ayed-desktop:~$ compiz
ayed@ayed-desktop:~$ compiz.real: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz.real: No manageable screens found on display :0.0[/B]
What's wrong?
You don't start Compiz like that. ;)

The easiest way, assuming you used those instructions, is to press Alt+F2 and run:

```
compiz-tray-icon
```

And then right click on it, and check enable GL Desktop. You can also set some common and basic options through the preferences editor.


However, if you do want to start Compiz from the terminal, you can run:

```
compiz --replace gconf
```

---

### Post by navneeth on 2007-02-18
If you don't mind, I have a related question. What are the min. reqs. to run Compiz. I don't have either nVidia or ATI cards. It's an S3 ProSavaage DDR. And I don't know what this means...


>  i810 Drivers

For all Intel integrated GPU models newer or equal to i810, the i810 driver will allow for Compiz to run over AIGLX.

xf86-video-i810 is the corresponding driver package. 

Thanks.

---

### Post by ButteBlues on 2007-02-18
> **navneeth said:**
> If you don't mind, I have a related question. What are the min. reqs. to run Compiz. I don't have either nVidia or ATI cards. It's an S3 ProSavaage DDR. And I don't know what this means...




Thanks.
To run Compiz, what I'd recommend:

Pentium 4 or higher CPU
512 MB RAM
Graphics Cards{
Intel i810 or higher
ATI Radeon 7000 or higher
Nvidia card supported by nvidia proprietary driver}

So where does that leave you? No idea.

Unless the Linux driver for your card supports things like 3d compositing, you won't be able to run Compiz. However, if you can get 3d compositing working on it, then in theory, Compiz should work.

You can try googling - I'm sure someone else has tried to do it.

---

### Post by ayed on 2007-02-19
hmm, none of the ways worked, instead the whole screen just went really weird. How can I check if I have 3D enabled?

---

### Post by jvc26 on 2007-02-19
If I remember rightly the code is:
```

glxinfo | grep rendering

```
To see whether you have direct rendering enabled.
Il

---

### Post by ayed on 2007-02-19
It said no, how do I turn it on... iremeber something

---

### Post by ayed on 2007-02-20
So can I enable 3D acceleration, I have a nvida 5200, and I remeber some where that you can, but I forgot the code!! Please Help!
Thanks!

---

