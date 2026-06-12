---
title: "Problem installing video card (yup, .run problem)"
date: 2009-05-01
forum: General Help
---

### Post by Sponno on 2009-05-01
So I'm new to ub, and loving it, but I cant install my 9600GT, I have the driver from nVidia's website, and it's a .run file, but when i use the shNVIDIA-Linux-x86_64-180.51-pkg2.run command it comes up with Can't open NVIDIA-Linux-x86_64-180.51-pkg2.run. Does not matter if I try with the x86 or x86-64 versions, it gives me this error. I'm using the newest version of ub, any help? Thanks!

---

### Post by taurus on 2009-05-01
Are you in the right directory when you ran that command?

```
cd ~/Desktop
sudo sh NVIDIA-Linux-x86_64-180.51-pkg2.run
```
Of course, you need to shut down X server first before you can install a driver for your graphic card since it will complain about it as soon as you run it.

Look in System -> Administration -> Hardware Drivers to see if your graphic card is on the list.

---

### Post by Sponno on 2009-05-01
> **taurus said:**
> Are you in the right directory when you ran that command?

```
cd ~/Desktop
sudo sh NVIDIA-Linux-x86_64-180.51-pkg2.run
```Of course, you need to shut down X server first before you can install a driver for your graphic card since it will complain about it as soon as you run it.

Look in System -> Administration -> Hardware Drivers to see if your graphic card is on the list.


Nope, its not in the list.

---

### Post by Sponno on 2009-05-01
Also, how do i disable the X server, or whatever it is I need to do? excuse the retardation, I'm 17 now and have been using windows since 95, so I'm a bit one-track.

---

### Post by taurus on 2009-05-01
```
sudo /etc/init.d/gdm stop
```

---

### Post by Sponno on 2009-05-01
> **taurus said:**
> ```
sudo /etc/init.d/gdm stop
```


All that does is flash some text about daemons on my screen...?

---

### Post by 3Miro on 2009-05-01
If you are new to Ubuntu you shouldn't be doing this. You can mess too many things too easily (I have been using Linux since 2000 and doing what you are trying to do has always ended in a disaster of some sort).

Go to System -> Administration -> Hardware Manager and it will list available drivers for your Nvidia card. Pick one (probably the newer one) and select Activate (then wait a few minutes, it might take time). That is the correct way to do drivers in Ubuntu.

---

### Post by Sponno on 2009-05-01
> **3Miro said:**
> If you are new to Ubuntu you shouldn't be doing this. You can mess too many things too easily (I have been using Linux since 2000 and doing what you are trying to do has always ended in a disaster of some sort).

Go to System -> Administration -> Hardware Manager and it will list available drivers for your Nvidia card. Pick one (probably the newer one) and select Activate (then wait a few minutes, it might take time). That is the correct way to do drivers in Ubuntu.


For some reason, now that worked, before when I had the driver on my desktop it wasnt on the list. thanks guys.

---

### Post by 3Miro on 2009-05-01
You probably had to reload the repository database (fetch from servers). You can do that manually from System -> Admin -> Synaptic (however, there is no need now since it works).

---

