---
title: "Plymouth doing nothing?"
date: 2010-12-23
forum: Desktop Environments
---

### Post by VirusCollector on 2010-12-23
Hello, I'm using Xubuntu 10.10, with 2.6.35-24-generic kernel. I'm 64-bit. If it helps at all, I'm using xorg-edgers, but that doesn't seem to mean anything here.

My issue is that Plymouth is doing absolutely nothing on boot. I know this from using bootchart and seeing that Plymouth launches itself three times, but not seeing anything every boot. The only splash I do see is after I log in, the mouse thing, but that's XFCE.

So, how can I either remove Plymouth entirely, get it working, or find a better splash program? The reason why I ask how to get rid of Plymouth is because it may be entangled in some things that apt-get purge wouldn't fix.

---

### Post by garvinrick4 on 2010-12-23
> **VirusCollector said:**
> Hello, I'm using Xubuntu 10.10, with 2.6.35-24-generic kernel. I'm 64-bit. If it helps at all, I'm using xorg-edgers, but that doesn't seem to mean anything here.

My issue is that Plymouth is doing absolutely nothing on boot. I know this from using bootchart and seeing that Plymouth launches itself three times, but not seeing anything every boot. The only splash I do see is after I log in, the mouse thing, but that's XFCE.

So, how can I either remove Plymouth entirely, get it working, or find a better splash program? The reason why I ask how to get rid of Plymouth is because it may be entangled in some things that apt-get purge wouldn't fix.
If you remove plymouth look what else is broken below!!!!
```
rick@rick-laptop:/$ aptitude show plymouth
Package: plymouth                        
State: installed
Automatically installed: no
Version: 0.8.2-2ubuntu8
Priority: required
Section: x11
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 483 k
Depends: libc6 (>= 2.8), libdrm-intel1 (>= 2.4.9), libdrm-nouveau1 (>=
         2.4.21-1), libdrm-radeon1 (>= 2.4.17), libdrm2 (>= 2.4.3), libplymouth2
         (= 0.8.2-2ubuntu8), upstart-job, udev (>= 149-2), mountall (>= 2.0),
         initramfs-tools
Recommends: plymouth-theme-ubuntu-text | plymouth-theme
Conflicts: usplash
Breaks: gdm (< 2.29.1-0ubuntu4), kdm (< 4:4.4.2-0ubuntu6),
        lubuntu-plymouth-theme (<= 0.4), ubuntustudio-plymouth-theme (<= 0.38),
        xubuntu-plymouth-theme (< 10.04.4)
Description: graphical boot animation and logger - main package
 Plymouth is an application that runs very early in the boot process (even
 before the root filesystem is mounted!) that provides a graphical boot
 animation while the boot process happens in the background.

rick@rick-laptop:/$ 

```

---

### Post by VirusCollector on 2010-12-23
Seriously? Why does GDM *depend* on Plymouth? Can't it get along fine without it?

Anyway, it turns out that I was just being stupid, so this isn't important anymore.

---

### Post by garvinrick4 on 2010-12-23
The problem most likely is that your graphic drivers do not hit before ureadahead and mountall packages hit so you do not get splash. This bit of code will make drivers hit first:
```
sudo -i 
``````
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash 
update-initramfs -u 

``````
exit
```
#It was a bug at one time and this is the maintainers code from launchpad and it works.

---

### Post by VirusCollector on 2010-12-23
If Plymouth really isn't messed up, will this mess anything else up or will it simply make my splash come up faster? Because that would be really cool.

---

### Post by garvinrick4 on 2010-12-23
> **VirusCollector said:**
> If Plymouth really isn't messed up, will this mess anything else up or will it simply make my splash come up faster? Because that would be really cool.
It just makes your graphic drivers come in earlier before mountall can start mounting install. That is all it does, makes plymouth splash screen work. If you want to know how to
change the splash screen let me know, their are about 5 different graphical themes.

---

