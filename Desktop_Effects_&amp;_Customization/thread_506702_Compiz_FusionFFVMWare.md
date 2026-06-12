---
title: "Compiz Fusion/FF/VMWare"
date: 2007-07-22
forum: Desktop Effects &amp; Customization
---

### Post by sparks0548 on 2007-07-22
I finally have my system configured just the way I wanted it.  I was able to get the Desktop Effects running properly under FF, yet I wanted to check out Fusion and see how it responded.  I am a bit apprehensive to conduct the install.  I have all the packages I need to do the install, yet I'd like to know if anyone has had any issues with the NVidia driverand VMWare.  

I run a single VM with XP on it so I can run Visual Studio .NET.  I don't use the VM for anything else.  I have all the updated drivers, packages, and software.  After hours of configuring and installing I'd hate to shoot myself in the foot with something that could possibly destroy my setup.

I don't run any games in the VM nor am I going to, I'd just like to have the rest of the "bells and whistles" running on it.

My system is a HP DV2120 laptop.  1GB DDR II SDRAM, NVIDIA GeForce Go 6150 256MB

Thanks in advance for the insight.

---

### Post by scxtt on 2007-07-22
i don't believe vmware should factor into this at all ... just for the record, i have vmware running on an AMD box w/ an integrated 6100 and the "nvidia-glx-new" driver ... it works just fine ... and it worked fine when i have beryl on that box for a little bit too.

you can take a "snapshot" of your ubuntu install using something like **partimage** - only potential problem you'd have w/ it is if you only have 1 disk in your box, cause you can't back up the drive and write to it @ the same time (unless you have it divided into multiple partitions) - or it can use NFS ...

---

### Post by sparks0548 on 2007-07-22
I guess I was wondering how my VM would respond with the Fusion.  Can I turn it off through the System menu if it causes my system to grind to a halt?  I would like to be done with Visual Studio but I'm attached to the hip with it and have started to tinker with Mono Develop yet I have trouble letting go of the tether to VS Toolbox...LOL.  I really need to learn Python and C++

---

### Post by scxtt on 2007-07-22
vmware didn't care in the least that i was using beryl ... i haven't used Fusion, but i'm willing to bet it still wouldn't care ...

if it messes up your X session just switch over to vt1 or one of the other virtual terminals and kill it there - Ctrl+Alt+F[1-6]

---

