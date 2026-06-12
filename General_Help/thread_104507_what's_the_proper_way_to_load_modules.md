---
title: "what's the proper way to load modules?"
date: 2005-12-16
forum: General Help
---

### Post by yhotg on 2005-12-16
hi,  :P

i mean if i want to load a module at boot up, where i need to write "modprobe <module>"
i tried to write "dazuko" on /etc/modules but nothing happens (there's a problem loadin dazuko after a module called capability is loaded, but i can't find the place where tell to kubuntu to load dazuko before loading capability)
so,
any idea what's the file i am looking for?
thank u very muchwhat the proper way to load modules

---

### Post by stuporglue on 2005-12-16
Do you need it loaded at boot time, or just soon afterwards? If you need it at boot time (eg. a network card, HD, etc.), then you need to rebuild your initrd. It's not very hard. 

This tutorial focuses on OldWorld Macs, but applies to any Ubuntu system, I think. I've used the same method on x86 computers before. 

[http://stuporglue.org/initrd.php](http://stuporglue.org/initrd.php)

---

### Post by mlomker on 2005-12-16
[QUOTE=stuporglue]Do you need it loaded at boot time, or just soon afterwards? If you need it at boot time (eg. a network card, HD, etc.), then you need to rebuild your initrd. It's not very hard. 
[/QUOTE]

Getting it into initrd is one thing but how do you convince the kernel to load it earlier?  My understanding is that initrd is simply a filesystem that allows the kernel to access drivers before the main filesystem is mounted...it doesn't by itself call anything.

The capability module is a posix security module that is already in the initrd.  Normally you'd just add the module to /etc/hotplug/blacklist and then manually load it in /etc/modules, but that might not work in this case if the module loads before the root partition is even mounted.

---

### Post by MartinG on 2005-12-16
[QUOTE=yhotg]i tried to write "dazuko" on /etc/modules but nothing happens (there's a problem loadin dazuko after a module called capability is loaded, but i can't find the place where tell to kubuntu to load dazuko before loading capability)
so,
any idea what's the file i am looking for?
thank u very muchwhat the proper way to load modules[/QUOTE]

I used a quick and dirty workaround for this one.  Create a script called "dazuko" in /etc/init.rd, containing the following:

```
#! /bin/sh

rmmod capability && modprobe dazuko && modprobe capability
```

Then create a symlink to it in rc2.d, and rename it to S99dazuko.

This will unload the capability module, load the dazuko module, and reload capability.  I think there ought to be a more elegant solution that doesn't involve unloading capability at all, but this is simple and it works (for me).

---

### Post by wylfing on 2005-12-16
That is a fairly clever solution. I don't know of a way to guarantee the order modules are loaded at boot time, but I would be interested to learn it if anyone knows it.

---

