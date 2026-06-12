---
title: "stopping/replacing/unloading modules"
date: 2005-01-21
forum: Desktop Environments
---

### Post by machiner on 2005-01-21
So, I went to modprobe.d and opened the alias file (the big one) and I added:

alias sound-slot-0 nvsound
alias eth0 nvnet 

I didn't find any listing of forcedeth or i810_audio

So -- my question is -- do I have multiple modules loaded that are doing the same thing? I have sound and I am on the net so I'm working fine, but I installed the nforce drivers and I want to take advantage.

SO - how do I "stop" or "unload" a module and replace it with what I want.

Like I said, I added 2 alias lines already, rebooted and fine...but what am I using?

THanks

Oh - I get another nickle here!

---

### Post by machiner on 2005-01-21
What I think I want to do is:

add my 2 new alias lines to /etc/modutils/aliases

That make sense?

But where is "forcedeth" listed so I can comment it out? And the i810_audio listing as well?

grazzi

---

### Post by shmonkey on 2005-01-21
I'm not quite sure exactly what you are trying to do here. 

If you don't want to use the forcedeth module, first do lsmod to see if it is loaded, then

 sudo rmmod -f forcedeth
 sudo update-modules

---

### Post by machiner on 2005-01-21
Exactly what I was looking for.

Thanks

---

### Post by fourhead on 2005-11-04
Hello,

I'm trying to do the same - replace forcedeth with nvnet. But to no avail. I tried what you said, rmmod forcedeth, update-modules, then added 'alias eth0 nvnet' to /etc/modprobe.d/aliases and rebooted. Still, both modules are loaded and of course forcedeth is used.

From another thread, I tried putting forcedeth to /etc/hotplug/blacklist - but it still gets loaded. I tried adding nvnet to /etc/modules to auto-load it at the very beginning of the boot - but still forcedeth is used. Then I simple mv'ed forcedeth.ko from /lib to another dir - but STILL it is used!?

How the hell can I get rid of forcedeth (I want to get rid of it as much as someone can want to get rid of something!!) and auto-use nvnet instead?

BTW, when I manually load nvnet and use it, it works fine, and the upload speed to my server magically rices to 8-10MB/s instead!


Tom

---

### Post by Elvari on 2005-11-16
I'm having similar problem with Broadcom networkcard. It uses tg3 module by default, and I want to use bcm5700 instead. But after boot both are listed by lsmod. And tg3 is the one in use.

---

### Post by mael on 2005-11-25
this worked under breezy-server:

echo nvnet >> /etc/mkinitramfs/modules
cd /boot
mkinitramfs -o initrd_nvnet.img
ln -fs initrd_nvnet.img initrd.img

:)

now even WoL is working (didn't work with forcedeth)
i'm using a Asus K8N-E mobo
but i didn't try a Gbit connection

---

