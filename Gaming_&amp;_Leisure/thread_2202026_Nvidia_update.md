---
title: "Nvidia update"
date: 2014-01-27
forum: Gaming &amp; Leisure
---

### Post by MikeCyber on 2014-01-27
Hi, anyone updated with the Steam check video driver updates?
If nobody I will try later the Nvidia installer download as I've made very bad experiences with ppa etc.

---

### Post by josh17 on 2014-01-27
I tried it once a while back, and ended up needing to reinstall ubuntu afterwards -.- however I could have just gotten unlucky

---

### Post by dannyboy79 on 2014-01-28
i personally don't even trust the steam graphics driver updater myself. I always install drivers from either AMD or Nvidia's website and do just fine

---

### Post by efflandt on 2014-01-30
Since I started using Steam during beta Jan 2013 when they recommended experimental drivers for nvidia, I have been using Ubuntu nvidia-experimental-310 in 12.04, which was a 319 version and recently updated to 331.20:```
efflandt@xps8100-1204:~$ dpkg-query -l nvidia* | grep ii
ii  nvidia-319-updates                     331.20-0ubuntu0.0.1                     Transitional package for nvidia-331-updates
ii  nvidia-331-updates                     331.20-0ubuntu0.0.1                     NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                          1:0.2.44.2                              Find obsolete NVIDIA drivers
ii  nvidia-experimental-310                319.32-0ubuntu0.0.1                     Transitional package for nvidia-experimental-310
ii  nvidia-settings                        331.20-0ubuntu0.0.1                     Tool for configuring the NVIDIA graphics driver
ii  nvidia-settings-319-updates            331.20-0ubuntu0.0.1                     Transitional package for nvidia-settings
```

---

### Post by PotatoHead007 on 2014-02-02
> **josh17 said:**
> I tried it once a while back, and ended up needing to reinstall ubuntu afterwards -.- however I could have just gotten unlucky

Done that twice :p.
What i did was install the driver from [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us).
Then i used something like this: [http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html) (method 2).
That made my resolution something like 640x580, so i installed additional drivers, and that fixed it, and made my performance(games) much higher.
Try that, but backup first :P

---

### Post by MikeCyber on 2014-02-03
a ppa install once even left me with a unbootable os!

Anyway I just ran the latest 331.38 installer download from Nvidia and it worked.
I needed to build the module and use my previous (backed up) Nvidia X configuration.

sudo service lightdm stop
cd Down*
sudo ./NV*run

reboot:
nvidia-settings

if only it would always be that easy...

---

### Post by ovidiu3 on 2014-02-03
Hi

I updated the to last driver 331.38

It gave me a headache but finally installed.

but now i have a problem, playonlinux says that "Direct3D9 is not available without OpenGL."

any hint about this

i have a gtx 650 TI.

Regards

---

### Post by PotatoHead007 on 2014-02-03
Hi ovidiu3 :)

Sounds like you are missing OpenGl :P Could be mistaken though.
Try this: ```
dpkg -L libqt4-opengl
```
If that says "Package `libqt4-opengl' is not installed.", run this: ```
sudo apt-get install libqt4-opengl
```
Might just work :) Cant hurt anyway.

---

### Post by ovidiu3 on 2014-02-03
thankx for the fast reply :D awsome thing :D

i will try it as soon i will get home and give feedback.

---

### Post by PotatoHead007 on 2014-02-03
> **ovidiu3 said:**
> thankx for the fast reply :D awsome thing :D

i will try it as soon i will get home and give feedback.

Cool beans :biggrin:

---

### Post by ovidiu3 on 2014-02-03
did that and it is installed
output
root@ovidio-X58-USB3:/home/ovidio# dpkg -L libqt4-opengl
/.
/usr
/usr/lib
/usr/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu/libQtOpenGL.so.4.8.4
/usr/lib/x86_64-linux-gnu/qt4
/usr/lib/x86_64-linux-gnu/qt4/plugins
/usr/lib/x86_64-linux-gnu/qt4/plugins/graphicssystems
/usr/lib/x86_64-linux-gnu/qt4/plugins/graphicssystems/libqglgraphicssystem.so
/usr/share
/usr/share/doc
/usr/share/doc/libqt4-opengl
/usr/share/doc/libqt4-opengl/copyright
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/libqt4-opengl
/usr/lib/x86_64-linux-gnu/libQtOpenGL.so.4.8
/usr/lib/x86_64-linux-gnu/libQtOpenGL.so.4
/usr/share/doc/libqt4-opengl/LGPL_EXCEPTION.txt
/usr/share/doc/libqt4-opengl/changelog.Debian.gz



any other hint???

i installed x64 ver of the driver but i said to install x32 libraries too

---

### Post by ovidiu3 on 2014-02-03
err:wgl:has_opengl Failed to load libGL: libGL.so.1: wrong ELF class: ELFCLASS64
err:wgl:has_opengl OpenGL support is disabled.
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D9 is not available without OpenGL.

how can i indicate playonlinux to load libraries from /usr/lib32/????

---

### Post by PotatoHead007 on 2014-02-04
Ah man.... i am not sur ei know how to fix that. I will do some digging, but maybe you can try get help at the [http://www.playonlinux.com/](http://www.playonlinux.com/) forums? They know their stuff there :)

---

### Post by MikeCyber on 2014-02-04
I remember something similar ~2 years ago:
wrong ELF class: ELFCLASS64

Or, instead of editing the file ld.so.conf directly, create a file called local.conf in the subdirectory /etc/ld.so.conf.d containing just the line /usr/local/lib. That is,

Contents of /etc/ld.so.conf.d/local.conf:

/usr/lib32

Then run the sudo ldconfig -v command.
That worked but hey what year is it? 1991? Probably it would get better by sticking to the LSB... Maybe installing the LSB  would fix that?

---

### Post by ovidiu3 on 2014-02-04
i tryed to installed and it is allready installed.

i think it is because they try to use a x32 lib and i have installed an x64 lib.

but i tried on playonlinux forum too :)

thkx anyway :)

---

### Post by MikeCyber on 2014-02-04
Wine needs 32bit. If 32bit is installed, then it's not found and you should try my solution as above.

---

### Post by MikeCyber on 2014-02-10
Or a even better solution: Installing LSB seems to fix those all. At least my error:
[http://ubuntuforums.org/showthread.php?t=2204542](http://ubuntuforums.org/showthread.php?t=2204542)
seems gone. (needs some more days testing)

---

### Post by barbarah2 on 2014-02-26
I use [NVidia Driver Download Utility]("http://softwarepuppy.com/search/Nvidia.html") to update NVidia drivers. Unfortunately, I can't insert the exact link so just scroll down a little bit to find it in the list

---

