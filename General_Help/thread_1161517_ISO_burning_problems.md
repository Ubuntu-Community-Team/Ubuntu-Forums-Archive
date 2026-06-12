---
title: "ISO burning problems"
date: 2009-05-16
forum: General Help
---

### Post by techturkey on 2009-05-16
I am trying to mount an .iso image to a dvd but i keep getting unhandling errors... I have no clue what that means. I have used the drive to burn pictures and music to dvd's but it doesnt work to burn an iso. 


Pleaz help

---

### Post by paydaydaddy on 2009-05-16
Try using K3b as your burning software. Install it with synaptic.

---

### Post by gettinoriginal on 2009-05-16
> I had that problem with memorex dvds and so did a lot of other people. Verbatim, Sony, TDK all seem to work OK though. seems to be a frequent statement in like threads.  Also, burn at the slowest speed possible. Do not use auto, as that sets speed at about 8 and you want 4.

---

### Post by Game Over on 2009-05-16
If you can get your hands of a mac for about 1-2 hours, download the iso and burn it with Disk Utility. Thats what I did and it was smooth sailing. IMHO, there is not a better DVD burners. Keep in mind I'm new to Linux and have yet to burn a disc.

---

### Post by techturkey on 2009-05-16
I am going to get K3B and run it on the lowest speed, ill see how that works. Thank you if it works and if it doesn't. And im using Sony dvds.

---

### Post by Rocket2DMn on 2009-05-16
> **Game Over said:**
> If you can get your hands of a mac for about 1-2 hours, download the iso and burn it with Disk Utility. Thats what I did and it was smooth sailing. IMHO, there is not a better DVD burners. Keep in mind I'm new to Linux and have yet to burn a disc.

Telling a uesr to use a different operating system to solve a problem isn't really very helpful, unless the task they are trying to do requires it.

K3b should work well, though you will need a bunch of KDE libraries.  Unfortunately some people just seem to have problems with Brasero which Ubuntu uses by default.

---

### Post by Locutus_of_Borg on 2009-05-16
you kids and your needless frilly gui apps

```

cdrecord dev=/dev/sr0 /path/to.iso

```

is all you need

---

### Post by techturkey on 2009-05-17
Well i did use the K3B tool and at 4x speed and it worked perfectly. I will have to experiment with the terminal version of writing disks...

Thanks everybody!

---

### Post by blackened on 2009-05-17
> **Locutus_of_Borg said:**
> you kids and your needless frilly gui apps

```

cdrecord dev=/dev/sr0 /path/to.iso

```

is all you need

Heh, +1 if you're burning ISOs, not so much if you're burning miscellaneous files. For that I prefer Gnomebaker.

---

