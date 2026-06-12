---
title: "Making a LiveCD From Scratch"
date: 2009-05-03
forum: General Help
---

### Post by gamewolf on 2009-05-03
I love live cds. I have tried many different Debian based live cds, but I am just not satisfied with the programs included. Many live cds such as knoppix are just getting outdated and the kernels are old.

So I am wanting to just create my own from scratch. I know this is obviously a daunting task, but I have the patience and I believe I know enough about linux to be able to do it.

I have been doing research. I have downloaded the sources for squashfs and unionfs as well as the latest kernel. I have made a very minimal debootstrap environment which I will soon customize with my own programs, etc.

I do have a couple a questions. What is the knoppix system that automatically detects hardware and drivers? Is is something that the knoppix developers created or is it something I can download? The other questions is how would I go about creating a splashscreen on boot? I have looked in the ubuntu desktop iso, but the isolinux folder contents are all compiled.

If someone could help me get started I would really appreciate it. Thanks!

---

### Post by blazemore on 2009-05-03
Have you tried LinuxFromScratch?
Or you got get the Ubuntu Minimal installation, and build up from there. You could recompile the kernel, install your own apps and artwork, and then use remastersys to create the .iso

---

### Post by gamewolf on 2009-05-03
I looked into remastersys and looks good! I installed it and will probably use it for creating the iso.

I looked into Linux From Scratch awhile back and while it looks good, it's not quite what i'm looking for. I believe the only thing I need now is the Knoppix boot system for automatically detecting hardware.

---

### Post by gamewolf on 2009-05-03
Ok, I found the knoppix sources at [http://debian-knoppix.alioth.debian.org/sources/](http://debian-knoppix.alioth.debian.org/sources/)

I am not sure what I need to use the hardware detection system. Any tips? Thanks.

---

### Post by gamewolf on 2009-05-03
Any ideas?

---

### Post by delcypher on 2009-05-03
To make your own ubuntu live cd/dvd customised with whatever you want then check out the [Ubuntu customisation kit (UCK)]("http://uck.sourceforge.net/")

I've tried it out and have made some nice discs. You need an ubuntu live disc to start out with.

---

### Post by gamewolf on 2009-05-03
Well I am wanting to have a different desktop enviroment. LXDE wasn't available in the repos for UCK.

---

