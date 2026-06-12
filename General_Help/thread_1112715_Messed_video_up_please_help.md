---
title: "Messed video up please help"
date: 2009-03-31
forum: General Help
---

### Post by Irishbmx on 2009-03-31
Computer details
motherboard XFX GeForce 8200 amd 64bit
I use the integrated graphix
OS Ubuntu 8.04 32 bit


I was screwing around and saw a video on you tube about Beryl and though man that would be cool so I went to this website and fallowed instructions as best I could
[http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html)
Well it screwed up my display bad and it didn't even install it I don't know what happened I don't want it anymore I just wanna fix my computer.
I'm stuck in a crappy resolution and I don't know how to fix it I can't set resolution back to how it was and every time I restart it says I'm running in low graphics mode anyone know how I can install the correct drivers ect?

---

### Post by overdrank on 2009-03-31
Hi and those instructions are for Feisty, which version of ubuntu are you using?

---

### Post by Irishbmx on 2009-03-31
8.04 32 bit sorry
and yea i'm dumb

---

### Post by 3rdalbum on 2009-04-01
Ouch... that's like following a "How to install DirectX on Windows 98" document on Vista.

You probably need to reinstall graphics drivers:

```
sudo apt-get install --reinstall nvidia-glx-180
```

Before rebooting, you should probably put the command "compiz --replace" into your startup items. Otherwise it might use the old version of Beryl as your default window manager, fail, and leave you without window borders... a right schmozzle.

Compiz is the successor to Beryl. The majority of effects available for Beryl are in Compiz, and then some! If you install the "compizconfig-settings-manager" package you will be able to tune the effects and do all the outrageous things that you saw in the video.

---

### Post by Irishbmx on 2009-04-01
Ok I fixed resolution part but now it's all messed up I used Envy to reinstall drivers but it's all dark now and kinda choppy It looks kinda like theres a shadow across the screen with a darker bar across the left hand side

attatched SS don't know if you can see it on there

---

### Post by Irishbmx on 2009-04-01
> **3rdalbum said:**
> Ouch... that's like following a "How to install DirectX on Windows 98" document on Vista.

You probably need to reinstall graphics drivers:

```
sudo apt-get install --reinstall nvidia-glx-180
```

Before rebooting, you should probably put the command "compiz --replace" into your startup items. Otherwise it might use the old version of Beryl as your default window manager, fail, and leave you without window borders... a right schmozzle.

Compiz is the successor to Beryl. The majority of effects available for Beryl are in Compiz, and then some! If you install the "compizconfig-settings-manager" package you will be able to tune the effects and do all the outrageous things that you saw in the video.

Ok I understand were I screwed up now lol I'm sorry but I'm still a complete nub to Ubuntu.

And sorry to be a headache but I'm not sure how to do what you said

put the command "compiz --replace" into your startup items

or how to install "compizconfig-settings-manager"

also got this
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-glx-180

---

