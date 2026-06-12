---
title: "dos login"
date: 2009-01-22
forum: General Help
---

### Post by jeroen505 on 2009-01-22
hi, im new to linux/ubuntu

when i login, i get a dos login screen, instead of the normal login screen, and when i login i'm still in the dos screen. how can i get the normal login screen?

---

### Post by taurus on 2009-01-22
What happens when you run this command at a prompt after you've logged in?

```
startx
```

---

### Post by jerome1232 on 2009-01-22
> **jeroen505 said:**
> hi, im new to linux/ubuntu

when i login, i get a dos login screen, instead of the normal login screen, and when i login i'm still in the dos screen. how can i get the normal login screen?

What did you do prior to this happening? ie. Did you try to install some  video drivers? Did you reconfigure something, install some updates?

Just to clarify on terminology DOS is the **D**isk **O**perating **S**ystem the most widely known version is called MS-DOS. I don't think anything uses DOS anymore. [http://en.wikipedia.org/wiki/DOS](http://en.wikipedia.org/wiki/DOS)

What your getting dumped to is the command-line interface of Linux, often abbreviated as cli.

---

### Post by jeroen505 on 2009-01-22
1 the startx does'nt work (no screens found)

2 i installed video drivers

---

### Post by taurus on 2009-01-22
Try reconfiguring your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by jeroen505 on 2009-01-22
it still doesn't work (no screens found)

---

### Post by Prospero2006 on 2009-01-22
Number 1: Please, for the love of God, don't call it DOS. 

Suggestion: 
reconfigure your video driver with envy

try this:
```

sudo apt-get install envyng-core
envyng -t

```

If you have an ATI card or NVIDIA card, that should reconfigure your graphics. It's worth a try.

---

### Post by jeroen505 on 2009-01-25
it still doesnt work, when is try to start envyng -t i get:

[B][I][U]if 173 in candidates['nvidia'] and 177 in candidates['nvidia']:
list indices must be integers[/U][/I][/B]

---

