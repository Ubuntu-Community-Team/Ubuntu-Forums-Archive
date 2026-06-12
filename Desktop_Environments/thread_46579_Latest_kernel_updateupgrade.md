---
title: "Latest kernel update/upgrade"
date: 2005-07-05
forum: Desktop Environments
---

### Post by littlepr on 2005-07-05
Guys,

Here's is what I get when I try to upgrade/update my kernel:

E: /var/cache/apt/archives/linux-image-2.6.10-5-386_2.6.10-34.3_i386.deb:  trying to overwrite `/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko', which is also in package ndiswrapper-modules-2.6.10-5-386


I have tried to trick it by renaming the ndiswrapper.ko to ndiswrapper.ko.bak but it still complains about the ndsiwrapper.ko file. I personally would like the script to ask if I would like to keep the current ndiswrapper since it is already configured for my wireless adapter.
 
Has anyone else run into this showstopper?

---

### Post by Xian on 2005-07-05
Usually (as I'm not familiar with this exact package), this type of message indicates that you _first_ need to remove the offending package, which in this case is 'ndiswrapper-modules-2.6.10-5-386', then install the desired kernel, and after this go back and see if you can get the removed package reinstalled.

---

### Post by littlepr on 2005-07-05
Xian,

Thanks for the response. It was exactly what you said.

---

### Post by littlepr on 2005-07-06
Now I have problems with my wireless connection. Ndiswrapper.ko is having issues loading

I get this error:

Jul  5 23:04:04 localhost kernel: ndiswrapper version 1.0rc2 loaded (preempt=yes,smp=no)
Jul  5 23:04:04 localhost kernel: ndiswrapper (wrapper_init:1494): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
Jul  5 23:04:05 localhost udev[8109]: creating device node '/dev/ndiswrapper'
Jul  5 23:04:05 localhost loadndisdriver: loadndisdriver: main(629): version 1.1 doesn't match driver version 1.0rc2
Jul  5 23:04:05 localhost udev[8120]: removing device node '/dev/ndiswrapper'
Jul  5 23:04:05 localhost modprobe: FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted


What do I have to do for it to work again?
Any help is appreciated.

---

### Post by littlepr on 2005-07-08
All set people. All I had to do was upate the ndiswrapper -utils to match the new kernel. I also installed the ndiswrapper-sources. I did  uninstall the drivers first. Then I uninstalled ndiswrapper v1.1 and upgraded to .12+1.0rc2-1. once that was done i ran the ndiswrapper -i xxxxx.inf. Then i ndiswrapper -m to add it to the /etc/modules boot. Rebooted and all was up and well again.

---

