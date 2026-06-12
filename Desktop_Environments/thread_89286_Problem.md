---
title: "Problem"
date: 2005-11-12
forum: Desktop Environments
---

### Post by Mombo on 2005-11-12
Ok, first off I am an absolute noob at linux so bear with me, I just installed it today for the first time...anyways When I first load up Ubuntu, right after the loading screen disapears, I get a screen that is made up of just random colors and it stays there...How do I fix this?

---

### Post by tseliot on 2005-11-12
What's your graphic card model?

---

### Post by Mombo on 2005-11-12
I have a Geforce 6800

---

### Post by tseliot on 2005-11-12
[QUOTE=Mombo]I have a Geforce 6800[/QUOTE]

A quick fix:

Boot in Recovery mode (select it from the GRUB menu after you turn your computer on)

Then type

```
nano /etc/X11/xorg.conf
```

Then find the section Device and make sure the word I put in red is &#8220;vesa&#8221;:

```
Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "[COLOR="Red"]vesa[/COLOR]"
BusID "PCI:1:0:0"
```


```
CTRL+O to save (yes, use the same name and overwrite the file)
CTRL+X to exit
```

Then type:

```
startx
```

If it works (i.e. if you get to see the graphical interface), restart your computer (do not use recovery mode this time) and everything will work.

Then you might be interested in my guide if you want to enable 3D acceleration for your card:

[http://ubuntuforums.org/showthread.php?t=75074]("http://ubuntuforums.org/showthread.php?t=75074")


Tell me if it works

---

### Post by Mombo on 2005-11-12
Thanks ill try that now

---

### Post by Mombo on 2005-11-12
When I type in that first command is there supposed to be text in there already or do I have to type in all that other stuff? Because when I did the nano /etc/x11/xorg.conf ther was nothing in it, and it wouldnt let me save the file anyway

---

### Post by bartc on 2005-11-12
[QUOTE=Mombo]When I type in that first command is there supposed to be text in there already or do I have to type in all that other stuff? Because when I did the nano /etc/x11/xorg.conf ther was nothing in it, and it wouldnt let me save the file anyway[/QUOTE]

The file should contain quite some text...
Maybe you dont have permission to read the file? Or maybe the file just doesn't exist.
Try ```
"ls -l /etc/X11/xorg.conf"
```
It should return something like this:
[INDENT]-rw-r--r--  1 root root 2978 2005-10-28 22:39 /etc/X11/xorg.conf[/INDENT]

---

### Post by Mombo on 2005-11-12
[QUOTE=bartc]The file should contain quite some text...
Maybe you dont have permission to read the file? Or maybe the file just doesn't exist.
Try ```
"ls -l /etc/X11/xorg.conf"
```
It should return something like this:
[INDENT]-rw-r--r--  1 root root 2978 2005-10-28 22:39 /etc/X11/xorg.conf[/INDENT][/QUOTE]
I did that and I said the file wasnt there

---

### Post by Ampersand on 2005-11-12
The file names are case sensitive, possibly try
```

cd /etc
cd X11
sudo nano xorg.conf

```

The problem might be solved by logging in normally and pressing Ctrl, Alt and + to cycle through the available resolutions.

---

### Post by tseliot on 2005-11-12
Please try this command:

```
apt-get install xserver-org
```

or (if it says you haven't the authorisation)

```
sudo apt-get install xserver-org
```

---

### Post by Mombo on 2005-11-12
They are case sensitive eh? Ok time to try something new again, lol

Ok, problem is fixed...It was the vesa thing, thanks a lot for your help guys. You can expect more questions from me in the future

---

