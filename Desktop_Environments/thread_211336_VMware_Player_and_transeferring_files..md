---
title: "VMware Player and transeferring files."
date: 2006-07-08
forum: Desktop Environments
---

### Post by frup on 2006-07-08
I've just downloaded the VMware player lastnight and have managed to make a few Virtual OS's ... i've been searching on google if you can transfer files between guest and host. It looks like its possible according to mailing lists etc but i cant actually find the info.

Also the clipboard doesnt transfer between the two OS's either. Is this just part of VMware Player to increase Workstation ownership? or can I do something about this?

EDIT: i've thought about it and figured maybe i could set up a samba share.. and it shows ubuntu and the guest OS... but its asking for a password :(... time to search the forum. unless someone wants to give me the info :)

---

### Post by bartbes on 2006-07-08
There now is a free VMWare Server, which is about the same as Workstation except for that you can run Virtual Machines over the network and internet. Probably you can configure that there.

---

### Post by frup on 2006-07-08
well i've managed to get a network between the host and guest :)
just had to set a samba password for my ubuntu computer :)
its all working good now... copy and paste though :S lol but its not that important... VMware server is in the repositries?

---

### Post by bartbes on 2006-07-08
Not that I know of...
But it is here:
[VMWare Server](http://www.vmware.com/products/server/)

---

### Post by Dearhell on 2006-07-08
I have installed recently that VMWare server and works fine, you only have to follow the instructions through the installation menu, it's really easy

The only thing you have to do it's install xinetd in order to make a properly installation

---

### Post by frup on 2006-07-08
hmm well player works and using Qemu i can make drives and i understand how to edit the .vmk files so i'll stick with that until they release the final version. lol

---

