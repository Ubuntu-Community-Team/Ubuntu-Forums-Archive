---
title: "HELP With Graphics Drivers and Compiz!!"
date: 2008-12-19
forum: General Help
---

### Post by Jessethenoob on 2008-12-19
Hello i have a graphics card from the  Intel Corporation 82845G Chipset.
I had compiz running fine and there was no problems with any drivers and i could use all the 3d effects i wanted. i ended up coming across a problem with my GRUB and couldnt figure it out so i re-installed Ubuntu and updated to Intrepid Ibex, but ever since i re-installed i havent been able to get any effects working! its a major pain i really liked having Compiz, for the cool 3d effects and also as a composite manager for Kiba-Dock. if anyone can help me it would be greatly appreciated i just dont understand why it worked fine but now it refuses...and by the way i think that i do have the Intel Drivers installed from synaptic.

---

### Post by stderr on 2008-12-20
Hi Jesse

Offhand I don't know, but I may be able to be more help (and others too) if you post the contents of your /etc/X11/xorg.conf file. Also, if you could open up a terminal and execute 

```
glxinfo
```

and post the output.

The xorg.conf file contains your X-Server configuration options, whilst glxinfo should (if glx is up etc) give us an indication of whether your driver's loaded properly and importantly if you've got hardware acceleration.

Cheers

edit/ Oh, and what message does it give you when you try to enable Compiz?

---

### Post by sloggerkhan on 2008-12-20
Please confirm that it's actually using intel and not vesa, and which video output it's using. I doubt you'd have the same issue, but at my work we have a bunch of intel computers that won't work with the latest releases of most linux distributions and drop to the vesa driver. For us it seems to be i865 w/ DVI that's the major thorn, but you never know.

---

### Post by densou on 2008-12-21
however, I think compiz 0.7.x branch works bad compared to previous 0.6.x with Intel drivers, several effects dropped to 'unstable' status according to Compiz developers' forum

so tell us if you are using vesa driver.

---

### Post by abn91c on 2008-12-21
with 8.10 and intel 845 series cards compiz will not work , it is a known bug and the only workaround now is to remove compiz, here is the posting, go to #26: [http://ubuntuforums.org/showthread.php?t=966436&page=3](http://ubuntuforums.org/showthread.php?t=966436&page=3)

---

### Post by yogo on 2008-12-21
Best bet is to downgrade to Hardy, I had that exact same problem on a Dell 2400. I spent all kinds of time trying to get it going, save yourself the headache and install HH, 8.04.

---

### Post by abn91c on 2008-12-21
i Have a dimension 2400 also with kubuntu/ubuntu installed with wubi once i removed compiz 8.10 has worked normally

---

### Post by Jessethenoob on 2008-12-22
> **sloggerkhan said:**
> Please confirm that it's actually using intel and not vesa, and which video output it's using. I doubt you'd have the same issue, but at my work we have a bunch of intel computers that won't work with the latest releases of most linux distributions and drop to the vesa driver. For us it seems to be i865 w/ DVI that's the major thorn, but you never know.

how do i know if im using vesa? i believe i installed the intell drivers in the repository.

---

