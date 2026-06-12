---
title: "Blackout after Nvidia driver download"
date: 2005-11-01
forum: Desktop Environments
---

### Post by Malpin on 2005-11-01
I just got a new mother board, processor, and hard drive and decided to load ubuntu 5.10 on it.(well first i tried out windows x64 but after the trial went back to linux). Anyways i have tried everything i know and everything i have seen on the forums but nothing seems to work. When i first install ubuntu it runs fine, but when i try to get the nvidia driver to work everything goes wrong.

The problem- After installing the nvidia driver, i reboot ubuntu. It goes through the basic boot and load process but when it is time to start up i am greated with a nice black screen and 5 seconds after my screen goes into power saving mode.

Now, i have tried every different screen resolution available, and 5 or more different ways of installing the driver but it all ends up the same.

My Computer Hardware
New ECS K8T890-A mother board
1gb of ram
nvidia 5200 ultra
new Amd Anthlon 3200
new 120gb wd sata hard drive
ubuntu 5,10 breezy badger 32bit operating system

Any ideas? i am compleatly stumped and want to play my games!

edit, i have tried the how to manualy guide and such, but i just came across another topic, i never though of loading up the old driver, im doing that now and hopefully i wont have to reinstall ubuntu again

Edit2. That idea was a no-go, looks like im going to have to re-install ubuntu yet again. Tried it with the old version of hoary also and nothingseems to work....Anyone know what the problem could be?:confused: :confused: :confused:

---

### Post by rj686 on 2005-11-01
i had problems with the new drivers too make sure you remove all the info pertaining to the old drivers. That was my problem, ubuntu was just confused:p

---

### Post by Malpin on 2005-11-01
Ive done that, and ive tried installing it first with a frsh copy, same thing happens, i allways get a black screen

---

### Post by wylfing on 2005-11-01
I cannot think of five different ways to install the nvidia driver :)

It's unclear from your post whether you are trying to use the Ubuntu-supplied nvidia-glx package, or if you are downloading the driver from the nVidia web site. I am going to bet you're trying to install the one from nVidia's site.

If that guess is right, then stop trying that. If necessary, run the downloaded driver package with the --uninstall option to get rid of all of that stuff. You may also need to do run these commands:
```
modprobe -r nvidia
modprobe -r nvidia_agp
modprobe -r agpgart
```

After you've got this all cleaned up, follow the instructions here:
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29)

---

### Post by Malpin on 2005-11-03
I tried that, no luck

---

### Post by RAOF on 2005-11-03
Have you tried:
```

sudo apt-get install linux linux-k7 nvidia-glx
sudo nvidia-glx-config enable

```
(you can drop the "linux-k7" if you haven't installed a kernel different from the default i386 one)?  And then if that doesn't work
```

sudo dpkg-reconfigure xserver-xorg

```
selecting the "nvidia" driver, and making sure all the other options are correct?

---

