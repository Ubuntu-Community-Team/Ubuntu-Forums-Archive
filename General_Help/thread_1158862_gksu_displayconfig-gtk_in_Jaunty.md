---
title: "gksu displayconfig-gtk in Jaunty?"
date: 2009-05-14
forum: General Help
---

### Post by ierpe on 2009-05-14
Why is gksu displayconfig-gtk not working anymore in Jaunty? What replaces it?

---

### Post by CatKiller on 2009-05-14
It was taken out to be re-written based on Guidance. The closest thing for display configuration at the moment is gnome-display-properties.

---

### Post by foogoo on 2009-05-18
I just upgraded to 9.04 and was pretty surprised displayconfig-gtk is gone. How can I try changing display drivers in Jaunty? That was the only way I knew to do it in 8.10 and gnome-display-properties doesn't let you access drivers. Thanks.

---

### Post by Legace on 2009-05-18
> **foogoo said:**
> I just upgraded to 9.04 and was pretty surprised displayconfig-gtk is gone. How can I try changing display drivers in Jaunty? That was the only way I knew to do it in 8.10 and gnome-display-properties doesn't let you access drivers. Thanks.

Do you mean this:
/usr/bin/jockey-gtk

---

### Post by foogoo on 2009-05-18
> **Legace said:**
> Do you mean this:
/usr/bin/jockey-gtk

Thanks for the input, but that just takes me to the 'Hardware Drivers' app and I don't have my graphics driver displayed. displayconfig-gtk was the only place in 8.10 where I could try changing display drivers.

---

### Post by Legace on 2009-05-18
> **foogoo said:**
> Thanks for the input, but that just takes me to the 'Hardware Drivers' app and I don't have my graphics driver displayed. displayconfig-gtk was the only place in 8.10 where I could try changing display drivers.

What graphics card do you have and what drivers dou want?

---

### Post by foogoo on 2009-05-18
> **Legace said:**
> What graphics card do you have and what drivers dou want?

I have an Intel x3100/GMA 965 which does not play well with Ubuntu. I believe I'm currently using the default Vesa driver, but would like to try some of the updated Intel drivers to see if they are working better with 9.04.

---

### Post by ierpe on 2009-05-19
I have a z61m lenovo laptop, the graphic chipset is an intel 945 and I cannot get my graphics to work properly.

I reversed to the Intrepid driver and it's kind of working fine, except that I can't have my extended desktop...

The display management is the ONLY thing I hate in Ubuntu...

---

### Post by foogoo on 2009-05-19
> **ierpe said:**
> I have a z61m lenovo laptop, the graphic chipset is an intel 945 and I cannot get my graphics to work properly.

I reversed to the Intrepid driver and it's kind of working fine, except that I can't have my extended desktop...

The display management is the ONLY thing I hate in Ubuntu...

Do you mind explaining how you reverted to the Intrepid driver? That may be my best bet...

I wish they can get OpenGL and 3D effects to work properly with this card under Ubuntu. It works fine under Win so I know it can be done, I guess it's just a matter of drivers...

---

### Post by ierpe on 2009-05-19
Guide to revert xorg:

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
[http://ubuntuforums.org/showthread.php?t=1155843](http://ubuntuforums.org/showthread.php?t=1155843)

Im not sure which one I followed anymore. But I think its one of these 2. Otherwise just search in google for similar topic

---

