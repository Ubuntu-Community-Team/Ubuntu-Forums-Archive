---
title: "New nVidia beta driver released"
date: 2008-12-14
forum: General Help
---

### Post by loomsen on 2008-12-14
Hello everyone.

nVidia released a new version of its beta driver yesterday, 
Version: 180.16
It includes a new API, and, for me, it fixes all the major annoiances of the last couple of weeks.
However, it is still beta, and you'll notice it. Mine for instance sometimes seems to run hot for any reason I wasn't able to find yet. So you should have an eye on your thermal monitor. 

[color=red]
NOTE: DO NOT run beta drivers if you don't know what you're doing! These are beta and therefore might include some bugs which weren't noticed yet, or behave abnormal and so on. 
If everything works fine for you, don't use it. If not I think you should have a little bit of experience with your video device already[/color]

You can get it from command line with
[color=red]Arch=amd64:[/color]
```

wget ftp://download.nvidia.com/XFree86/Linux-x86_64/180.16/NVIDIA-Linux-x86_64-180.16-pkg?.run
```
(should be 3 files)

[color=red]Arch=x86:[/color]
```
wget ftp://download.nvidia.com/XFree86/Linux-x86/180.16/NVIDIA-Linux-x86-180.16-pkg?.run
```
(2 files)


NOTE: This will download all available, usually 3, driver pkges to your current working dir. Usually you'll only need one of them, if I remember right the higher numbers mean higher compatibility. So try and run pkg0 first, if it fails run pkg1 and if this one should fail as well run pkg2.

I assume you know what you're doing so I won't explain how to get rid of your old install or install this one. Just wanted to point at the update.


For further information visit the nvnews forum where drivers get announced:
[Current NVIDIA Linux graphics driver releases](http://www.nvnews.net/vbulletin/showthread.php?t=122606)
[180.16 (BETA) for Linux x86/x86-64 released](http://www.nvnews.net/vbulletin/showthread.php?p=1873716)

---

### Post by obsrv on 2008-12-20
I need a HTTP server to download this driver from. I cannot use ftp protocol. My ISP blocks it.

---

### Post by .arean on 2008-12-22
> **obsrv said:**
> I need a HTTP server to download this driver from. I cannot use ftp protocol. My ISP blocks it.

A new version was released a couple of days ago.

32-bit
```
http://us.download.nvidia.com/XFree86/Linux-x86/180.17/NVIDIA-Linux-x86-180.17-pkg1.run
```
64-bit
```
http://us.download.nvidia.com/XFree86/Linux-x86_64/180.17/NVIDIA-Linux-x86_64-180.17-pkg2.run
```

---

### Post by dwarness on 2008-12-22
I'm curious.  Installing this package, would it automatically configure X to use them, or would these new drivers show up under System->Administration->Hardware Drivers, and I would have to select them?  If it doesn't show up there, how would I make it show up there?

---

### Post by elninja on 2008-12-22
> **obsrv said:**
> I need a HTTP server to download this driver from. I cannot use ftp protocol. My ISP blocks it.

Also, you might want to try calling your ISP and seeing if they'll remove that block for you. I've done that for the ISPs I've had where SMTP was blocked.

---

### Post by IanW on 2008-12-23
Actually, Nvidia have up-issued again. Current driver is now [180.18](http://www.nvnews.net/vbulletin/showthread.php?t=125134).

---

### Post by Usufruct on 2008-12-23
Not sure if I'm even going to bother with the new nvidia beta.  Maybe if I get bored tomorrow.  180.06 solved so many issues, I may just wait for the release.

---

### Post by loomsen on 2008-12-29
Hi.

Maybe we should collect some experiences with different setup/drivers?

Card: 8600M GT
Driver: 180.11.02
Performance: 3/5

or so... 

The 180.18 for instance doesnt work too well for me (thermal monitor shows up to 98°C)

---

### Post by mikull on 2008-12-30
no big deal.
thnaks for the heads up anyway jack! :@

---

### Post by Usufruct on 2008-12-30
Yeah I did end up getting bored and installing a newer beta driver.

Card: nVidia Quadro FX 350M (7300LE)
Driver: 180.17 (64-Bit)
Performance: 4/5

Not noticing a whole lot of difference between this and the 180.06 driver, but that's just me.

---

### Post by Macr237 on 2009-01-14
Now they have [180.22]("ftp://download.nvidia.com/XFree86/Linux-x86/180.22/") released. I haven't loaded it yet to see what differences, but I have been happy with 180.17.

---

### Post by loomsen on 2009-01-14
I have downloaded and installed it some days ago. Did not noticable change performance, tho I'll probably switch back to the opengl3.0 driver which I liked better somehow. Can't tell exactly but for my computer it just seems to suit somewhat better.

---

### Post by HunterK on 2009-01-14
> **Macr237 said:**
> Now they have [180.22]("ftp://download.nvidia.com/XFree86/Linux-x86/180.22/") released. I haven't loaded it yet to see what differences, but I have been happy with 180.17.

I tried that driver with my 6800GT and it really messed things up for me.  Clicking on a window to drag it resulted in a split second pause.  Firefox scrolling was horrible.

180.18 work great for me!

---

### Post by Zakhafr on 2009-01-14
Do you know, by any chance, if 180.22 will be on backports repositories for Intrepid... or if someone has it on some kind of PPA repo (it has already been packaged for Jaunty : [https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180]("https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180"))

---

### Post by loomsen on 2009-01-26
You can still use the jaunty pkges in intrepid.

jaunty is a hint that this version isnt stable yet.

Do this to download all available binaries to a folder in your home directory:

[color=green]NOTE the links are for the amd64 version. You'll find the pkges for the 32bit version [ HERE, on the right side, where resulting binaries are listed.](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/180.22-0ubuntu2/+build/832063)[/color]

Open a terminal, type (or simply copy n paste):
```


mkdir src && mkdir nvidia && cd src/nvidia

wget http://launchpadlibrarian.net/21067512/nvidia-180-kernel-source_180.22-0ubuntu2_amd64.deb http://launchpadlibrarian.net/21067509/nvidia-180-libvdpau_180.22-0ubuntu2_amd64.deb http://launchpadlibrarian.net/21067508/nvidia-180-modaliases_180.22-0ubuntu2_amd64.deb http://launchpadlibrarian.net/21067510/nvidia-glx-180_180.22-0ubuntu2_amd64.deb http://launchpadlibrarian.net/21067511/nvidia-glx-180-dev_180.22-0ubuntu2_amd64.deb

```
Make sure u copy the whole lines to get all (5) available binaries
When done you can install the pkges with:

```

sudo dpkg -i nvidia-180-kernel-source_180.22-0ubuntu2_amd64.deb nvidia-180-libvdpau_180.22-0ubuntu2_amd64.deb nvidia-180-modaliases_180.22-0ubuntu2_amd64.deb nvidia-glx-180_180.22-0ubuntu2_amd64.deb nvidia-glx-180-dev_180.22-0ubuntu2_amd64.deb

```

Reboot your computer, and if you disable the bootsplash you should be able to read a line telling you that DKMS compiled the nvidia kernel module version 180.22 for your kernel.

You can also type 
```

cat /proc/driver/nvidia/version

```
into a terminal to check which version is installed.

---

