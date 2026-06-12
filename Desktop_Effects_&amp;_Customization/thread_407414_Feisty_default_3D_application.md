---
title: "Feisty default 3D application"
date: 2007-04-12
forum: Desktop Effects &amp; Customization
---

### Post by bbalazs on 2007-04-12
Hi All,

I've been using Ubuntu since our company has deployed linux in production...
I have tried several distributions, and frankly Ubuntu is one of the best ones.

Yesterday I installed mandriva one 2007, and the default 3d (aixgl or something...) looks quite good. Really good!

Does anyone have information about if it is planned to pack something like that into the new Ubuntu 7.04 Feisty by default? I tried beryl, but the screen switched off (or I don't know), and I had to restrart the X from console.... so what 3d system do you suggest, and which is the easiest to install, configure and use?

Thanks,
Balazs from Hungary

---

### Post by Spr0k3t on 2007-04-12
It really depends on your hardware and if the chipset is supported.  Both Compiz and Beryl are maturing quite nicely, but most will say that out of the two Beryl is more stable.  In Feisty, you can enable Compiz by going to System - Preferences - Desktop Effects.

So, what are the specifications of your system?  And more importantly, what chipset is the graphics card?

---

### Post by bbalazs on 2007-04-12
OK, I see.

Do you have any experiences using beryl under VMware server or workstation?

There are only several very essential drivers available. Mandriva doesn't let me use its tool under vmware server.

---

### Post by Spr0k3t on 2007-04-12
Never have.  Most of my systems are either real or some vague remote system.  I'm not sure it would work under a VMware subsystem.

---

### Post by bbalazs on 2007-04-12
Thanks. My laptop is a Dell 610 one, it has i915 chipset, I use it only for work and I agree with you, VMware doesn't support especially the graphic system, nevertheless I'll take a try under VMware with Ubuntu Feisty.

Later I'll post my remarks.

---

### Post by rcmullins on 2007-04-12
Correct me if I am wrong but Edgy Eft had AIXGL already installed.  I installed Beryl straight from command line and it works great (except for the 'rain' effect).

I am in the middle of upgrading to Feisty Fawn 7.04, are you saying my beryl installation won't work?

---

### Post by bbalazs on 2007-04-13
you're right mate, aixgl is bundled, but under vmware when beryl tries to configure itself just a white screen comes as if it is freezed.
i'll take a try under the new vmware workstation 6, it might help.
when pressing ctrl+c several times a message comes up in console: dbus error os something.
what is dbus used for in this case?   

have a nice day,
b

---

### Post by igknighted on 2007-04-13
> **bbalazs said:**
> you're right mate, aixgl is bundled, but under vmware when beryl tries to configure itself just a white screen comes as if it is freezed.
i'll take a try under the new vmware workstation 6, it might help.
when pressing ctrl+c several times a message comes up in console: dbus error os something.
what is dbus used for in this case?   

have a nice day,
b

Thats just under VMware, because VMware virtualizes ALL your hardware.  The "virtual videocard" it shows to the client OS does not support 3d, so no matter what your card is capable of, the client OS cannot have 3d.  There is supposedly a patch for Qemu if you search in the cafe to enable 3d if your really want to try beryl on a virtual machine.  However, once you install it to a real computer it will work with no issues.

---

