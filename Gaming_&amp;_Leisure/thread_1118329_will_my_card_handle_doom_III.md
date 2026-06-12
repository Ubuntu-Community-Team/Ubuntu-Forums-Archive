---
title: "will my card handle doom III?"
date: 2009-04-06
forum: Gaming &amp; Leisure
---

### Post by krakk2k on 2009-04-06
i have a volari v8 duo using the xf86-video-xgi  built in driver. will this be capable of running doom III, or do i need to figure out how to install the dedicated linux driver?

---

### Post by krakk2k on 2009-04-06
bumpity bump bump bump =P

---

### Post by hikaricore on 2009-04-06
Please wait 24-48hrs before bumping a post.
Also please do not reply to this message saying you're sorry to further bump your post, I'm not an idiot.  :p

---

### Post by Perfect Storm on 2009-04-06
Never heard of that brand. How well does it run the free FPS games?

---

### Post by LORD_PoLvO on 2009-04-07
obscure card much?
couldnt find much info on it. but i would say your gonna need to install the dedicated linux driver to get anything out of it like most cards. as far as running a specific game your gonna need to post some specs =)

---

### Post by rizzeh on 2009-04-07
It can run Quake3 
[http://ixbtlabs.com/articles2/volari-duo/index-part2.html#p18](http://ixbtlabs.com/articles2/volari-duo/index-part2.html#p18)

I guess the problem will be finding linux drivers

---

### Post by wolfyking2 on 2009-04-07
It looks like your card is actually pretty good, but check the proprietary hardware for linux drivers.

---

### Post by Vadi on 2009-04-07
Well now the guy can't reply for another 12 hours :P

---

### Post by krakk2k on 2009-04-07
> **hikaricore said:**
> Please wait 24-48hrs before bumping a post.
Also please do not reply to this message saying you're sorry to further bump your post, I'm not an idiot.  :p

sorry sir =P

> **Artificial Intelligence said:**
> Never heard of that brand. How well does it run the free FPS games?

my isp is throttling my speed to near dialup speed so i cant test at the minute.

> **LORD_PoLvO said:**
> obscure card much?
couldnt find much info on it. but i would say your gonna need to install the dedicated linux driver to get anything out of it like most cards. as far as running a specific game your gonna need to post some specs =)

specs are in my signature =P

> **rizzeh said:**
> It can run Quake3 
[http://ixbtlabs.com/articles2/volari-duo/index-part2.html#p18](http://ixbtlabs.com/articles2/volari-duo/index-part2.html#p18)

I guess the problem will be finding linux drivers

i've found the drivers on xgis site.

> **wolfyking2 said:**
> It looks like your card is actually pretty good, but check the proprietary hardware for linux drivers.

does anyone have a clue how to install the driver, as it makes no sense to me ={

[http://www.xgitech.com/sd/sd_download3.asp?CTID={608DB519-2CE6-4785-BE9B-46BF40E5EBB3}&PType_3={634A4445-0AC4-4BFB-9177-569E83E98E06}](http://www.xgitech.com/sd/sd_download3.asp?CTID={608DB519-2CE6-4785-BE9B-46BF40E5EBB3}&PType_3={634A4445-0AC4-4BFB-9177-569E83E98E06})

---

### Post by Vadi on 2009-04-07
It's from 2005 and the changelog says "Add 3D functions.". Ehh.

this driver is newer, greater chance of it working: http://www.xgitech.com/sd/sd_download3.asp?CTID={861772EF-231B-4029-AC27-64CEAA6F8F27}&PType_3={634A4445-0AC4-4BFB-9177-569E83E98E06}

Oh! you can just install the "[xserver-xorg-video-sis]("apt:xserver-xorg-video-sis")" package. Might just work:

> X.Org X server -- SiS display driver
This package provides the driver for all SiS and **XGI Volari** cards.

More information about X.Org can be found at:
<URL:http://www.X.org>
<URL:http://xorg.freedesktop.org>
<URL:http://lists.freedesktop.org/mailman/listinfo/xorg>

This package is built from the X.org xf86-video-sis driver module.


---

### Post by krakk2k on 2009-04-07
> **Vadi said:**
> It's from 2005 and the changelog says "Add 3D functions.". Ehh.

this driver is newer, greater chance of it working: http://www.xgitech.com/sd/sd_download3.asp?CTID={861772EF-231B-4029-AC27-64CEAA6F8F27}&PType_3={634A4445-0AC4-4BFB-9177-569E83E98E06}

Oh! you can just install the "[xserver-xorg-video-sis]("apt:xserver-xorg-video-sis")" package. Might just work:

thanks but i already downloaded and compiled with that, works fantastically =D

is there anyway to get a control panel?

---

