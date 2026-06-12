---
title: "Set Acer AL 1715 resolution"
date: 2009-04-09
forum: Desktop Environments
---

### Post by oldcelt on 2009-04-09
This monitor is capable of 1024 x 768 and was ok under WXP.

There is no Linux driver as far as I can see and it is defaulting to 800 x 600.  I know the technical details but I can't find out how to set up a monitor with the necessary refresh rate etc.

Anybody help please?

Ken

---

### Post by oldcelt on 2009-04-09
> **oldcelt said:**
> This monitor is capable of 1024 x 768 and was ok under WXP.

There is no Linux driver as far as I can see and it is defaulting to 800 x 600.  I know the technical details but I can't find out how to set up a monitor with the necessary refresh rate etc.

Anybody help please?

Ken

Aw, c'mon guys - surely somebody must know how to set up a monitor using the technical data?

---

### Post by Zimmer on 2009-04-09
need to know what graphics card and (if any ) proprietry driver you are using and which Ubuntu.

I have such a monitor in front of me that autodetected and runs the right resolutions!!

---

### Post by oldcelt on 2009-04-10
> **Zimmer said:**
> need to know what graphics card and (if any ) proprietry driver you are using and which Ubuntu.

I have such a monitor in front of me that autodetected and runs the right resolutions!!
Ubuntu 8.10.  I've loaded no additional drivers - just using a new Ubuntu installation.

Graphics card is ATI Rage 128 Pro in an oldish Dell PC.

As I said, this was recognised and worked fine with WXP Pro.

---

### Post by Jakey_TheSnake on 2009-04-10
Run in a terminal:

```
sudo apt-get install displayconfig-gtk
```

Then:

```
displayconfig-gtk
``` 

You'll get a GUI (Graphical User Interface) up, select your monitor make and model, then resolution.

edit: if your monitor/screen doesn't register as plug and play, you'll have to wikipedia your laptop model to find out the screen info.

---

### Post by oldcelt on 2009-04-10
> **Jakey_TheSnake said:**
> Run in a terminal:

```
sudo apt-get install displayconfig-gtk
```

Then:

```
displayconfig-gtk
``` 

You'll get a GUI (Graphical User Interface) up, select your monitor make and model, then resolution.

edit: if your monitor/screen doesn't register as plug and play, you'll have to wikipedia your laptop model to find out the screen info.

No go I'm afraid.  Error says displayconfig-gtk has no installation candidate.

This is a desktop, by the way, not a laptop.

---

### Post by oldcelt on 2009-04-10
OK, forget it!

Simple solution:-
Swap iiyama monitor from WXP box to Ubuntu box and put Acer monitor on WXP box.

Both work perfectly.  Problem solved!

Life is too short to keep messing about with esoteric terminal command lines.

---

