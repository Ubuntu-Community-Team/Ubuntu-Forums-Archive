---
title: "beryl installed?"
date: 2008-02-17
forum: Desktop Effects &amp; Customization
---

### Post by TheNation7 on 2008-02-17
Hey everyone, im kinda new to linux so im not sure about this. But i heard that beryl is already installed with Ubuntu 7.10. 

I just installed 7.10, how do i get to the beryl manager so i can play with the settings and go on the cube and such?

---

### Post by FuturePilot on 2008-02-17
Beryl is no longer developed. It was merged back into Compiz to become Compiz Fusion. Yes, 7.10 already has Compiz Fusion installed.
First check if you need a driver for your graphics card by going System&#8594;Administration&#8594;Restricted Driver Manager. If there is one reboot after installing it.
Then install Compizconfig
```
sudo apt-get install compizconfig-settings-manager
```
You can find that under System&#8594;Preferences&#8594;Advanced Desktop Effects Settings.

---

### Post by TheNation7 on 2008-02-17
thanx for the reply, i tried what u said in terminal and i keep getting the error:

couldnt find package compizconfig-settings-manager

maybe im doing something wrong?

---

### Post by overdrank on 2008-02-17
> **TheNation7 said:**
> thanx for the reply, i tried what u said in terminal and i keep getting the error:

couldnt find package compizconfig-settings-manager

maybe im doing something wrong?

HI and you may want to enable your repos
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
And your graphics card will have to support 3D. :)

---

### Post by TheNation7 on 2008-02-17
that did it, thanx man

---

### Post by overdrank on 2008-02-17
> **TheNation7 said:**
> that did it, thanx man

No problem and good luck! :KS

---

### Post by TheNation7 on 2008-02-17
haha hate to be like this, but i enabled the desktopcube, and when i do ctrl, alt, left click nothing happens. I just see like the drag box. any idea y?

---

### Post by overdrank on 2008-02-17
> **TheNation7 said:**
> haha hate to be like this, but i enabled the desktopcube, and when i do ctrl, alt, left click nothing happens. I just see like the drag box. any idea y?

Then you can use Advance desktop manager it will be located under system,preference. Choose the general options , desktop size set the horizontal virtual size to 4. Also make sure the rotate cube box is checked.

---

