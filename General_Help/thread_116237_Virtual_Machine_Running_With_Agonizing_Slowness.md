---
title: "Virtual Machine Running With Agonizing Slowness"
date: 2006-01-12
forum: General Help
---

### Post by kenquad on 2006-01-12
Hi:

I posted this to a previous thread but no respone, so thought I'd try a new one.  I've used qemu (compiled with kqemu accelerator) to create a virtual machine on my Kubuntu Breezy box, running Win2k for some programs my work requires.  However, the Win2k system runs with absolutely incredible slowness--as in 5 seconds to load a right-click menu....  It's taking up 90% CPU and 60% RAM on my 1.3 Ghz 256 MB PIII system.

Also, I cannot access my network from the virtual machine.  I'd appreciate any help.  If I can't find a way to fix this, I may have to regretfully regress back to the *other* excuse for an operating system.

Thanks in advance for any ideas

---

### Post by kenweill on 2006-01-12
256 mb of memory is not enough.

I got the same problem before with 256 mb. Solved after adding another 512 mb of memory.

I'm currently running a virtual machine using VMware Player, installed Windows XP in the virtual machine.

About connecting to the network, I created 2 Virtual Adapter. Windows XP detected and installed 2 Network Adapter. The first was created to accept DHCP, from the connection from the internet. The other one was assigned with a static ip address to connect to my LAN.

I really think 256 mb is not enough. The memory that will now be the total allocated memory of Ubuntu(Linux) + the memory allocated by Windows(in the Virtual Machine).

---

### Post by Chris Tucker on 2006-01-12
Yikes! have you tried vmware player? theres a thread in the customization tips/tricks section. i run it on my laptop (sempron 3000+) (1.8ghz) 512 mb ram, and XP in the virtual machine, i find it exceptionally fast, it doesnt even kick my cpu stepping up from 800mhz to a higher step unless i do something cpu intensive. the only gripe i have is 3D in the virtual machine is a royal pain. this doesnt affect me right now, as my laptop doesnt have 3D in linux.. but i have access to two machines that have 3D support that i would like to be able to use.

---

### Post by kenquad on 2006-01-12
Thanks, people.  I thought RAM might be the issue and fortunately am in a position to upgrade, which I will do immediately.  On VMware Player, I have the program and have installed the RPM via Alien, but can't figure out how to get it started.  I also wasn't sure it would work for booting a partition created with qemu.

---

### Post by kenweill on 2006-01-12
[QUOTE=kenquad]Thanks, people.  I thought RAM might be the issue and fortunately am in a position to upgrade, which I will do immediately.  On VMware Player, I have the program and have installed the RPM via Alien, but can't figure out how to get it started.  I also wasn't sure it would work for booting a partition created with qemu.[/QUOTE]

It would be better if you download vmware player in .tar.gz format. And follow the manual in the Ubuntu Wiki.

Converting an rpm through alien doesn't always work.

---

### Post by kenquad on 2006-01-12
Could you give me the exact link to the wiki article?  I searched an couldn't find it.

---

### Post by humanity_to_others on 2006-01-12
[https://wiki.ubuntu.com/VmWare](https://wiki.ubuntu.com/VmWare)

---

### Post by kenquad on 2006-01-12
That links to instructions for using VMware proper--not the free product.  Are there instructions for the player?

---

### Post by kenquad on 2006-01-12
OK, I actually found the wiki article on installing the player, but I need some help using it.  *Will* it make use of my pre-configured qemu partition (.img) loaded with Win2k?

---

### Post by Chris Tucker on 2006-01-12
possibly, but its best to use a vmdk.. for more in depth questions and answers visit the thread in customization tips and tricks.

---

### Post by kenquad on 2006-01-13
Okay, it's set up and everything but networking is going great.  vmplayer vs. Qemu is just no comparison speedwise.  Glad VM put out the free product!  Thanks for the help.

---

