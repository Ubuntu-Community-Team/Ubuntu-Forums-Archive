---
title: "nvidia graphics config"
date: 2011-01-08
forum: Desktop Environments
---

### Post by davidmaxwaterman on 2011-01-08
Hi,

I have just switched form Ubuntu to Kubuntu and am having a little trouble finding my way around.

One thing I want to use is the tool to configure the nvidia graphics card so that I can get accelerated graphics and can drive additional monitors (eg a projector to make presentations).

Can anyone guide me on how to get this working?

Thanks,

Max.

---

### Post by Krytarik on 2011-01-09
Since I always run Gnome, I don't know the structure of the menus. You will already know where the tool is in Gnome: System -> Administration -> NVIDIA X Server Settings.
If it isn't in the KDE-equivalent, check if it is installed:
```
dpkg -l |grep nvidia-settings
```
If it isn't install it:
```
sudo apt-get install nvidia-settings
```
Then check again the menus. If it still isn't there, just run it from a terminal:
```
nvidia-settings
```

Greetings.

---

### Post by davidmaxwaterman on 2011-01-09
> **Krytarik said:**
> Since I always run Gnome, I don't know the structure of the menus. You will already know where the tool is in Gnome: System -> Administration -> NVIDIA X Server Settings.
If it isn't in the KDE-equivalent, check if it is installed:
```
dpkg -l |grep nvidia-settings
```


Yup, I have that :

```
$ dpkg -l | grep nvidia
ii  nvidia-173-modaliases                       173.14.28-0ubuntu1                                Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-96-modaliases                        96.43.18-0ubuntu1                                 Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-common                               0.2.24                                            Find obsolete NVIDIA drivers
ii  nvidia-current-modaliases                   260.19.06-0ubuntu1                                Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-settings                             260.19.06-0ubuntu1                                Tool of configuring the NVIDIA graphics driver

```

> 
```
nvidia-settings
```


and that runs, but it tells me to run nvidia-xconfig, but I don't have that installed...can't seem to find it anywhere either. I know I had this under Ubuntu (10.4) since this is what I was using before...

Any ideas?

Max.

PS. I see this post <[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1252175&page=2]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1252175&page=2")> asking basically the same thing...seems there is no xconfig package available?

---

### Post by Krytarik on 2011-01-09
You don't have the actual driver installed. :-D

Is there an equivalent to "System -> Administration -> Hardware Drivers/Additional Drivers" in KDE?

This would be the best way to install, unless you know exactly which is the appropriate driver version for your card.

---

### Post by davidmaxwaterman on 2011-01-09
> **Krytarik said:**
> You don't have the actual driver installed. :-D

Is there an equivalent to "System -> Administration -> Hardware Drivers/Additional Drivers" in KDE?


I haven't seen one.

> This would be the best way to install, unless you know exactly which is the appropriate driver version for your card.

I do notice a utility called 'nvidia-detector' but that simply returns 'none'. Perhaps this is why I didn't have any nvidia driver installed? - though I do :

```

$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation G84M [Quadro NVS 140M] (rev a1)

```

---

### Post by davidmaxwaterman on 2011-01-09
> **davidmaxwaterman said:**
> I haven't seen one.

Ah, I find 'Additional Drivers' on the Applications/System menu. It lists some drivers that need to be 'activated', involving some downloads that take a little while.

Let me see how that goes - I'm hopeful.

EDIT: Yup, things are making much more sense now.

Thanks for your help!

Max.

---

