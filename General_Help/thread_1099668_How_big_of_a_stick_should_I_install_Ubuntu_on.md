---
title: "How big of a stick should I install Ubuntu on?"
date: 2009-03-18
forum: General Help
---

### Post by Znupi on 2009-03-18
Hi, I have a project for school which I've done in Python + GTK + some other weird things (like process control and stuff -- that doesn't work right in Windows). I'll have to show this project in a few weeks, but all my school's computers run Windows (bummer). I have two options:

1) Install Ubuntu on my mother's laptop and it that to school, but I don't want to risk messing up her laptop -- she and my dad would be really mad even if I would just lose a few files.

2) Install Ubuntu on an USB stick. I'll have to ask my teacher if the computers at school are able to boot from USB, but that's another problem. The thing is, I don't have a big enough stick, so I'm thinking of getting one. On the stick I'll have to have Ubuntu with one extra package (python-eyeD3 -- awesome for ID3 reading/writing) and at least a couple of gigs of music (my project manages music and stuff, so I need to have a large data set to show the program working on). My question is: would a 4GB stick suffice? Or should I get an 8GB one, just to be sure? Did anyone install Ubuntu on a stick (heh, "ubuntu-on-a-stick"!) before? Approximately how much space does it take? Also, do I need to download an .img? Where from? Thanks!

---

### Post by Neo_The_User on 2009-03-18
4GB is big enough lol! I've made one on a 500MB stick by putting the iso through extremely heavy compression. It was highly unstable and it would only install on the 3rd or 4th try.

---

### Post by LowSky on 2009-03-18
4GB should be fine, just dont go adding too many apps..lol

OH dont use SWAP, SWAP can shorten the Flash cards lifetime.

when installing to the Flash drive, pick manual partiiton, and create your root partition... it might warn you about swap but dont worry, it isn't needed.

---

### Post by Znupi on 2009-03-18
Ah, so I shouldn't use the **System -> Administration -> Create a USB Startup Disk** tool? Should I simply boot an Ubuntu Live CD and install it on the flash drive? Then what's the Create USB Startup Disk tool for? :)

---

### Post by fieroboom on 2009-03-18
> **Znupi said:**
> 
How big of a stick should I install Ubuntu on?


Heh heh... Depends on how hard you wanna smack down Windows... ;)

The [minimum system requirements](http://en.wikipedia.org/wiki/Ubuntu#System_requirements) for a vanilla Ubuntu desktop install recommends 4GB of Disk space, whilst a server install recommends 500MB.

If you have/prefer a 4GB flash drive, then it's relatively simple (if you have the time & desire) to do a minimal install, and then only add on the applications you want. However... I can almost guarantee your USBuntu will be used for much more than this one project, because they come in *very* handy. With that in mind, I'd go ahead and spring for the 8GB thumb drive. You can grab an 8GB thumb drive on newegg.com [for about $16](http://www.newegg.com/Product/Product.aspx?Item=N82E16820326008).
:D
-Paul

---

### Post by mb_webguy on 2009-03-18
> **Znupi said:**
> Ah, so I shouldn't use the **System -> Administration -> Create a USB Startup Disk** tool? Should I simply boot an Ubuntu Live CD and install it on the flash drive? Then what's the Create USB Startup Disk tool for? :)

I would use the Create USB Startup Disk utility.  If you want to install Ubuntu to a USB drive using the LiveCD, you'll probably want to remove your computer's hard drive to avoid messing up your MBR.  I don't think it's worth the extra hassle, since you end up with essentially the same thing.

---

