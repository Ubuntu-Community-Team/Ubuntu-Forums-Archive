---
title: "Problems updating virtualbox 2.1 &gt; 2.2"
date: 2009-04-16
forum: General Help
---

### Post by shorizo on 2009-04-16
Hi everyone
if you have troubles when virtualbox is loading and it freezes
that is a USB driver problem
the problem is the imcompatibility whith the old 2.1 USB driver
and this causes the error
you can fix this by editing the next file

```
sudo nano /etc/fstab
```

and check the line tha you added to enable USB in virtualbox 2.1.
something like this:

```
none /proc/bus/usb usbfs devgid=125,devmode=664 0 0
```

you can comment the line adding a '#' or just remove it.
now you must reboot and the problem is solved

;)

---

### Post by codeseer on 2009-04-16
I didn't have any problems transitioning. When transitioning between versions of VirtualBox, it is best to uninstall the previous version and then install the new version; not using the upgrade feature of synaptic. Your settings and disk images will remain intact during that process. Also remember to upgrade the VirtualBox Tools within each of your virtual machines.

---

### Post by ptviperz on 2009-04-27
Is there a good documented procedure for uninstalling/reinstalling? 

I don't want to screw up my vdi's

---

