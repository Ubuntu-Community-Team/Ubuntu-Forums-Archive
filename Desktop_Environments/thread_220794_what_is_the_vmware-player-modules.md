---
title: "what is the vmware-player-modules?"
date: 2006-07-22
forum: Desktop Environments
---

### Post by baosheng on 2006-07-22
I searched on Synaptic with the key "kernel" and found a package named "vmware-player-modules". 

What is the purpose of it? How can we use it?

---

### Post by moma on 2006-07-22
$ apt-cache search vmware

"vmware-player-kernel-modules" is a pre-compiled kernel module for VMware player.

Read: [http://packages.ubuntulinux.org/dapper/misc/vmware-player-kernel-modules-2.6.15-25]("http://packages.ubuntulinux.org/dapper/misc/vmware-player-kernel-modules-2.6.15-25")

I suppose that if the VMware player's installer can find a ready-made kenel module it will use that, otherwise it will compile the module from source. Compilation from source requires linux-headers-2.6.X-Y package so it's slightly more complicated affair.

$ apt-cache search $(uname -r)

BTW: Installation of WMware player in *buntu is a very easy task and there are several ready-made Linux-images which you can run in the player.

Take a look at this blogg-page (the text is in Norwegian laguage but just enter the commands and you're done).
[http://linux1.no/node/1738]("http://linux1.no/node/1738")

Practically all major distrubutions have ready-made WMware images.
[http://www.vmware.com/vmtn/appliances/directory/cat/25]("http://www.vmware.com/vmtn/appliances/directory/cat/25")

Link to WMware_Server HOWTO at bottom of this page
[http://www.futuredesktop.com/ubuntu6.06.html]("http://www.futuredesktop.com/ubuntu6.06.html")

---

