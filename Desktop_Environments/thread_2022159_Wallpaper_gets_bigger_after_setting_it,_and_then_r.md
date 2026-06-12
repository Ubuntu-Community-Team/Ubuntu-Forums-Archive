---
title: "Wallpaper gets bigger after setting it, and then rebooting?"
date: 2012-07-10
forum: Desktop Environments
---

### Post by Jamie_Edwards on 2012-07-10
Hi guys, 

So I'm running a dual monitor setup one being a 15" 1024x768 res, and the other a 19" 1920x1080 res. ( I know, probably a bad idea, but my 15" is quite old and cannot reach the seconds res )

Anyway, now that's clear, I recently decided to get a wallpaper with a res of 1920x1080 and set it as my background, and looks good on both screens.

Only problem is, when I reboot my box the 19"'s wallpaper gets massive and cuts off the head of the person in the wallpaper, whereas the wallpaper on my 15" is perfectly fine ( well as perfect as it can be with only a resolution of 1024x768 :L )

Oh and one last thing, I've only had it happen with this wallpaper, every other is fine.

Any ideas on a fix? Or on what might be happening?

Thanks,

Jamie.

---

### Post by Jamie_Edwards on 2012-07-11
bump :L

---

### Post by Laiquendi on 2012-07-11
Try with the "Appearance" settings from dash, with the wallpaper position.
Another place where i would look is screens settings. 
Quite difficult situation to get it working simultaneously on both screens.

Oh and what kind of graphic card do you have and which driver to it?

---

### Post by Jamie_Edwards on 2012-07-12
> **Laiquendi said:**
> Try with the "Appearance" settings from dash, with the wallpaper position.
Another place where i would look is screens settings. 
Quite difficult situation to get it working simultaneously on both screens.

Oh and what kind of graphic card do you have and which driver to it?

Thanks for getting back to me, and just so you know as I should have put it up in the OP, I'm running Gnome shell, not Unity :L 

And in answer to the GPU question, I have a VTX Radeon HD 5450, but get this...

I did lspci | more and I get the following:

```
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Manhatta
n [Mobility Radeon HD 5430 Series]

```

Obviously not my card, and I did some looking into this card and found out the MRHD 5430 is a netboot/laptop GPU which isn't right at all as I'm running on a desktop.

ANd I'm having to use the driver Ubuntu has provided, don't know the name of it :L as when I try to install CCC it breaks my OS :L

---

### Post by Jamie_Edwards on 2012-07-13
bump

---

### Post by Laiquendi on 2012-07-13
Had similiar problems. It's a driver issue i think. Try updating it, maybe try development version. ATI has "shittiest" drivers so it may be tough to solve this.
In my situation - just started working with some updates, never rely on ati.

---

### Post by Jamie_Edwards on 2012-07-14
> **Laiquendi said:**
> Had similiar problems. It's a driver issue i think. Try updating it, maybe try development version. ATI has "shittiest" drivers so it may be tough to solve this.
In my situation - just started working with some updates, never rely on ati.

I've read that NVidia have better driver support than ATi, to be honest, I'm rather regretting getting an Ati card now :L Luckily it was only £30 and not any more or I wouldn't be a very happy bunny right now XD

---

