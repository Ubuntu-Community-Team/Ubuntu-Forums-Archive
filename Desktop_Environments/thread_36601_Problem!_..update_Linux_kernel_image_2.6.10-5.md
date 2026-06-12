---
title: "Problem! ..update Linux kernel image 2.6.10-5"
date: 2005-05-23
forum: Desktop Environments
---

### Post by userone on 2005-05-23
Today! I reload my synaptic an receive update some message for update “Linux kernel image for version 2.6.10 on 386”. Then I mark for upgrade kernel and wait for download file. After finished dowload  and reboot my Kubuntu. 
So sad.... My linux can't start KDM and turn error messages about problem X.org not compatable with new kernel.

........................................................................................................................
FATAL : Module NVIDIA not found
(EE) NVIDIA(0) : Failed to load th NVIDIA kernel module!
(EE) NVIDIA(0) : *** Aborting ***
(EE) Screen(s) found, but none have a usable configurator
. . .
. . .
XIO : Fatal IO Error 104 (Connettion reset by peer) on X Server “:0.0”
        after 0 requests (0 know processed) with 0 events remaining
........................................................................................................................

Can anyone help me?

many many thank you.  :neutral:

---

### Post by tread on 2005-05-24
Get 2.6.10-5-restricted also (I don't remember the exact package name). The nvidia drivers are in restricted, and changing the kernel means you have to update your drivers too.

---

### Post by !nkubus on 2005-05-24
I don't think that the drivers are there yet , or maby i do not see it.

---

### Post by sancho on 2005-05-24
It looks like you have upgraded your kernel.  Everytime you upgrade your kernel you MUST reinstall the nvidia drivers.   

If you have never done a manual install of nvidia drivers go grab yourself a beer and some tylenol. Here we go...

```

cd /usr/src
ls -lha

```
<copy and paste this output here if you need to>
the idea is to get "linux" to symnlink to the kernel source direcotry.  
if it does not link to the proper kernel folder do this.  
```

rm linux
ln -s *kernel-folder (linux-2.6,10-5)* linux

```
Once you got the linux symlink right it is time to install the nvidia drivers. 
```

wget http://download.nvidia.com/XFree86/Linux-x86/1.0-7174/NVIDIA-Linux-x86-1.0-7174-pkg1.run
chmod x NVIDIA-Linux-x86-1.0-7174-pkg1.run
./NVIDIA-Linux-x86-1.0-7174-pkg1.run

```
Follow the onscreen prompts.  It won't be able to find the drivers but it should build the drivers for you. 
Then do this..
```

nano /etc/X11/xorg.conf
look for the "device" section.  
change "nv" to "nvidia" if necessary
save and quit.  

```
Finally issue "startx" and see what happens.  

A few notes.  This assumes you are using a 32bit processor.   Also you will have to sudo a lot of those commands, in fact prolly all but the first two.  This is by no means an in depth walk through and i'm doing it all from memory but hopefully it will be enough for you to figure it out.  If you have any problems post back some errors and i will try to help you.

---

### Post by !nkubus on 2005-05-24
I'l test it tonight at home

thanks


is there a package i need to install to thave the kernel sources ?

apt-get install kernel-header ?

---

### Post by sancho on 2005-05-24
yeah i would install the linux-headers and the linux-source if they are not installed already.

---

