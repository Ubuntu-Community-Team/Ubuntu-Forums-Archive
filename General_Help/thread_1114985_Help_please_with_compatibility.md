---
title: "Help please with compatibility"
date: 2009-04-03
forum: General Help
---

### Post by Kaorichan2009 on 2009-04-03
Im new here and sort of new to Ubuntu. I used ubuntu only a few times because Vista wouldnt let me do squat and my friend gave me a cd for it till i got an xp disk.

Now due to virus threat... I need a bunker to hide in. I also kind of need help figuring out if any of my hardware is compatible i do know i may need something for my video card... anyone have a list of compatible video cards. Mine is Nvidia 6150 SE i think.

---

### Post by kanikilu on 2009-04-03
I couldn't tell from your post if you already have Ubuntu installed or not, but if so, you can go to System > Administration > Hardware Drivers, to see if there are any available.

---

### Post by Kaorichan2009 on 2009-04-03
I dont have Ubuntu installed yet. Sorry I didn't say that. I just need to know if the video drive will work with it before me and my friend throw ubuntu on here to run.

Another question. Can I burn the ISO onto a DVD?

I'm also trying to put Ubuntu on a PS3 will it work there too?

---

### Post by kanikilu on 2009-04-03
With the Ubuntu Live CD, you can try it before installing. If it works from there, then it should work after installing. From there you can check for drivers as suggested above if you want to try to get desktop effects working.

I can't see why you couldn't burn the ISO to DVD, but I've honestly never tried it.

Not sure about the PS3 question.

---

### Post by albinootje on 2009-04-03
> **Kaorichan2009 said:**
>  Mine is Nvidia 6150 SE i think.

Please boot from the Ubuntu cdrom, choose the "Try without installing", and after the desktop is ready, start a terminal (->Applications ->Accessories -> Terminal), and copy&paste the output of these commands :
```

lspci
lsusb
sudo lshw -C video

```

---

### Post by albinootje on 2009-04-03
> **Kaorichan2009 said:**
>  Another question. Can I burn the ISO onto a DVD?

In Ubuntu with the burn program k3b I have burned cdrom iso images to DVDs without problems. I assume other programs should be able to do that too.
> 
I'm also trying to put Ubuntu on a PS3 will it work there too?
Apparently so :
[https://help.ubuntu.com/community/PlayStation_3](https://help.ubuntu.com/community/PlayStation_3)

---

### Post by Kaorichan2009 on 2009-04-03
I guess that live CD threw me off I always thought ISO's had to be written to CDs before you could use them.
I accidentally installed it oops... anyone have any idea how to boot to Ubuntu from windows?

---

