---
title: "Dare to upgrade???"
date: 2010-01-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by confubar on 2010-01-27
I have an Inspiron 1545 that came pre-loaded with 9.04. I went this route because I don't have much experience. I am very disappointed to find that Blender 3d doesnt work: have been advised to upgrade to 9.10 for this. 
If I use the alternate install disc to upgrade to 9.10, is everything reasonably likely to  work after the upgrade?  I need wireless, would prefer to have sound working. Is there anything I need to know before jumping in to this. I am totally confused by the mixture of horror and "it works fine" stories, would very much like to upgrade but don't want a disaster I don't have the experience to deal with easily. 
Good advice appreciated....

---

### Post by Enigmapond on 2010-01-27
78% you will have no problems with the upgrade...but there are issues, as you can read in the forum, regarding this. It really depends on how badly you want blender to work. If you can hold out until after April, the new LTS Lucid Lynx will become available and hopefully bugs will have been worked out by then. Karmic works well but there is a bit of tweaking to be done.

---

### Post by confubar on 2010-01-29
> **Enigmapond said:**
> 78% you will have no problems with the upgrade...but there are issues, as you can read in the forum, regarding this. It really depends on how badly you want blender to work. If you can hold out until after April, the new LTS Lucid Lynx will become available and hopefully bugs will have been worked out by then. Karmic works well but there is a bit of tweaking to be done.
Would I be able to use the alternate install disc to go directly from Jaunty to Lucid? I had been under the impression that one could only go one step at a time. And, my update manager, doesn't show the 9.10 upgrade.... Does that mean that the spooky dell stuff might not be compatible with upgrades?

---

### Post by llawwehttam on 2010-01-29
> **confubar said:**
> Would I be able to use the alternate install disc to go directly from Jaunty to Lucid? I had been under the impression that one could only go one step at a time. And, my update manager, doesn't show the 9.10 upgrade.... Does that mean that the spooky dell stuff might not be compatible with upgrades?

Quite possibly. You may want to wait til april and do a clean install of lucid lynx though.

---

### Post by gabo.cr on 2010-01-29
I would wait for Lucid too.
You may want to install the ubuntu restricted extras after that.

---

### Post by zipperback on 2010-01-29
You could also consider doing a distribution upgrade via apt-get.

To do this, open a terminal and enter the following into the command line.

```

sudo apt-get update && sudo apt-get dist-upgrade

```

The above command line will update your computer with the repository information and then perform a version upgrade for you. 

As always, be sure to backup any important data from your computer just in case something goes wrong, as you don't want to lose anything important.

I hope this helps you,
- zipperback
:popcorn:

---

### Post by gabo.cr on 2010-01-29
If you can avoid upgrades please do.
A clean install is always the best option, but it takes a little more of work.

---

### Post by waqas1290 on 2010-01-30
The up gradation is some time good and some time not good so please prefer your own choice to upgrade.

---

### Post by gradinaruvasile on 2010-01-30
How does Blender not work? just download the generic build from their site.

---

### Post by confubar on 2010-01-30
> **gradinaruvasile said:**
> How does Blender not work? just download the generic build from their site.
The blender interface doesn't work properly,  menus, windows and tools forming blurred multiple images, forming an unusable mess.... see screenshot.

---

### Post by gradinaruvasile on 2010-01-30
Well thats a mess for sure. What video card do you have? 

Also, if you use desktop effects, disable them. I always did it when running Blender - it just dont mix well with compiz.

---

### Post by confubar on 2010-01-30
> **zipperback said:**
> You could also consider doing a distribution upgrade via apt-get.

To do this, open a terminal and enter the following into the command line.

```

sudo apt-get update && sudo apt-get dist-upgrade

```The above command line will update your computer with the repository information and then perform a version upgrade for you. 

As always, be sure to backup any important data from your computer just in case something goes wrong, as you don't want to lose anything important.

I hope this helps you,
- zipperback
:popcorn:
Thanks for this, zipperback. It gives me another option if  I can overcome my crappy-download-speed problem

---

### Post by confubar on 2010-01-30
[gradinaruvasile]("http://ubuntuforums.org/member.php?u=589640")....
Intel Graphics Media Accelerator X4500HD
I removed compiz... didn't help

---

### Post by confubar on 2010-01-30
> **gabo.cr said:**
> If you can avoid upgrades please do.
A clean install is always the best option, but it takes a little more of work.
My laptop came loaded with 9.04. The info I understood from Dell starter support is that I need to upgrade rather than clean install, to keep the spooky dell drivers and whatever that I need to keep everything working properly.  What would I need to know to do a clean upgrade?

---

### Post by gradinaruvasile on 2010-01-30
Well the x4500hd doesnt have good drivers AFAIK... 

Maybe try the 9.10 but i recommend a clean install if you want to switch - i had my share of problems when upgrading. 
But first boot from a cd or usb and try it. You can run the blender that can be downloaded from their site in live mode.

[http://www.blender.org/download/get-blender/](http://www.blender.org/download/get-blender/)

Just download and unpack wherewer you want and run the executable.

---

### Post by gradinaruvasile on 2010-01-30
> **confubar said:**
> My laptop came loaded with 9.04. The info I understood from Dell starter support is that I need to upgrade rather than clean install, to keep the spooky dell drivers and whatever that I need to keep everything working properly.  What would I need to know to do a clean upgrade?

There are no spooky dell drivers AFAIK. I use a D630 (with nvidia quadro nvs 135m card), i installed Ubuntu on it  versions 8.04, 8.10, 9.04 and now Xubuntu 9.10 - and everything works perfectly. No spooky dell drivers were needed. If there are any, they are already included in the kernel. 
I found that many dell specific packages i installed n 9.04 are included in the base distribution (dellWirelessCtl, dellBiosUpdate etc).

---

### Post by confubar on 2010-01-31
> **gradinaruvasile said:**
> Well the x4500hd doesnt have good drivers AFAIK... 

Maybe try the 9.10 but i recommend a clean install if you want to switch - i had my share of problems when upgrading. 
But first boot from a cd or usb and try it. You can run the blender that can be downloaded from their site in live mode.

[http://www.blender.org/download/get-blender/](http://www.blender.org/download/get-blender/)

Just download and unpack wherewer you want and run the executable.
Good idea to try the live cd.... thanks

---

