---
title: "Openoffice problem with graphics."
date: 2009-05-30
forum: General Help
---

### Post by xavierp94 on 2009-05-30
I've recently have been using openoffice after enabling the 180 driver for my Nvidia graphics card I have noticed some problems under openoffice. Under a select amount of themes I have noticed bad corruption of icons disappearing, going away, flying off screen, etc. I have included some screen shots of the themes that I have tested.
 [http://www.imagebam.com/image/302aff37404855](http://www.imagebam.com/image/302aff37404855)
 [http://www.imagebam.com/image/dfcd8037404857](http://www.imagebam.com/image/dfcd8037404857)
 [http://www.imagebam.com/image/8fc8e637404859](http://www.imagebam.com/image/8fc8e637404859)
Architecture: i386
DistroRelease: Ubuntu 9.04
NonfreeKernelModules: nvidia
Package: openoffice.org-core 1:3.0.1-9ubuntu3
ProcEnviron:
 PATH=(custom, no user)
 LANG=en_US.UTF-8
 SHELL=/bin/bash
SourcePackage: openoffice.org
Uname: Linux 2.6.28-11-generic i686

Is there any solutions?

---

### Post by blueridgedog on 2009-05-30
I have had the same issue, but generally have ignored it as it has not impacted my use of the programs.  The most common annoyance is the "rollover" effect leaves the icon invisible.

---

### Post by xavierp94 on 2009-05-30
> **blueridgedog said:**
> I have had the same issue, but generally have ignored it as it has not impacted my use of the programs.  The most common annoyance is the "rollover" effect leaves the icon invisible.
Same thing I get.

---

### Post by blueridgedog on 2009-05-30
> **xavierp94 said:**
> Same thing I get.

I used it as-is for my last to classes in grad school and have had no functional issues.  Actually, I am glad that the effort was put into the workings of the application, perhaps mildly at the expense of the eye candy.

---

### Post by Soul-Sing on 2009-05-31
when using tango icons[COLOR="Red"](example[/COLOR])please install also the openoffice.org-style-tango package.

general default:
```
sudo apt-get install openoffice.org-style-human
```

```
sudo apt-get install openoffice.org-style-*
```

But i think it is a problem with X....

---

### Post by xavierp94 on 2009-05-31
> **leoquant said:**
> when using tango icons[COLOR=Red](example[/COLOR])please install also the openoffice.org-style-tango package.

general default:
```
sudo apt-get install openoffice.org-style-human
``````
sudo apt-get install openoffice.org-style-*
```But i think it is a problem with X....
So everytime I switch my theme I need to do this?
I did that right at this moment and it still hasn't worked.

The following link it a bug the deeply fits my description of the situation.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/253844]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/381981")

---

### Post by Soul-Sing on 2009-05-31
> So everytime I switch my theme I need to do this?

No its random, soms theme's needs this.

I googled around and didn't found a straight answer....(sorry)

---

### Post by blueridgedog on 2009-05-31
Well, there arn't that many:

```
 sudo apt-get install openoffice.org-style-
openoffice.org-style-andromeda   openoffice.org-style-hicontrast
openoffice.org-style-crystal     openoffice.org-style-human
openoffice.org-style-default     openoffice.org-style-industrial
openoffice.org-style-galaxy      openoffice.org-style-tango
```

And you can select the package you want in preferences, but it still has the slight bug we have been talking about.  Still a great application.

I just did sudo apt-get install openoffice.org-style-* and will try each set to see if any act better.

---

### Post by roman_platonov on 2009-05-31
Not good solution is in deinstalling openoffice-gnome. After that buttons and fields artefats was gone...

---

### Post by xavierp94 on 2009-05-31
The icons problem was completely fixed with downloading the 180.51 driver and installing it from the Nvidia website, but I'm still having the problem with the text on the text document not appearing till I scroll the page. I'll post a screen shot later.

---

### Post by Soul-Sing on 2009-05-31
> **xavierp94 said:**
> The icons problem was completely fixed with downloading the 180.51 driver and installing it from the Nvidia website, but I'm still having the problem with the text on the text document not appearing till I scroll the page. I'll post a screen shot later.

Good job, a X problem/driver issue though...
Hmmm nvidia is a bit struggling lately.

---

### Post by blueridgedog on 2009-05-31
I am still at 177 and everything else works great...so I am reluctant to mess with it.

---

### Post by xavierp94 on 2009-05-31
> **blueridgedog said:**
> I am still at 177 and everything else works great...so I am reluctant to mess with it.
Wait, I realized that I installed the wrong driver! I installed the Nvidia 8 Series when my computer is a Nvidia 8M Series. It working better now! Only thing that annoys me is that every time I turn on the pc a Nvidia logo pops up just before the main screen. lol

---

### Post by Soul-Sing on 2009-05-31
> **xavierp94 said:**
> Wait, I realized that I installed the wrong driver! I installed the Nvidia 8 Series when my computer is a Nvidia 8M Series. It working better now! Only thing that annoys me is that every time I turn on the pc a Nvidia logo pops up just before the main screen. lol

```
gksudo gedit etc/X11/xorg.conf
```

Option      "NoLogo" "True"

Section "Device"
	Identifier	"Videocard0"
	Boardname	"nvidia"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Option		"NoLogo" "True"

:)

---

### Post by xavierp94 on 2009-06-01
> **leoquant said:**
> ```
gksudo gedit etc/X11/xorg.conf
```Option      "NoLogo" "True"

Section "Device"
    Identifier    "Videocard0"
    Boardname    "nvidia"
    Busid        "PCI:1:0:0"
    Driver        "nvidia"
    Option        "NoLogo" "True"

:)
What do I do if it is blank?

---

### Post by Soul-Sing on 2009-06-01
your xorg.conf?

---

### Post by Soul-Sing on 2009-06-01
```
gksudo nautilus
```

navigate to: etc/X11/xorg.config

---

### Post by xavierp94 on 2009-06-02
> **leoquant said:**
> ```
gksudo nautilus
```navigate to: etc/X11/xorg.config
It's  /etc/X11/xorg.config

---

