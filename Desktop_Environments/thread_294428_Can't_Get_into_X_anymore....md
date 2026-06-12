---
title: "Can't Get into X anymore..."
date: 2006-11-06
forum: Desktop Environments
---

### Post by r1zen on 2006-11-06
I recently installed Automatix and noticed an available update for the Nvidia drivers. Not thinking logically, I updated the drivers and restarted. However, after rebooting I just get horizontal lines and can't read or see anything.

I'm not sure how to resolve this issue. I tried searching here, Google, and a few other forums, but havn't found anything useful yet. Any help would be greatly appreciated.

Thanks in advance!

---

### Post by Najand on 2006-11-06
1. Remove the package you installed using:
```

sudo aptitude remove <PACKAGENAME>

```
(If you don't know the name of the package, use
```

aptitude search *nvidia*

```
or something similar to find the package.)
2. Edit your repositories and comment Automatix repositories using # sign by *nano* or *vi* or any editor you like.
```

sudo *nano* /etc/apt/sources.list

```
3. Install the package you removed using ubuntu's official repository, using
```

sudo aptitude install <PACKAGENAME>

```
4. use "startx" or just restart your computer.
(You may also reconfigure your Xorg configuration using the command:
```

sudo dpkg-reconfigure xserver-xorg

```
if you get an error again.)

---

### Post by r1zen on 2006-11-06
Ok, I got it to work, but the screen resolution only goes up to 1024 now when it went much higher before. I have an Alienware 766 with a Geforce Go5700 card and would love to get my old resolution back. Any ideas?

---

### Post by taurus on 2006-11-06
Then install nvidia driver for your graphic card then...

---

### Post by r1zen on 2006-11-06
I'll definitely do just that. I just don't want to screw up again considering I'm new at this whole thing with Linux. I checked the Nvidia site and I'm unsure as to which drivers to get.

---

### Post by taurus on 2006-11-06
> **r1zen said:**
> I'll definitely do just that. I just don't want to screw up again considering I'm new at this whole thing with Linux. I checked the Nvidia site and I'm unsure as to which drivers to get.
Here you go...

[http://albertomilone.com/driver_edgy.html](http://albertomilone.com/driver_edgy.html)
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

