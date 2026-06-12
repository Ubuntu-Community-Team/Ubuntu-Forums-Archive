---
title: "networking two computers"
date: 2006-08-30
forum: Desktop Environments
---

### Post by harty83 on 2006-08-30
I need to back up my laptop because I'm reformatting.  I don't have an external.  So I want to connect my laptop to my desktop and back up my files.  I have close to 40 gigs to back up (because of VMware with Windows xp) so I really don't want to do it over my dsl but with a direct connection between teh two computers.  How do I set up a direct connection between the two using an ethernet cable?

Thanks!
Alan

---

### Post by Ramses de Norre on 2006-08-30
Or: you use a router (maybe you can use one of a friend if you don't have it your self);

or: you use a cross cable, this is an ethernet cable with a few cables that changed of place on one side of the cable, this is the only way to make a direct link with an ethernet cable.
You can buy such a cable or make one your own (it's not difficult and there are guides for it on the web).

---

### Post by AlbertTatlocksCap on 2006-08-30
Alan

You will need a crossover ethernet cable if you wish to connect them directly. If you have a hub/switch then you can use straight thro' cables.

Obviously the network settings may need tweaking in terms of IP addresses, workgroup etc 

Hope this helps

---

### Post by GarlicFish on 2006-08-30
The simplest way is with an ethernet cross-over cable (Not a regular ethernet cable) you can pick them up from most cable suppliers for a few pounds.

connect the cable to the ethernet port on both machines

set the IP address and subnet mask so they are on the same subnet:

laptop 192.168.0.1 subnet 255.255.255.0
desktop 192.168.0.2 subnet 255.255.255.0

you will not need to set the default gateway in this case.

test you can ping each machine from the other.

you should then be able to use sftp or scp to copy files between the machines.

e.g. from the laptop
sftp username@192.168.0.2

If you want to use Windows networking, you will need to take extra steps to sort out name resolution such as editing the hosts file.

---

### Post by GarlicFish on 2006-08-30
rsync is also pretty useful for taking backups

---

