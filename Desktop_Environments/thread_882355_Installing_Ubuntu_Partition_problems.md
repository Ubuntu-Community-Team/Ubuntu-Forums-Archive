---
title: "Installing Ubuntu: Partition problems"
date: 2008-08-06
forum: Desktop Environments
---

### Post by shesk on 2008-08-06
Hey,
I'm a first time user with ubuntu and am trying to install version 8.04 for an intel comp.  I accidentally installed the standard version on a partition instead.  Can any help me with the new install so that it overwrites the old Ubuntu install without messing up any other partitions.  I have windows xp on the first partition and 8.04 standard on the second. 

thanks

---

### Post by arubislander on 2008-08-06
Hi,

Maybe you could tell me what the difference is between the version you wanted to install and the one you installed instead? Afaik there is no 'standard' version of Ubuntu 8.04, there is the desktop version in two processor flavours (32 bit and 64 bit) and there is the server edition, and the alternate disk...

---

### Post by tuxxy on 2008-08-06
I think he means standard as 32bit?

---

### Post by arubislander on 2008-08-07
I suppose...,

Well it doesn't matter anyhow. The way to install the desired Ubuntu version over an existing one is to run the installer and choose manual at the partioning screen. then delete the partition where Ubuntu is on (make a note of which one that is beforehand, you really do not want to delete the wrong partition!!!) create it again and set / as the mountpoint and install.

Of course it is better to create a seperate /home partition while you're at it, but I'm sure there are other threads out there that explain how to do this.

---

### Post by cdtech on 2008-08-07
arubislander is correct by saying "choose manual at the partioning screen" and the installer will overwrite any existing data on that partition.

---

### Post by shesk on 2008-08-07
Thanks guys, yeah i meant 32bit as standard and i meant to install 64bit.  I tried to manual install but i dont know how to create a root directory.

---

### Post by arubislander on 2008-08-10
Where exactly are you getting stomped?

---

