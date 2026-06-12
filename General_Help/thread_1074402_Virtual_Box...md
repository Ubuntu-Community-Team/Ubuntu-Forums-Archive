---
title: "Virtual Box.."
date: 2009-02-19
forum: General Help
---

### Post by Awesom on 2009-02-19
```

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

```

I get this error :S no idea what to do..

---

### Post by albandy on 2009-02-19
if you downloaded it directly from virtualbox.org type:

sudo /etc/init.d/vboxdrv setup

or if you've downloaded it from the repositories you should download the kernel modules for virtualbox update.

---

### Post by binbash on 2009-02-19
add your self to vboxusers group then

sudo /etc/init.d/vboxdrv setup

---

### Post by Awesom on 2009-02-19
Thanks.. But how do I add myself to that group . ? I am really new so yeh I need details :P

And I downloaded it from Terminal so repositories I guess..?

---

### Post by albandy on 2009-02-19
sudo adduser youruser vboxusers

---

### Post by Awesom on 2009-02-19
> **binbash said:**
> add your self to vboxusers group then

sudo /etc/init.d/vboxdrv setup

```

troy@TroY:~$ sudo /etc/init.d/vboxdrv setup
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
troy@TroY:~$ start
start: missing job name
Try `start --help' for more information.
troy@TroY:~$ /etc/init.d/vboxdrv start
open: Permission denied
 * Starting VirtualBox kernel module vboxdrv                                    chown: changing group of `/dev/vboxdrv': Operation not permitted
ERROR: Removing 'vboxdrv': Operation not permitted

open: Permission denied
 * Cannot change owner vboxusers for device /dev/vboxdrv.
troy@TroY:~$ 
```

---

### Post by albandy on 2009-02-19
This is the repositories edition, so you've two options:

1.- Download the virtualbox kernel modules for your kernel form synaptic
2.- Uninstall it and download the one from virtualbox.org 

I recomend you the 2nd option

---

### Post by Awesom on 2009-02-20
I did the 2nd option and now I get this when trying to install it?

[img]http://www.freeimagehosting.net/uploads/c4b269c1ca.png[/img]

---

### Post by Awesom on 2009-02-20
Anyone?

---

### Post by albandy on 2009-02-20
you've not completelly uninstalled the virtualbox-ose from ubuntu repositories.

search in synaptic for 
virtualbox-ose-modules-2.6.24-23
and uninstall it
try to install virtualbox again

---

