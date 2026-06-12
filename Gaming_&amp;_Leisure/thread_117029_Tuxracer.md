---
title: "Tuxracer"
date: 2006-01-14
forum: Gaming &amp; Leisure
---

### Post by Ubuntuud on 2006-01-14
Hi, how can I install tuxracer? When I type "apt-get install tuxracer" an error comes up saying: "can't find /var/lib/apt/lists/lock" What should I do? Download a compiler and compile the sourcecode? In that case, which compiler would you recommend?

---

### Post by joselin on 2006-01-14
Hi,

Check [this page]("https://wiki.ubuntu.com/AddingRepositoriesHowto") to enable repositories.

Then:

```

sudo apt-get update
sudo apt-get install tuxracer

```

Regards.

---

### Post by Ubuntuud on 2006-01-14
OK. Thanks.

---

### Post by Ubuntuud on 2006-01-14
But where is it? I only get planet pinguin racer, it looks like it, but it runs much to slow.

---

### Post by briancurtin on 2006-01-14
"The game TuxRacer isn't developed anymore, but a fork called PlanetPenguin
Racer exists.  This is an empty transition package, with the purpose to
install the new package planetpenguin-racer on upgrades.

The packages tuxracer, tuxracer-data and tuxracer-extras can safely be
removed."

taken from synaptic



as for it being slow: do you have 3D acceleration enabled?

---

### Post by Ubuntuud on 2006-01-14
I don't know if I have 3D acceleration enabled. How do you see/enable that? And Planet Pinguin racer isn't fun. I liked the original Tuxracer because of it is so simple: 1 type of tree, 1 color fish... Is it possible to get the original tuxracer?

---

### Post by Perfect Storm on 2006-01-14
Which card do you have?

---

### Post by Ubuntuud on 2006-01-14
I think my accelerator is called Intel 915GM.

---

### Post by Perfect Storm on 2006-01-14
```
sudo gedit /etc/X11/xorg.conf
```

find the **Section 'Module**

and add:

```
Load        "drm"
```

reboot

that should do the trick.


.:=The AI Dude=:.

---

### Post by Ubuntuud on 2006-01-14
Can I type "Load "drm"" anywhere? Or is there a specific place? And does it matter how many spaces you type between "Load" and ""drm""?

---

### Post by curuxz on 2006-01-14
Anywhere in the correct section, and no the number of spaces does not matter tho I always try and keep it in line with everything else :)

---

### Post by Perfect Storm on 2006-01-14
Just make sure it's under Section "Module"

Here's a snapshot of mine without "drm" (I have gf4 so I don't need it).

```
Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"

```

I don't think it will make any diffrence where you put it in the Section "Module". (Anyone correct me if I'm wrong).

---

### Post by Ubuntuud on 2006-01-14
OK. Thanks alot.

---

### Post by Scratty on 2006-01-20
Hi,
I think I've damaged planetpenguin-racer somehow. It seems like the keyboard steering controls have ceased to work after an attempt to install my joystick according some instructions here among the forums. Everytime I try to enter the new controls in the keyboard control menu they'll disappear when I review the settings. However it works fine with other keys, like characters and numbers, but not arrow-keys. I've even tried to reinstall the game, but of no avail.
I think that joystick script must have done something really naughty. Or could it just be coincidence? I can agree that it is sounds pretty unlikely that the joystick hack would have anyting to do with this. But anyting can happen in Linux.

Hints please. I would really like to be able to play this great game again.

---

### Post by Scratty on 2006-01-20
Ah, I managed to fix it:
```

:~/.ppracer$ rm options

```

---

### Post by Ubuntuud on 2006-01-21
OK. That's handy, I had the same problem...

---

### Post by midwinter on 2006-01-21
I just used different keys, not a big deal ;)

---

