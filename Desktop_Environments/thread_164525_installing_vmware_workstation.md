---
title: "installing vmware workstation"
date: 2006-04-22
forum: Desktop Environments
---

### Post by Brando569 on 2006-04-22
im trying to install vmware and i get this:

Your kernel was built with "gcc" version "3.4.5", while you are trying to use
"/usr/bin/gcc" version "4.0.2". This configuration is not supported and VMware
Workstation cannot work in such configuration. Please either recompile your
kernel with "/usr/bin/gcc" version "4.0.2", or restart /usr/bin/vmware-config.pl
with CC environment variable pointing to the "gcc" version "3.4.5".

how can i do what the last line says? thanks.

---

### Post by jimboberella on 2006-04-23
type these at the command prompt

```
CC=gcc-3.4
```
```
export CC
```

That should so it.

---

### Post by funkyade on 2006-04-24
Trying to get VMware workstation (5.5) going but get the following error -

```
$>vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
```

vmware installed absolutely fine and I cannot for the life of me work out what is going on here!

have got gcc-3.4 installed already.

Does anybody know what is going on with this... I have vmplayer working fine, however, that is a bit useless without being able to create VMs to use with it!!!! AAAAAAAAAARRRRRRRRRRRRRRGGGGGGGGGGHHHHHHHHHH... (sorry, been banging my head on this one for hours!)

:confused:

---

### Post by jstueve on 2006-04-24
```

sudo mv /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1.vm
sudo mv /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0.vm

```

---

### Post by wylfing on 2006-04-24
You don't need VMware Workstation to create new VMs. You can do it with qemu. Read here:

[https://wiki.ubuntu.com/VMwarePlayerAndQemu](https://wiki.ubuntu.com/VMwarePlayerAndQemu)

---

### Post by kenweill on 2006-04-25
[QUOTE=funkyade]Trying to get VMware workstation (5.5) going but get the following error -

```
$>vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
```

vmware installed absolutely fine and I cannot for the life of me work out what is going on here!

have got gcc-3.4 installed already.

Does anybody know what is going on with this... I have vmplayer working fine, however, that is a bit useless without being able to create VMs to use with it!!!! AAAAAAAAAARRRRRRRRRRRRRRGGGGGGGGGGHHHHHHHHHH... (sorry, been banging my head on this one for hours!)

:confused:[/QUOTE]

Just go to the Wiki Page of Ubuntu.
Then search for VMware.
There, theres a link to installing VMware Workstation.
It was actually for Ubuntu Breezy but it worked for me, even if im using Ubuntu Dapper Beta. 6.06.

You can try it.

---

### Post by funkyade on 2006-04-25
[QUOTE=kenweill]Just go to the Wiki Page of Ubuntu.
Then search for VMware.
There, theres a link to installing VMware Workstation.
It was actually for Ubuntu Breezy but it worked for me, even if im using Ubuntu Dapper Beta. 6.06.

You can try it.[/QUOTE]

Hiya,

Thanks for that.

I'd been at it for so long I'd forgotten to try the obvious. For anyone else who is getting this problem here is the solution I applied:

```
$>sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1
$>sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0
```

stupid, but works....

fa

EDIT: half of this solution is available from the vmware forum [http://www.vmware.com/community/thread.jspa?messageID=370107](http://www.vmware.com/community/thread.jspa?messageID=370107)

---

### Post by funkyade on 2006-04-25
[QUOTE=wylfing]You don't need VMware Workstation to create new VMs. You can do it with qemu. Read here:

[https://wiki.ubuntu.com/VMwarePlayerAndQemu](https://wiki.ubuntu.com/VMwarePlayerAndQemu)[/QUOTE]

cool... had never come across this..

---

