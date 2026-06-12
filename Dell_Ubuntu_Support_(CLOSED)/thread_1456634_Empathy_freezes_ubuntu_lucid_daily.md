---
title: "Empathy freezes ubuntu lucid daily"
date: 2010-04-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by erny on 2010-04-17
When starting Empathy, this is at least what happens.

My environment is:
 * Lucid desktop-amd64 install
 * Dell XPS M1330
 * on battery
 * near to standard setup, but with libia32
 * VMWare-Server 2.0.2 (had problems compiling this, so I applied custom patches) (vmnet and vsock didn't compile with kernel 2.6.32 kernel includes)
 * virtualbox 3.1.6

I suppose, that it may have to do with VMWare.

Regards.

---

### Post by Mountaineer on 2010-05-11
Everyone in this bug seems confident it's VMWare's vmnet kernel module:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/495577](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/495577)

Solution?
Uninstall VMWare.  As I need it for work, that's not a good option for me. :(

---

### Post by erny on 2010-05-13
I just stop vmware (/etc/init.d/vmware stop) and don't tell it to start at boot (update-rc.d -f vmware remove). 

I'll be looking for alternatives, and it seems to me that qemu (with or without kvm) will do it for me.

Thanks for your reply.

---

### Post by Mountaineer on 2010-05-13
I used the stop command once.
Several reboots on (and apt-get upgrades) everything seems to be operating fine.
I've also disabled compiz so I don't know what's different.

But I've got a VM open right now and I'm sending and receiving messages with empathy just fine. <shrug>

---

