---
title: "New Nvidia Drivers in Jaunty - Gnome does not work"
date: 2009-08-20
forum: Desktop Environments
---

### Post by ViPeRaY on 2009-08-20
Hey guys,

I have been using xinerema with the default drivers which came with the ubuntu. Unfortunetlly when i enable xinerema i cannot use compiz. I read that if i enable twin view, that will let me use compiz with two monitors. In nvidia settings twin view was greyed out. A friend of mine told me that i need to install latest drivers from nvidia,com. I am using Jaunty x64 by the way. So i downloaded the file below and installed it.
```

NVIDIA-Linux-x86_64-185.18.31-pkg2.run

```I stopped the X server before install and everything went smoothly. After i restart i get the message below.
[[IMG]http://img182.imageshack.us/img182/6803/20090820184435.th.jpg[/IMG]]("http://img182.imageshack.us/i/20090820184435.jpg/")

After i click ok it asked me if i want to create a new configuration file for the hardware or use the default conf file. First i tried new conf file, after restart same thing happened. Then i chose default conf file. This time i did not get any error, gnome started successfully. However there is a problem. When i went to enable twin view to nvidia settings by typing "gksudo nvidia-settings" to terminal, i got the error below.
[[IMG]http://img190.imageshack.us/img190/2423/nv1.th.png[/IMG]]("http://img190.imageshack.us/i/nv1.png/")

Then i tried the command that the error was suggesting "sudo nvidia-xconfig" and restart the computer. After that i got the same error that i was getting before (the first picture on this post). I am trying to make x server use new nvidia settings. Any ideas?

PS: I do have two nvidia video cards and one monitor attached to each. So i have total of 2 monitors.

[IMG]http://img182.imageshack.us/i/20090820184435.jpg/[/IMG]

---

### Post by ViPeRaY on 2009-08-20
I removed the drivers come with jaunty and that solved the problem.

---

### Post by jtappin on 2009-08-21
> **ViPeRaY said:**
> Hey guys,

I have been using xinerema with the default drivers which came with the ubuntu. Unfortunetlly when i enable xinerema i cannot use compiz. I read that if i enable twin view, that will let me use compiz with two monitors. In nvidia settings twin view was greyed out. A friend of mine told me that i need to install latest drivers from nvidia,com. I am using Jaunty x64 by the way. So i downloaded the file below and installed it.
```

NVIDIA-Linux-x86_64-185.18.31-pkg2.run

```

Bit of a guess here -- but I think you would be better off using the Ubuntu restricted drivers installer (I'm not exactly sure where to find it as I use Kubuntu), that will at least install the correct Nvidia drivers for your graphics card. Essentially if Ubuntu wants to install an earlier version, that means that the latest drivers no longer support one or both graphics cards.

Of course there can still be problems -- for example on my "test-bed" machine, I can't use the proper screen resolution for the 1680x1050 monitor with the nvidia drivers (173 release) with the DVI output though it works fine with nouveau (on Pardus & Fedora).

---

