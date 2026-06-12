---
title: "[SOLVED] My desktop disappeared"
date: 2008-09-16
forum: Desktop Environments
---

### Post by opossumjack on 2008-09-16
Hi everybody...
Today I installed a new copy of Ubuntu 8.04 on my computer...
After an update, my desktop and all in it disappeared (the background image, the icons...)

Is there a way I can have it back?Is this problem related to the update?

Thanks in advance :)

---

### Post by Idefix82 on 2008-09-16
I think
```
sudo apt-get gnome-desktop
```
should do the trick.

---

### Post by opossumjack on 2008-09-16
> **Idefix82 said:**
> I think
```
sudo apt-get gnome-desktop
```
should do the trick.
It says that that command doesn't exist... :(

I think the update corrupted something..

---

### Post by Idefix82 on 2008-09-16
I am very sorry, I meant
```
sudo apt-get install gnome-desktop
```

---

### Post by opossumjack on 2008-09-16
> **Idefix82 said:**
> I am very sorry, I meant
```
sudo apt-get install gnome-desktop
```
I tried it... it says it cannot find gnome-desktop....
Any suggestion?

---

### Post by aragorn2909 on 2008-09-16
```
sudo apt-get update

sudo apt-get install ubuntu-desktop
```

should do it for you.

---

### Post by opossumjack on 2008-09-16
> **aragorn2909 said:**
> ```
sudo apt-get update

sudo apt-get install ubuntu-desktop
```

should do it for you.
nothing to do...
ubuntu-desktop is already installed...

I think I'm gonna cry...

---

### Post by Idefix82 on 2008-09-16
So what if you just try to launch it by typing something like "ubuntu-desktop"? I don't have my computer here, otherwise I would try it out myself.

---

### Post by aragorn2909 on 2008-09-16
I assume you still have both panels, and its just your Desktop background and icons that are missing, correct?

If so,
```
gconf-editor
```
should (I assume) help you restore your desktop icons and wallpaper.

---

### Post by opossumjack on 2008-09-17
Ok... it works now...

I restarted my computer this morning and everything worked... Well.. I don't know what to say :D

Thanks everybody for your support

---

