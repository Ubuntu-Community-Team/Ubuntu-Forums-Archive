---
title: "GNOME Boxes says 'Connection to [name] failed' on creating or starting a box"
date: 2013-11-12
forum: Desktop Environments
---

### Post by Zeklandia on 2013-11-12
GNOME Boxes gives that error when I create or open a box. It produces no output in a terminal either.

Running ```
gnome-boxes --checks
``` does give this info though:

```
(gnome-boxes:13519): Boxes-WARNING **: util-app.vala:247: Failed to execute child process "restorecon" (No such file or directory)&#8226; The CPU is capable of virtualization: yes
&#8226; The KVM module is loaded: yes
&#8226; Libvirt KVM guest available: yes
&#8226; Boxes storage pool available: no
    Could not get 'gnome-boxes' storage pool information from libvirt. Make sure 'virsh -c qemu:///session pool-dumpxml gnome-boxes' is working.
&#8226; The SELinux context is default: no


Report bugs to <https://bugzilla.gnome.org/enter_bug.cgi?product=gnome-boxes>.
Boxes home page: <http://live.gnome.org/Boxes>.
```

---

### Post by Zeklandia on 2013-11-14
bumpity bump bump.

---

### Post by d-ralston on 2013-11-18
I hate to be a "me too", but this affects me also. I am unable to access my boxes after upgrading to 13.10

Any help is greatly appreciated.

---

