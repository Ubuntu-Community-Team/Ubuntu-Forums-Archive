---
title: "Big Problem, need help..."
date: 2006-05-11
forum: Desktop Environments
---

### Post by hotcha3 on 2006-05-11
Hi, , im a linux newbie, i really need some help with an issue:

I bought an AvertTV dvb-t USB 2.0 and i've been trying to make system recognize it for like a week but i can't. I've found a nice guide here: [http://www.wi-bw.tfh-wildau.de/~pboe...=dvb-usb-howto](http://www.wi-bw.tfh-wildau.de/~pboe...=dvb-usb-howto)

which has helped me alot, but i have a problem after the cvs checkout when i start to compile: when i press: :~/dvb-kernel/build-2.6$ make

i keep getting : Makefile:13: /lib/modules/2.6.15-22-386/source/.config: FIle or directory doesen't exist
make: *** there's no rule to build the objective `/lib/modules/2.6.15-22-386/source/.config'. Alto.


I really don't know anything about compiling but it's the only way i've found to make my dapper (i tried unluckily with breezy) recognize it. I would really appreciate if someone could help me. 

I've already installed kernel headers, source and build essential.

---

### Post by louis_nichols on 2006-05-11
Unfortunatelly, the link you posted was truncated, thus broken. Try reposting it using the link feature of the editor (write a text, select it, press link button, paste link address, press ok)

I'm guessing you haven't installed kernel sources. Do

apt-get install kernel-tree kernel-headers

then try again

---

### Post by hotcha3 on 2006-05-11
[http://www.wi-bw.tfh-wildau.de/~pboettch/home/index.php?site=dvb-usb-howto]("http://www.wi-bw.tfh-wildau.de/~pboettch/home/index.php?site=dvb-usb-howto")

I think it will work now xD

[http://labitacora.net/index.php?p=383]("http://labitacora.net/index.php?p=383")

and this one is another guide i followed (it's the same usb-receiver), but it's in spanish.


well, i put apt-get install kernel-tree kernel-headers   and it says "can't find kernel-tree package"

My sources.list is: 
> ## Uncomment the following two lines to fetch updated software from the network
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse


I just upgraded yesterday to Dapper, and i installed kernel sources and headers (i think so, im very newbie).

Thanks alot

---

### Post by louis_nichols on 2006-05-11
what is the output of the command

dpkg -l | grep kernel

?

---

### Post by hotcha3 on 2006-05-11
ii  iptables                               1.3.3-2ubuntu4  Linux kernel 2.4+ iptables administration tools
ii  kernel-package                         9.001ubuntu15  A utility for building Linux kernel related Debian packa
ii  libapm1                                3.2.2-3ubuntu2  Library for interacting with APM driver in kernel
ii  libdrm2                                2.0-0ubuntu1  Userspace interface to kernel DRM services -- runtime
ii  linux-386                              2.6.15.21  Complete Linux kernel on 386.
ii  linux-headers-2.6.15-22                2.6.15-22.34  Header files related to Linux kernel version 2.6.15
ii  linux-headers-2.6.15-22-386            2.6.15-22.34  Linux kernel headers 2.6.15 on 386
ii  linux-image-2.6.12-10-386              2.6.12-10.32  Linux kernel image for version 2.6.12 on 386.
ii  linux-image-2.6.12-9-386               2.6.12-9.23  Linux kernel image for version 2.6.12 on 386.
ii  linux-image-2.6.15-21-386              2.6.15-21.32  Linux kernel image for version 2.6.15 on 386.
ii  linux-image-2.6.15-22-386              2.6.15-22.34  Linux kernel image for version 2.6.15 on 386.
ii  linux-image-386                        2.6.15.21  Linux kernel image on 386.
ii  linux-kernel-headers                   2.6.11.2-0ubuntu16  Linux Kernel Headers for development
ii  linux-source                           2.6.15.21  Linux kernel source with Ubuntu patches
ii  linux-source-2.6.15                    2.6.15-22.34  Linux kernel source for version 2.6.15 with Ubuntu patch
ii  module-init-tools                      3.2.2-1ubuntu7  tools for managing Linux kernel modules
ii  nvidia-kernel-common                   20051028+1  NVIDIA binary kernel module common files
ii  powernowd                              0.97-1ubuntu1  control cpu speed and voltage using 2.6 kernel interface
ii  udev                                   079-0ubuntu30  rule-based device node and kernel event manager

---

### Post by hotcha3 on 2006-05-11
Is it normal that i have so much different kernel images (or whatever... im trying to learn) ?

---

### Post by louis_nichols on 2006-05-11
[QUOTE=hotcha3]Is it normal that i have so much different kernel images (or whatever... im trying to learn) ?[/QUOTE]

Well... there's no problem with that, except it takes some more space on your hard-disk. The policy I use is to keep the original kernel from the install cd and then the latest from the repos.

I'll look some more in your compiling problem.

---

### Post by hotcha3 on 2006-05-11
Ok, do u think the problem i have may be caused by that ?  I would like to keep only the last one 2.6.15-22 and erase others to free space, how can i do that ? 

Thanx alot for helping, coz im really getting desperate with that dvb usb (i have a dual boot, with xp, and it works there, but i only keep it for games) i've been trying for a week...

---

### Post by louis_nichols on 2006-05-11
No, the compiling problem is definitely not caused by your having more kernels installed. the system knows which one runs via the simple command ```
uname -r
``` and doesn't confuse anything.

Now, I'm pretty sure the problem is a missing package, but I don't know which one. It's looking for this path /lib/modules/2.6.15-22-386/source/.config which doesn't even exist on my system and I'm sure on yours either.

I also downloaded the source for dvb-usb and I'm getting the same error. troubleshooting now... ... ... ...:-k

---

### Post by louis_nichols on 2006-05-11
OK. I got  a step further. By making the symlink

```
sudo ln -s /usr/src/linux-headers-2.6.15-21/ /lib/modules/2.6.15-21-k7/source
```

I got it to start compiling. But it stopped at another point, where it says:

```
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-21'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.15-21/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/flexcop-pci.o
In file included from /home/myself/downloads/^src/dvb-kernel/build-2.6/dvbdev.h:32,
                 from /home/myself/downloads/^src/dvb-kernel/build-2.6/dmxdev.h:37,
                 from /home/myself/downloads/^src/dvb-kernel/build-2.6/flexcop-common.h:16,
                 from /home/myself/downloads/^src/dvb-kernel/build-2.6/flexcop-pci.c:10:
/home/myself/downloads/^src/dvb-kernel/build-2.6/compat.h:7:18: error: bttv.h: No such file or directory
make[3]: *** [/home/myself/downloads/^src/dvb-kernel/build-2.6/flexcop-pci.o] Error 1
make[2]: *** [_module_/home/myself/downloads/^src/dvb-kernel/build-2.6] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-21'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/myself/downloads/^src/dvb-kernel/build-2.6'
make: *** [all] Error 2

```. I'm guessing this is because the source actually doesn't belong to the k7 version of the kernel, which I'm running. The problem is it seems the kernel-headers for my current version are unavailable in synaptic, so I'm installing kernel 2.6.15-22-k7, complete with headers and all, and then try again. This will take a while over my connection, though.

---

### Post by hotcha3 on 2006-05-11
Ok so im at the same stage as you, i think.

I did: 
> sudo ln -s /usr/src/linux-headers-2.6.15-22/ /lib/modules/2.6.15-22-386/source

then i started compiling on build-2.6 and it gave me this:

> [ -L saa7146_video.c ] || ./getlinks
getting links from kernel-cvs driver
make[1]: se ingresa al directorio `/home/sunil/dvb-kernel/build-2.6'
rm -f *.o *.ko .*.o.cmd .*.ko.cmd *.mod.c .*.o.d fdump av7110_firm.h video-buf.crm -rf .tmp_versions
find . -type l | xargs -r rm
make[1]: se sale del directorio `/home/sunil/dvb-kernel/build-2.6'
crea el enlace simbólico `av7110.c' a `../linux/drivers/media/dvb/ttpci/av7110.c'
crea el enlace simbólico `av7110.h' a `../linux/drivers/media/dvb/ttpci/av7110.h'
crea el enlace simbólico `av7110_av.c' a `../linux/drivers/media/dvb/ttpci/av7110_av.c'
crea el enlace simbólico `av7110_av.h' a `../linux/drivers/media/dvb/ttpci/av7110_av.h'
crea el enlace simbólico `av7110_ca.c' a `../linux/drivers/media/dvb/ttpci/av7110_ca.c'
crea el enlace simbólico `av7110_ca.h' a `../linux/drivers/media/dvb/ttpci/av7110_ca.h'
crea el enlace simbólico `av7110_hw.c' a `../linux/drivers/media/dvb/ttpci/av7110_hw.c'
crea el enlace simbólico `av7110_hw.h' a `../linux/drivers/media/dvb/ttpci/av7110_hw.h'
crea el enlace simbólico `av7110_ipack.c' a `../linux/drivers/media/dvb/ttpci/av7110_ipack.c'
crea el enlace simbólico `av7110_ipack.h' a `../linux/drivers/media/dvb/ttpci/av7110_ipack.h'
crea el enlace simbólico `av7110_ir.c' a `../linux/drivers/media/dvb/ttpci/av7110_ir.c'
crea el enlace simbólico `av7110_v4l.c' a `../linux/drivers/media/dvb/ttpci/av7110_v4l.c'
crea el enlace simbólico `budget-av.c' a `../linux/drivers/media/dvb/ttpci/budget-av.c'
crea el enlace simbólico `budget-ci.c' a `../linux/drivers/media/dvb/ttpci/budget-ci.c'
crea el enlace simbólico `budget-core.c' a `../linux/drivers/media/dvb/ttpci/budget-core.c'
crea el enlace simbólico `budget-patch.c' a `../linux/drivers/media/dvb/ttpci/budget-patch.c'
crea el enlace simbólico `budget.c' a `../linux/drivers/media/dvb/ttpci/budget.c'
crea el enlace simbólico `budget.h' a `../linux/drivers/media/dvb/ttpci/budget.h'
crea el enlace simbólico `fdump.c' a `../linux/drivers/media/dvb/ttpci/fdump.c'
crea el enlace simbólico `ttpci-eeprom.c' a `../linux/drivers/media/dvb/ttpci/ttpci-eeprom.c'
crea el enlace simbólico `ttpci-eeprom.h' a `../linux/drivers/media/dvb/ttpci/ttpci-eeprom.h'
crea el enlace simbólico `dvb-ttusb-budget.c' a `../linux/drivers/media/dvb/ttusb-budget/dvb-ttusb-budget.c'
crea el enlace simbólico `dvb-ttusb-dspbootcode.h' a `../linux/drivers/media/dvb/ttusb-budget/dvb-ttusb-dspbootcode.h'
crea el enlace simbólico `ttusb_dec.c' a `../linux/drivers/media/dvb/ttusb-dec/ttusb_dec.c'
crea el enlace simbólico `ttusbdecfe.c' a `../linux/drivers/media/dvb/ttusb-dec/ttusbdecfe.c'
crea el enlace simbólico `ttusbdecfe.h' a `../linux/drivers/media/dvb/ttusb-dec/ttusbdecfe.h'
crea el enlace simbólico `dibusb-mb.c' a `../linux/drivers/media/dvb/dvb-usb/dibusb-mb.c'
crea el enlace simbólico `a800.c' a `../linux/drivers/media/dvb/dvb-usb/a800.c'
crea el enlace simbólico `cxusb.c' a `../linux/drivers/media/dvb/dvb-usb/cxusb.c'
crea el enlace simbólico `cxusb.h' a `../linux/drivers/media/dvb/dvb-usb/cxusb.h'
crea el enlace simbólico `dibusb-common.c' a `../linux/drivers/media/dvb/dvb-usb/dibusb-common.c'
crea el enlace simbólico `dibusb-mc.c' a `../linux/drivers/media/dvb/dvb-usb/dibusb-mc.c'
crea el enlace simbólico `dibusb.h' a `../linux/drivers/media/dvb/dvb-usb/dibusb.h'
crea el enlace simbólico `digitv.c' a `../linux/drivers/media/dvb/dvb-usb/digitv.c'
crea el enlace simbólico `digitv.h' a `../linux/drivers/media/dvb/dvb-usb/digitv.h'
crea el enlace simbólico `dtt200u-fe.c' a `../linux/drivers/media/dvb/dvb-usb/dtt200u-fe.c'
crea el enlace simbólico `dtt200u.c' a `../linux/drivers/media/dvb/dvb-usb/dtt200u.c'
crea el enlace simbólico `dtt200u.h' a `../linux/drivers/media/dvb/dvb-usb/dtt200u.h'
crea el enlace simbólico `dvb-usb-common.h' a `../linux/drivers/media/dvb/dvb-usb/dvb-usb-common.h'
crea el enlace simbólico `dvb-usb-dvb.c' a `../linux/drivers/media/dvb/dvb-usb/dvb-usb-dvb.c'
crea el enlace simbólico `dvb-usb-firmware.c' a `../linux/drivers/media/dvb/dvb-usb/dvb-usb-firmware.c'
crea el enlace simbólico `dvb-usb-i2c.c' a `../linux/drivers/media/dvb/dvb-usb/dvb-usb-i2c.c'
crea el enlace simbólico `dvb-usb-ids.h' a `../linux/drivers/media/dvb/dvb-usb/dvb-usb-ids.h'
crea el enlace simbólico `dvb-usb-init.c' a `../linux/drivers/media/dvb/dvb-usb/dvb-usb-init.c'
crea el enlace simbólico `dvb-usb-remote.c' a `../linux/drivers/media/dvb/dvb-usb/dvb-usb-remote.c'
crea el enlace simbólico `dvb-usb-urb.c' a `../linux/drivers/media/dvb/dvb-usb/dvb-usb-urb.c'
crea el enlace simbólico `dvb-usb.h' a `../linux/drivers/media/dvb/dvb-usb/dvb-usb.h'
crea el enlace simbólico `nova-t-usb2.c' a `../linux/drivers/media/dvb/dvb-usb/nova-t-usb2.c'
crea el enlace simbólico `umt-010.c' a `../linux/drivers/media/dvb/dvb-usb/umt-010.c'
crea el enlace simbólico `vp702x-fe.c' a `../linux/drivers/media/dvb/dvb-usb/vp702x-fe.c'
crea el enlace simbólico `vp702x.c' a `../linux/drivers/media/dvb/dvb-usb/vp702x.c'
crea el enlace simbólico `vp702x.h' a `../linux/drivers/media/dvb/dvb-usb/vp702x.h'
crea el enlace simbólico `vp7045-fe.c' a `../linux/drivers/media/dvb/dvb-usb/vp7045-fe.c'
crea el enlace simbólico `vp7045.c' a `../linux/drivers/media/dvb/dvb-usb/vp7045.c'
crea el enlace simbólico `vp7045.h' a `../linux/drivers/media/dvb/dvb-usb/vp7045.h'
crea el enlace simbólico `dst_ca.c' a `../linux/drivers/media/dvb/bt8xx/dst_ca.c'
crea el enlace simbólico `bt878.c' a `../linux/drivers/media/dvb/bt8xx/bt878.c'
crea el enlace simbólico `bt878.h' a `../linux/drivers/media/dvb/bt8xx/bt878.h'
crea el enlace simbólico `dst.c' a `../linux/drivers/media/dvb/bt8xx/dst.c'
crea el enlace simbólico `dst_ca.h' a `../linux/drivers/media/dvb/bt8xx/dst_ca.h'
crea el enlace simbólico `dst_common.h' a `../linux/drivers/media/dvb/bt8xx/dst_common.h'
crea el enlace simbólico `dst_priv.h' a `../linux/drivers/media/dvb/bt8xx/dst_priv.h'
crea el enlace simbólico `dvb-bt8xx.c' a `../linux/drivers/media/dvb/bt8xx/dvb-bt8xx.c'
crea el enlace simbólico `dvb-bt8xx.h' a `../linux/drivers/media/dvb/bt8xx/dvb-bt8xx.h'
crea el enlace simbólico `flexcop-common.h' a `../linux/drivers/media/dvb/b2c2/flexcop-common.h'
crea el enlace simbólico `flexcop-dma.c' a `../linux/drivers/media/dvb/b2c2/flexcop-dma.c'
crea el enlace simbólico `flexcop-eeprom.c' a `../linux/drivers/media/dvb/b2c2/flexcop-eeprom.c'
crea el enlace simbólico `flexcop-fe-tuner.c' a `../linux/drivers/media/dvb/b2c2/flexcop-fe-tuner.c'
crea el enlace simbólico `flexcop-hw-filter.c' a `../linux/drivers/media/dvb/b2c2/flexcop-hw-filter.c'
crea el enlace simbólico `flexcop-i2c.c' a `../linux/drivers/media/dvb/b2c2/flexcop-i2c.c'
crea el enlace simbólico `flexcop-misc.c' a `../linux/drivers/media/dvb/b2c2/flexcop-misc.c'
crea el enlace simbólico `flexcop-pci.c' a `../linux/drivers/media/dvb/b2c2/flexcop-pci.c'
crea el enlace simbólico `flexcop-reg.h' a `../linux/drivers/media/dvb/b2c2/flexcop-reg.h'
crea el enlace simbólico `flexcop-sram.c' a `../linux/drivers/media/dvb/b2c2/flexcop-sram.c'
crea el enlace simbólico `flexcop-usb.c' a `../linux/drivers/media/dvb/b2c2/flexcop-usb.c'
crea el enlace simbólico `flexcop-usb.h' a `../linux/drivers/media/dvb/b2c2/flexcop-usb.h'
crea el enlace simbólico `flexcop.c' a `../linux/drivers/media/dvb/b2c2/flexcop.c'
crea el enlace simbólico `flexcop.h' a `../linux/drivers/media/dvb/b2c2/flexcop.h'
crea el enlace simbólico `flexcop_ibi_value_be.h' a `../linux/drivers/media/dvb/b2c2/flexcop_ibi_value_be.h'
crea el enlace simbólico `flexcop_ibi_value_le.h' a `../linux/drivers/media/dvb/b2c2/flexcop_ibi_value_le.h'
crea el enlace simbólico `stv0297_cs2.c' a `../linux/drivers/media/dvb/b2c2/stv0297_cs2.c'
crea el enlace simbólico `stv0297_cs2.h' a `../linux/drivers/media/dvb/b2c2/stv0297_cs2.h'
crea el enlace simbólico `stv0297_priv.h' a `../linux/drivers/media/dvb/b2c2/stv0297_priv.h'
crea el enlace simbólico `cinergyT2.c' a `../linux/drivers/media/dvb/cinergyT2/cinergyT2.c'
crea el enlace simbólico `dmxdev.c' a `../linux/drivers/media/dvb/dvb-core/dmxdev.c'
crea el enlace simbólico `demux.h' a `../linux/drivers/media/dvb/dvb-core/demux.h'
crea el enlace simbólico `dmxdev.h' a `../linux/drivers/media/dvb/dvb-core/dmxdev.h'
crea el enlace simbólico `dvb_ca_en50221.c' a `../linux/drivers/media/dvb/dvb-core/dvb_ca_en50221.c'
crea el enlace simbólico `dvb_ca_en50221.h' a `../linux/drivers/media/dvb/dvb-core/dvb_ca_en50221.h'
crea el enlace simbólico `dvb_demux.c' a `../linux/drivers/media/dvb/dvb-core/dvb_demux.c'
crea el enlace simbólico `dvb_demux.h' a `../linux/drivers/media/dvb/dvb-core/dvb_demux.h'
crea el enlace simbólico `dvb_filter.c' a `../linux/drivers/media/dvb/dvb-core/dvb_filter.c'
crea el enlace simbólico `dvb_filter.h' a `../linux/drivers/media/dvb/dvb-core/dvb_filter.h'
crea el enlace simbólico `dvb_frontend.c' a `../linux/drivers/media/dvb/dvb-core/dvb_frontend.c'
crea el enlace simbólico `dvb_frontend.h' a `../linux/drivers/media/dvb/dvb-core/dvb_frontend.h'
crea el enlace simbólico `dvb_net.c' a `../linux/drivers/media/dvb/dvb-core/dvb_net.c'
crea el enlace simbólico `dvb_net.h' a `../linux/drivers/media/dvb/dvb-core/dvb_net.h'
crea el enlace simbólico `dvb_ringbuffer.c' a `../linux/drivers/media/dvb/dvb-core/dvb_ringbuffer.c'
crea el enlace simbólico `dvb_ringbuffer.h' a `../linux/drivers/media/dvb/dvb-core/dvb_ringbuffer.h'
crea el enlace simbólico `dvbdev.c' a `../linux/drivers/media/dvb/dvb-core/dvbdev.c'
crea el enlace simbólico `dvbdev.h' a `../linux/drivers/media/dvb/dvb-core/dvbdev.h'
crea el enlace simbólico `at76c651.c' a `../linux/drivers/media/dvb/frontends/at76c651.c'
crea el enlace simbólico `at76c651.h' a `../linux/drivers/media/dvb/frontends/at76c651.h'
crea el enlace simbólico `bcm3510.c' a `../linux/drivers/media/dvb/frontends/bcm3510.c'
crea el enlace simbólico `bcm3510.h' a `../linux/drivers/media/dvb/frontends/bcm3510.h'
crea el enlace simbólico `bcm3510_priv.h' a `../linux/drivers/media/dvb/frontends/bcm3510_priv.h'
crea el enlace simbólico `cx22700.c' a `../linux/drivers/media/dvb/frontends/cx22700.c'
crea el enlace simbólico `cx22700.h' a `../linux/drivers/media/dvb/frontends/cx22700.h'
crea el enlace simbólico `cx22702.c' a `../linux/drivers/media/dvb/frontends/cx22702.c'
crea el enlace simbólico `cx22702.h' a `../linux/drivers/media/dvb/frontends/cx22702.h'
crea el enlace simbólico `cx24110.c' a `../linux/drivers/media/dvb/frontends/cx24110.c'
crea el enlace simbólico `cx24110.h' a `../linux/drivers/media/dvb/frontends/cx24110.h'
crea el enlace simbólico `cx24123.c' a `../linux/drivers/media/dvb/frontends/cx24123.c'
crea el enlace simbólico `cx24123.h' a `../linux/drivers/media/dvb/frontends/cx24123.h'
crea el enlace simbólico `dib3000-common.c' a `../linux/drivers/media/dvb/frontends/dib3000-common.c'
crea el enlace simbólico `dib3000-common.h' a `../linux/drivers/media/dvb/frontends/dib3000-common.h'
crea el enlace simbólico `dib3000.h' a `../linux/drivers/media/dvb/frontends/dib3000.h'
crea el enlace simbólico `dib3000mb.c' a `../linux/drivers/media/dvb/frontends/dib3000mb.c'
crea el enlace simbólico `dib3000mb_priv.h' a `../linux/drivers/media/dvb/frontends/dib3000mb_priv.h'
crea el enlace simbólico `dib3000mc.c' a `../linux/drivers/media/dvb/frontends/dib3000mc.c'
crea el enlace simbólico `dib3000mc_priv.h' a `../linux/drivers/media/dvb/frontends/dib3000mc_priv.h'
crea el enlace simbólico `dvb-pll.c' a `../linux/drivers/media/dvb/frontends/dvb-pll.c'
crea el enlace simbólico `dvb-pll.h' a `../linux/drivers/media/dvb/frontends/dvb-pll.h'
crea el enlace simbólico `dvb_dummy_fe.c' a `../linux/drivers/media/dvb/frontends/dvb_dummy_fe.c'
crea el enlace simbólico `dvb_dummy_fe.h' a `../linux/drivers/media/dvb/frontends/dvb_dummy_fe.h'
crea el enlace simbólico `l64781.c' a `../linux/drivers/media/dvb/frontends/l64781.c'
crea el enlace simbólico `l64781.h' a `../linux/drivers/media/dvb/frontends/l64781.h'
crea el enlace simbólico `lgdt330x.c' a `../linux/drivers/media/dvb/frontends/lgdt330x.c'
crea el enlace simbólico `lgdt330x.h' a `../linux/drivers/media/dvb/frontends/lgdt330x.h'
crea el enlace simbólico `lgdt330x_priv.h' a `../linux/drivers/media/dvb/frontends/lgdt330x_priv.h'
crea el enlace simbólico `mt312.c' a `../linux/drivers/media/dvb/frontends/mt312.c'
crea el enlace simbólico `mt312.h' a `../linux/drivers/media/dvb/frontends/mt312.h'
crea el enlace simbólico `mt312_priv.h' a `../linux/drivers/media/dvb/frontends/mt312_priv.h'
crea el enlace simbólico `mt352.c' a `../linux/drivers/media/dvb/frontends/mt352.c'
crea el enlace simbólico `mt352.h' a `../linux/drivers/media/dvb/frontends/mt352.h'
crea el enlace simbólico `mt352_priv.h' a `../linux/drivers/media/dvb/frontends/mt352_priv.h'
crea el enlace simbólico `nxt2002.c' a `../linux/drivers/media/dvb/frontends/nxt2002.c'
crea el enlace simbólico `nxt2002.h' a `../linux/drivers/media/dvb/frontends/nxt2002.h'
crea el enlace simbólico `nxt200x.c' a `../linux/drivers/media/dvb/frontends/nxt200x.c'
crea el enlace simbólico `nxt200x.h' a `../linux/drivers/media/dvb/frontends/nxt200x.h'
crea el enlace simbólico `nxt6000.c' a `../linux/drivers/media/dvb/frontends/nxt6000.c'
crea el enlace simbólico `nxt6000.h' a `../linux/drivers/media/dvb/frontends/nxt6000.h'
crea el enlace simbólico `nxt6000_priv.h' a `../linux/drivers/media/dvb/frontends/nxt6000_priv.h'
crea el enlace simbólico `or51132.c' a `../linux/drivers/media/dvb/frontends/or51132.c'
crea el enlace simbólico `or51132.h' a `../linux/drivers/media/dvb/frontends/or51132.h'
crea el enlace simbólico `or51211.c' a `../linux/drivers/media/dvb/frontends/or51211.c'
crea el enlace simbólico `or51211.h' a `../linux/drivers/media/dvb/frontends/or51211.h'
crea el enlace simbólico `s5h1420.c' a `../linux/drivers/media/dvb/frontends/s5h1420.c'
crea el enlace simbólico `s5h1420.h' a `../linux/drivers/media/dvb/frontends/s5h1420.h'
crea el enlace simbólico `sp8870.c' a `../linux/drivers/media/dvb/frontends/sp8870.c'
crea el enlace simbólico `sp8870.h' a `../linux/drivers/media/dvb/frontends/sp8870.h'
crea el enlace simbólico `sp887x.c' a `../linux/drivers/media/dvb/frontends/sp887x.c'
crea el enlace simbólico `sp887x.h' a `../linux/drivers/media/dvb/frontends/sp887x.h'
crea el enlace simbólico `stv0297.c' a `../linux/drivers/media/dvb/frontends/stv0297.c'
crea el enlace simbólico `stv0297.h' a `../linux/drivers/media/dvb/frontends/stv0297.h'
crea el enlace simbólico `stv0299.c' a `../linux/drivers/media/dvb/frontends/stv0299.c'
crea el enlace simbólico `stv0299.h' a `../linux/drivers/media/dvb/frontends/stv0299.h'
crea el enlace simbólico `tda10021.c' a `../linux/drivers/media/dvb/frontends/tda10021.c'
crea el enlace simbólico `tda10021.h' a `../linux/drivers/media/dvb/frontends/tda10021.h'
crea el enlace simbólico `tda1004x.c' a `../linux/drivers/media/dvb/frontends/tda1004x.c'
crea el enlace simbólico `tda1004x.h' a `../linux/drivers/media/dvb/frontends/tda1004x.h'
crea el enlace simbólico `tda8083.c' a `../linux/drivers/media/dvb/frontends/tda8083.c'
crea el enlace simbólico `tda8083.h' a `../linux/drivers/media/dvb/frontends/tda8083.h'
crea el enlace simbólico `tda80xx.c' a `../linux/drivers/media/dvb/frontends/tda80xx.c'
crea el enlace simbólico `tda80xx.h' a `../linux/drivers/media/dvb/frontends/tda80xx.h'
crea el enlace simbólico `ves1820.c' a `../linux/drivers/media/dvb/frontends/ves1820.c'
crea el enlace simbólico `ves1820.h' a `../linux/drivers/media/dvb/frontends/ves1820.h'
crea el enlace simbólico `ves1x93.c' a `../linux/drivers/media/dvb/frontends/ves1x93.c'
crea el enlace simbólico `ves1x93.h' a `../linux/drivers/media/dvb/frontends/ves1x93.h'
crea el enlace simbólico `saa7146_core.c' a `../linux/drivers/media/common/saa7146_core.c'
crea el enlace simbólico `saa7146_fops.c' a `../linux/drivers/media/common/saa7146_fops.c'
crea el enlace simbólico `saa7146_hlp.c' a `../linux/drivers/media/common/saa7146_hlp.c'
crea el enlace simbólico `saa7146_i2c.c' a `../linux/drivers/media/common/saa7146_i2c.c'
crea el enlace simbólico `saa7146_vbi.c' a `../linux/drivers/media/common/saa7146_vbi.c'
crea el enlace simbólico `saa7146_video.c' a `../linux/drivers/media/common/saa7146_video.c'
crea el enlace simbólico `saa7146_vv_ksyms.c' a `../linux/drivers/media/common/saa7146_vv_ksyms.c'
crea el enlace simbólico `pluto2.c' a `../linux/drivers/media/dvb/pluto2/pluto2.c'
rm -rf video-buf.c
ln -s /lib/modules/2.6.15-22-386/source/drivers/media/video/video-buf.c video-buf.c
make -C /lib/modules/2.6.15-22-386/source  SUBDIRS=/home/sunil/dvb-kernel/build-2.6 AV7110_FIRMWARE= AV7110_OSD=y
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.15-22'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.15-22/Module.symvers
           is missing; modules will have no dependencies and modversions.

  LD      /home/sunil/dvb-kernel/build-2.6/built-in.o
  CC [M]  /home/sunil/dvb-kernel/build-2.6/version_check.o
  CC [M]  /home/sunil/dvb-kernel/build-2.6/flexcop-pci.o
En el fichero incluído de /home/sunil/dvb-kernel/build-2.6/dvbdev.h:32,
                 de /home/sunil/dvb-kernel/build-2.6/dmxdev.h:37,
                 de /home/sunil/dvb-kernel/build-2.6/flexcop-common.h:16,
                 de /home/sunil/dvb-kernel/build-2.6/flexcop-pci.c:10:
/home/sunil/dvb-kernel/build-2.6/compat.h:7:18: error: bttv.h: No existe el fichero o el directorio
make[2]: *** [/home/sunil/dvb-kernel/build-2.6/flexcop-pci.o] Error 1
make[1]: *** [_module_/home/sunil/dvb-kernel/build-2.6] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.15-22'
make: *** [all] Error 2


It hasn't gone well isn't it ?

---

### Post by louis_nichols on 2006-05-11
EDIT: I just noticed there's a newer version of the bttv driver than the one I initially linked to, and that I used in trying to compile, so I updated the link.

Well... I almost thought I had it :(

What I did... I downloaded the source for the bttv driver from [here.]("http://dl.bytesex.org/releases/video4linux/bttv-0.9.15.tar.gz") I don't know exactly what it is, but the README says you need it. Then I unpacked it and copied first the file bttv.h and after another similar error the file bt848.h to the dvb-kernel/build-2.6 directory. Then, I hit make. I almost thought it would go the whole way, but it stopped at an error that it's too late in the night for me to be able to troubleshoot. So, sorry it hasn't worked yet. Perhaps tomorrow we'll have better luck or perhaps someone from another time frame on the globe (It's around 7 PM in the States :) ) will stumble upon this discussion and find the solution to go further.

Below is the whole story (first make command is after copying the bttv.h file to the directory, the second after copying bt848.h)

```
make
make -C /home/myself/downloads/^src/dvb-kernel/build-2.6
make[1]: Entering directory `/home/myself/downloads/^src/dvb-kernel/build-2.6'
[ -L saa7146_video.c ] || ./getlinks
getting links from kernel-cvs driver
make[2]: Entering directory `/home/myself/downloads/^src/dvb-kernel/build-2.6'
rm -f *.o *.ko .*.o.cmd .*.ko.cmd *.mod.c .*.o.d fdump av7110_firm.h video-buf.c
rm -rf .tmp_versions
find . -type l | xargs -r rm
make[2]: Leaving directory `/home/myself/downloads/^src/dvb-kernel/build-2.6'
create symbolic link `budget-patch.c' to `../linux/drivers/media/dvb/ttpci/budget-patch.c'
create symbolic link `budget-core.c' to `../linux/drivers/media/dvb/ttpci/budget-core.c'
create symbolic link `fdump.c' to `../linux/drivers/media/dvb/ttpci/fdump.c'
create symbolic link `ttpci-eeprom.c' to `../linux/drivers/media/dvb/ttpci/ttpci-eeprom.c'
create symbolic link `ttpci-eeprom.h' to `../linux/drivers/media/dvb/ttpci/ttpci-eeprom.h'
create symbolic link `av7110.c' to `../linux/drivers/media/dvb/ttpci/av7110.c'
create symbolic link `av7110.h' to `../linux/drivers/media/dvb/ttpci/av7110.h'
create symbolic link `av7110_av.c' to `../linux/drivers/media/dvb/ttpci/av7110_av.c'
create symbolic link `av7110_av.h' to `../linux/drivers/media/dvb/ttpci/av7110_av.h'
create symbolic link `av7110_ca.c' to `../linux/drivers/media/dvb/ttpci/av7110_ca.c'
create symbolic link `av7110_ca.h' to `../linux/drivers/media/dvb/ttpci/av7110_ca.h'
create symbolic link `av7110_hw.c' to `../linux/drivers/media/dvb/ttpci/av7110_hw.c'
create symbolic link `av7110_hw.h' to `../linux/drivers/media/dvb/ttpci/av7110_hw.h'
create symbolic link `av7110_ir.c' to `../linux/drivers/media/dvb/ttpci/av7110_ir.c'
create symbolic link `budget.c' to `../linux/drivers/media/dvb/ttpci/budget.c'
create symbolic link `budget.h' to `../linux/drivers/media/dvb/ttpci/budget.h'
create symbolic link `av7110_v4l.c' to `../linux/drivers/media/dvb/ttpci/av7110_v4l.c'
create symbolic link `av7110_ipack.c' to `../linux/drivers/media/dvb/ttpci/av7110_ipack.c'
create symbolic link `av7110_ipack.h' to `../linux/drivers/media/dvb/ttpci/av7110_ipack.h'
create symbolic link `budget-av.c' to `../linux/drivers/media/dvb/ttpci/budget-av.c'
create symbolic link `budget-ci.c' to `../linux/drivers/media/dvb/ttpci/budget-ci.c'
create symbolic link `dvb-ttusb-budget.c' to `../linux/drivers/media/dvb/ttusb-budget/dvb-ttusb-budget.c'create symbolic link `dvb-ttusb-dspbootcode.h' to `../linux/drivers/media/dvb/ttusb-budget/dvb-ttusb-dspbootcode.h'
create symbolic link `ttusb_dec.c' to `../linux/drivers/media/dvb/ttusb-dec/ttusb_dec.c'
create symbolic link `ttusbdecfe.c' to `../linux/drivers/media/dvb/ttusb-dec/ttusbdecfe.c'
create symbolic link `ttusbdecfe.h' to `../linux/drivers/media/dvb/ttusb-dec/ttusbdecfe.h'
create symbolic link `dibusb.h' to `../linux/drivers/media/dvb/dvb-usb/dibusb.h'
create symbolic link `dvb-usb-i2c.c' to `../linux/drivers/media/dvb/dvb-usb/dvb-usb-i2c.c'
create symbolic link `dvb-usb-dvb.c' to `../linux/drivers/media/dvb/dvb-usb/dvb-usb-dvb.c'
create symbolic link `dvb-usb-ids.h' to `../linux/drivers/media/dvb/dvb-usb/dvb-usb-ids.h'
create symbolic link `digitv.c' to `../linux/drivers/media/dvb/dvb-usb/digitv.c'
create symbolic link `digitv.h' to `../linux/drivers/media/dvb/dvb-usb/digitv.h'
create symbolic link `dvb-usb-urb.c' to `../linux/drivers/media/dvb/dvb-usb/dvb-usb-urb.c'
create symbolic link `cxusb.c' to `../linux/drivers/media/dvb/dvb-usb/cxusb.c'
create symbolic link `cxusb.h' to `../linux/drivers/media/dvb/dvb-usb/cxusb.h'
create symbolic link `dvb-usb-init.c' to `../linux/drivers/media/dvb/dvb-usb/dvb-usb-init.c'
create symbolic link `dvb-usb-remote.c' to `../linux/drivers/media/dvb/dvb-usb/dvb-usb-remote.c'
create symbolic link `vp7045.c' to `../linux/drivers/media/dvb/dvb-usb/vp7045.c'
create symbolic link `vp7045.h' to `../linux/drivers/media/dvb/dvb-usb/vp7045.h'
create symbolic link `vp702x.c' to `../linux/drivers/media/dvb/dvb-usb/vp702x.c'
create symbolic link `vp702x.h' to `../linux/drivers/media/dvb/dvb-usb/vp702x.h'
create symbolic link `dibusb-common.c' to `../linux/drivers/media/dvb/dvb-usb/dibusb-common.c'
create symbolic link `dtt200u-fe.c' to `../linux/drivers/media/dvb/dvb-usb/dtt200u-fe.c'
create symbolic link `dvb-usb-firmware.c' to `../linux/drivers/media/dvb/dvb-usb/dvb-usb-firmware.c'
create symbolic link `vp7045-fe.c' to `../linux/drivers/media/dvb/dvb-usb/vp7045-fe.c'
create symbolic link `a800.c' to `../linux/drivers/media/dvb/dvb-usb/a800.c'
create symbolic link `umt-010.c' to `../linux/drivers/media/dvb/dvb-usb/umt-010.c'
create symbolic link `dibusb-mb.c' to `../linux/drivers/media/dvb/dvb-usb/dibusb-mb.c'
create symbolic link `dibusb-mc.c' to `../linux/drivers/media/dvb/dvb-usb/dibusb-mc.c'
create symbolic link `dvb-usb.h' to `../linux/drivers/media/dvb/dvb-usb/dvb-usb.h'
create symbolic link `dvb-usb-common.h' to `../linux/drivers/media/dvb/dvb-usb/dvb-usb-common.h'
create symbolic link `nova-t-usb2.c' to `../linux/drivers/media/dvb/dvb-usb/nova-t-usb2.c'
create symbolic link `vp702x-fe.c' to `../linux/drivers/media/dvb/dvb-usb/vp702x-fe.c'
create symbolic link `dtt200u.c' to `../linux/drivers/media/dvb/dvb-usb/dtt200u.c'
create symbolic link `dtt200u.h' to `../linux/drivers/media/dvb/dvb-usb/dtt200u.h'
create symbolic link `dvb-bt8xx.c' to `../linux/drivers/media/dvb/bt8xx/dvb-bt8xx.c'
create symbolic link `dvb-bt8xx.h' to `../linux/drivers/media/dvb/bt8xx/dvb-bt8xx.h'
create symbolic link `dst.c' to `../linux/drivers/media/dvb/bt8xx/dst.c'
create symbolic link `dst_common.h' to `../linux/drivers/media/dvb/bt8xx/dst_common.h'
create symbolic link `dst_ca.c' to `../linux/drivers/media/dvb/bt8xx/dst_ca.c'
create symbolic link `dst_ca.h' to `../linux/drivers/media/dvb/bt8xx/dst_ca.h'
create symbolic link `dst_priv.h' to `../linux/drivers/media/dvb/bt8xx/dst_priv.h'
create symbolic link `bt878.c' to `../linux/drivers/media/dvb/bt8xx/bt878.c'
create symbolic link `bt878.h' to `../linux/drivers/media/dvb/bt8xx/bt878.h'
create symbolic link `flexcop.c' to `../linux/drivers/media/dvb/b2c2/flexcop.c'
create symbolic link `flexcop.h' to `../linux/drivers/media/dvb/b2c2/flexcop.h'
create symbolic link `flexcop-fe-tuner.c' to `../linux/drivers/media/dvb/b2c2/flexcop-fe-tuner.c'
create symbolic link `flexcop-eeprom.c' to `../linux/drivers/media/dvb/b2c2/flexcop-eeprom.c'
create symbolic link `flexcop-hw-filter.c' to `../linux/drivers/media/dvb/b2c2/flexcop-hw-filter.c'
create symbolic link `flexcop-common.h' to `../linux/drivers/media/dvb/b2c2/flexcop-common.h'
create symbolic link `stv0297_priv.h' to `../linux/drivers/media/dvb/b2c2/stv0297_priv.h'
create symbolic link `flexcop_ibi_value_be.h' to `../linux/drivers/media/dvb/b2c2/flexcop_ibi_value_be.h'create symbolic link `flexcop_ibi_value_le.h' to `../linux/drivers/media/dvb/b2c2/flexcop_ibi_value_le.h'create symbolic link `flexcop-i2c.c' to `../linux/drivers/media/dvb/b2c2/flexcop-i2c.c'
create symbolic link `flexcop-dma.c' to `../linux/drivers/media/dvb/b2c2/flexcop-dma.c'
create symbolic link `flexcop-pci.c' to `../linux/drivers/media/dvb/b2c2/flexcop-pci.c'
create symbolic link `flexcop-reg.h' to `../linux/drivers/media/dvb/b2c2/flexcop-reg.h'
create symbolic link `flexcop-usb.c' to `../linux/drivers/media/dvb/b2c2/flexcop-usb.c'
create symbolic link `flexcop-usb.h' to `../linux/drivers/media/dvb/b2c2/flexcop-usb.h'
create symbolic link `flexcop-misc.c' to `../linux/drivers/media/dvb/b2c2/flexcop-misc.c'
create symbolic link `stv0297_cs2.c' to `../linux/drivers/media/dvb/b2c2/stv0297_cs2.c'
create symbolic link `stv0297_cs2.h' to `../linux/drivers/media/dvb/b2c2/stv0297_cs2.h'
create symbolic link `flexcop-sram.c' to `../linux/drivers/media/dvb/b2c2/flexcop-sram.c'
create symbolic link `cinergyT2.c' to `../linux/drivers/media/dvb/cinergyT2/cinergyT2.c'
create symbolic link `demux.h' to `../linux/drivers/media/dvb/dvb-core/demux.h'
create symbolic link `dvb_net.c' to `../linux/drivers/media/dvb/dvb-core/dvb_net.c'
create symbolic link `dvb_net.h' to `../linux/drivers/media/dvb/dvb-core/dvb_net.h'
create symbolic link `dvb_demux.c' to `../linux/drivers/media/dvb/dvb-core/dvb_demux.c'
create symbolic link `dvb_demux.h' to `../linux/drivers/media/dvb/dvb-core/dvb_demux.h'
create symbolic link `dvb_frontend.c' to `../linux/drivers/media/dvb/dvb-core/dvb_frontend.c'
create symbolic link `dvb_frontend.h' to `../linux/drivers/media/dvb/dvb-core/dvb_frontend.h'
create symbolic link `dvb_ringbuffer.c' to `../linux/drivers/media/dvb/dvb-core/dvb_ringbuffer.c'
create symbolic link `dvb_ringbuffer.h' to `../linux/drivers/media/dvb/dvb-core/dvb_ringbuffer.h'
create symbolic link `dvb_ca_en50221.c' to `../linux/drivers/media/dvb/dvb-core/dvb_ca_en50221.c'
create symbolic link `dvb_ca_en50221.h' to `../linux/drivers/media/dvb/dvb-core/dvb_ca_en50221.h'
create symbolic link `dvb_filter.c' to `../linux/drivers/media/dvb/dvb-core/dvb_filter.c'
create symbolic link `dvb_filter.h' to `../linux/drivers/media/dvb/dvb-core/dvb_filter.h'
create symbolic link `dmxdev.c' to `../linux/drivers/media/dvb/dvb-core/dmxdev.c'
create symbolic link `dmxdev.h' to `../linux/drivers/media/dvb/dvb-core/dmxdev.h'
create symbolic link `dvbdev.c' to `../linux/drivers/media/dvb/dvb-core/dvbdev.c'
create symbolic link `dvbdev.h' to `../linux/drivers/media/dvb/dvb-core/dvbdev.h'
create symbolic link `lgdt330x_priv.h' to `../linux/drivers/media/dvb/frontends/lgdt330x_priv.h'
create symbolic link `dib3000-common.c' to `../linux/drivers/media/dvb/frontends/dib3000-common.c'
create symbolic link `dib3000-common.h' to `../linux/drivers/media/dvb/frontends/dib3000-common.h'
create symbolic link `nxt2002.c' to `../linux/drivers/media/dvb/frontends/nxt2002.c'
create symbolic link `nxt2002.h' to `../linux/drivers/media/dvb/frontends/nxt2002.h'
create symbolic link `nxt200x.c' to `../linux/drivers/media/dvb/frontends/nxt200x.c'
create symbolic link `nxt200x.h' to `../linux/drivers/media/dvb/frontends/nxt200x.h'
create symbolic link `ves1820.c' to `../linux/drivers/media/dvb/frontends/ves1820.c'
create symbolic link `ves1820.h' to `../linux/drivers/media/dvb/frontends/ves1820.h'
create symbolic link `nxt6000.c' to `../linux/drivers/media/dvb/frontends/nxt6000.c'
create symbolic link `nxt6000.h' to `../linux/drivers/media/dvb/frontends/nxt6000.h'
create symbolic link `tda10021.c' to `../linux/drivers/media/dvb/frontends/tda10021.c'
create symbolic link `tda10021.h' to `../linux/drivers/media/dvb/frontends/tda10021.h'
create symbolic link `tda1004x.c' to `../linux/drivers/media/dvb/frontends/tda1004x.c'
create symbolic link `tda1004x.h' to `../linux/drivers/media/dvb/frontends/tda1004x.h'
create symbolic link `ves1x93.c' to `../linux/drivers/media/dvb/frontends/ves1x93.c'
create symbolic link `ves1x93.h' to `../linux/drivers/media/dvb/frontends/ves1x93.h'
create symbolic link `cx22700.c' to `../linux/drivers/media/dvb/frontends/cx22700.c'
create symbolic link `cx22700.h' to `../linux/drivers/media/dvb/frontends/cx22700.h'
create symbolic link `cx22702.c' to `../linux/drivers/media/dvb/frontends/cx22702.c'
create symbolic link `cx22702.h' to `../linux/drivers/media/dvb/frontends/cx22702.h'
create symbolic link `cx24110.c' to `../linux/drivers/media/dvb/frontends/cx24110.c'
create symbolic link `cx24110.h' to `../linux/drivers/media/dvb/frontends/cx24110.h'
create symbolic link `cx24123.c' to `../linux/drivers/media/dvb/frontends/cx24123.c'
create symbolic link `cx24123.h' to `../linux/drivers/media/dvb/frontends/cx24123.h'
create symbolic link `dib3000mb.c' to `../linux/drivers/media/dvb/frontends/dib3000mb.c'
create symbolic link `dib3000mc.c' to `../linux/drivers/media/dvb/frontends/dib3000mc.c'
create symbolic link `mt312_priv.h' to `../linux/drivers/media/dvb/frontends/mt312_priv.h'
create symbolic link `nxt6000_priv.h' to `../linux/drivers/media/dvb/frontends/nxt6000_priv.h'
create symbolic link `lgdt330x.c' to `../linux/drivers/media/dvb/frontends/lgdt330x.c'
create symbolic link `lgdt330x.h' to `../linux/drivers/media/dvb/frontends/lgdt330x.h'
create symbolic link `mt312.c' to `../linux/drivers/media/dvb/frontends/mt312.c'
create symbolic link `mt312.h' to `../linux/drivers/media/dvb/frontends/mt312.h'
create symbolic link `mt352.c' to `../linux/drivers/media/dvb/frontends/mt352.c'
create symbolic link `mt352.h' to `../linux/drivers/media/dvb/frontends/mt352.h'
create symbolic link `sp8870.c' to `../linux/drivers/media/dvb/frontends/sp8870.c'
create symbolic link `sp8870.h' to `../linux/drivers/media/dvb/frontends/sp8870.h'
create symbolic link `sp887x.c' to `../linux/drivers/media/dvb/frontends/sp887x.c'
create symbolic link `sp887x.h' to `../linux/drivers/media/dvb/frontends/sp887x.h'
create symbolic link `dib3000mc_priv.h' to `../linux/drivers/media/dvb/frontends/dib3000mc_priv.h'
create symbolic link `dvb_dummy_fe.c' to `../linux/drivers/media/dvb/frontends/dvb_dummy_fe.c'
create symbolic link `dvb_dummy_fe.h' to `../linux/drivers/media/dvb/frontends/dvb_dummy_fe.h'
create symbolic link `mt352_priv.h' to `../linux/drivers/media/dvb/frontends/mt352_priv.h'
create symbolic link `dvb-pll.c' to `../linux/drivers/media/dvb/frontends/dvb-pll.c'
create symbolic link `dvb-pll.h' to `../linux/drivers/media/dvb/frontends/dvb-pll.h'
create symbolic link `at76c651.c' to `../linux/drivers/media/dvb/frontends/at76c651.c'
create symbolic link `at76c651.h' to `../linux/drivers/media/dvb/frontends/at76c651.h'
create symbolic link `bcm3510.c' to `../linux/drivers/media/dvb/frontends/bcm3510.c'
create symbolic link `bcm3510.h' to `../linux/drivers/media/dvb/frontends/bcm3510.h'
create symbolic link `dib3000.h' to `../linux/drivers/media/dvb/frontends/dib3000.h'
create symbolic link `l64781.c' to `../linux/drivers/media/dvb/frontends/l64781.c'
create symbolic link `l64781.h' to `../linux/drivers/media/dvb/frontends/l64781.h'
create symbolic link `bcm3510_priv.h' to `../linux/drivers/media/dvb/frontends/bcm3510_priv.h'
create symbolic link `s5h1420.c' to `../linux/drivers/media/dvb/frontends/s5h1420.c'
create symbolic link `s5h1420.h' to `../linux/drivers/media/dvb/frontends/s5h1420.h'
create symbolic link `tda8083.c' to `../linux/drivers/media/dvb/frontends/tda8083.c'
create symbolic link `tda8083.h' to `../linux/drivers/media/dvb/frontends/tda8083.h'
create symbolic link `tda80xx.c' to `../linux/drivers/media/dvb/frontends/tda80xx.c'
create symbolic link `tda80xx.h' to `../linux/drivers/media/dvb/frontends/tda80xx.h'
create symbolic link `or51132.c' to `../linux/drivers/media/dvb/frontends/or51132.c'
create symbolic link `or51132.h' to `../linux/drivers/media/dvb/frontends/or51132.h'
create symbolic link `or51211.c' to `../linux/drivers/media/dvb/frontends/or51211.c'
create symbolic link `or51211.h' to `../linux/drivers/media/dvb/frontends/or51211.h'
create symbolic link `stv0297.c' to `../linux/drivers/media/dvb/frontends/stv0297.c'
create symbolic link `stv0297.h' to `../linux/drivers/media/dvb/frontends/stv0297.h'
create symbolic link `stv0299.c' to `../linux/drivers/media/dvb/frontends/stv0299.c'
create symbolic link `stv0299.h' to `../linux/drivers/media/dvb/frontends/stv0299.h'
create symbolic link `dib3000mb_priv.h' to `../linux/drivers/media/dvb/frontends/dib3000mb_priv.h'
create symbolic link `saa7146_video.c' to `../linux/drivers/media/common/saa7146_video.c'
create symbolic link `saa7146_core.c' to `../linux/drivers/media/common/saa7146_core.c'
create symbolic link `saa7146_fops.c' to `../linux/drivers/media/common/saa7146_fops.c'
create symbolic link `saa7146_i2c.c' to `../linux/drivers/media/common/saa7146_i2c.c'
create symbolic link `saa7146_hlp.c' to `../linux/drivers/media/common/saa7146_hlp.c'
create symbolic link `saa7146_vbi.c' to `../linux/drivers/media/common/saa7146_vbi.c'
create symbolic link `saa7146_vv_ksyms.c' to `../linux/drivers/media/common/saa7146_vv_ksyms.c'
create symbolic link `pluto2.c' to `../linux/drivers/media/dvb/pluto2/pluto2.c'
make -C /lib/modules/2.6.15-22-k7/source  SUBDIRS=/home/myself/downloads/^src/dvb-kernel/build-2.6 AV7110_FIRMWARE= AV7110_OSD=y
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-22-k7'
  LD      /home/myself/downloads/^src/dvb-kernel/build-2.6/built-in.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/version_check.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/flexcop-pci.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/flexcop-usb.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/flexcop.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/flexcop-fe-tuner.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/flexcop-i2c.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/flexcop-sram.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/flexcop-eeprom.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/flexcop-misc.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/flexcop-hw-filter.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/flexcop-dma.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dvbdev.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dmxdev.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dvb_demux.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dvb_filter.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dvb_ca_en50221.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dvb_frontend.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dvb_net.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dvb_ringbuffer.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/av7110_hw.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/av7110_v4l.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/av7110_av.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/av7110_ca.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/av7110.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/av7110_ipack.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/av7110_ir.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/a800.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/cxusb.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dibusb-common.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dibusb-mb.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dibusb-mc.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/digitv.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dtt200u.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dtt200u-fe.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/nova-t-usb2.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/umt-010.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/vp702x.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/vp702x-fe.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/vp7045.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/vp7045-fe.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-usb-firmware.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-usb-init.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-usb-urb.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-usb-i2c.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-usb-dvb.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-usb-remote.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/saa7146_i2c.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/saa7146_core.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/saa7146_vv_ksyms.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/saa7146_fops.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/saa7146_video.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/saa7146_hlp.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/saa7146_vbi.o
  LD [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/saa7146.o
  LD [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/saa7146_vv.o
  LD [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-core.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-pll.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/stv0299.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/sp8870.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/cx22700.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/at76c651.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/cx24110.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/cx24123.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/tda8083.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/l64781.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/mt312.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/mt352.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/ves1820.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/ves1x93.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/tda1004x.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/sp887x.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/nxt6000.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/nxt2002.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/nxt200x.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/cx22702.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/tda80xx.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dvb_dummy_fe.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/tda10021.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/stv0297.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/or51211.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/or51132.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dib3000-common.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dib3000mb.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dib3000mc.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/bcm3510.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/s5h1420.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/lgdt330x.o
  LD [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/b2c2-flexcop.o
  LD [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/b2c2-flexcop-pci.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/stv0297_cs2.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dst.o
In file included from /home/myself/downloads/^src/dvb-kernel/build-2.6/dst_common.h:28,
                 from /home/myself/downloads/^src/dvb-kernel/build-2.6/dst.c:31:
/home/myself/downloads/^src/dvb-kernel/build-2.6/bt878.h:28:19: error: bt848.h: No such file or directorymake[3]: *** [/home/myself/downloads/^src/dvb-kernel/build-2.6/dst.o] Error 1
make[2]: *** [_module_/home/myself/downloads/^src/dvb-kernel/build-2.6] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-22-k7'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/myself/downloads/^src/dvb-kernel/build-2.6'
make: *** [all] Error 2
myself@home:~/downloads/^src/dvb-kernel$ make
make -C /home/myself/downloads/^src/dvb-kernel/build-2.6
make[1]: Entering directory `/home/myself/downloads/^src/dvb-kernel/build-2.6'
[ -L saa7146_video.c ] || ./getlinks
make -C /lib/modules/2.6.15-22-k7/source  SUBDIRS=/home/myself/downloads/^src/dvb-kernel/build-2.6 AV7110_FIRMWARE= AV7110_OSD=y
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-22-k7'
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dst.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dst_ca.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/bt878.o
  CC [M]  /home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.o
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c: In function &#8216;frontend_init&#8217;:
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:605: error: &#8216;BTTV_DVICO_DVBT_LITE&#8217; undeclared (first use in this function)
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:605: error: (Each undeclared identifier is reported only once
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:605: error: for each function it appears in.)
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:649: error: &#8216;BTTV_AVDVBT_761&#8217; undeclared (first use in this function)
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:653: error: &#8216;BTTV_AVDVBT_771&#8217; undeclared (first use in this function)
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:661: error: &#8216;BTTV_TWINHAN_DST&#8217; undeclared (first use in this function)
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:686: error: &#8216;BTTV_PC_HDTV&#8217; undeclared (first use in this function)
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c: In function &#8216;dvb_bt8xx_probe&#8217;:
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:793: warning: implicit declaration of function &#8216;to_bttv_sub_dev&#8217;
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:793: warning: initialization makes pointer from integer without a cast
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:803: error: dereferencing pointer to incomplete type
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:804: error: dereferencing pointer to incomplete type
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:804: error: dereferencing pointer to incomplete type
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:805: error: dereferencing pointer to incomplete type
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:807: error: dereferencing pointer to incomplete type
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:817: error: &#8216;BTTV_DVICO_DVBT_LITE&#8217; undeclared (first use in this function)
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:840: error: &#8216;BTTV_AVDVBT_761&#8217; undeclared (first use in this function)
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:847: error: &#8216;BTTV_AVDVBT_771&#8217; undeclared (first use in this function)
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:854: error: &#8216;BTTV_TWINHAN_DST&#8217; undeclared (first use in this function)
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:872: error: &#8216;BTTV_PC_HDTV&#8217; undeclared (first use in this function)
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:880: error: dereferencing pointer to incomplete type
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:904: error: dereferencing pointer to incomplete type
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:906: error: dereferencing pointer to incomplete type
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c: At top level:
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:937: error: variable &#8216;driver&#8217; has initializer but incomplete type
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:938: error: unknown field &#8216;drv&#8217; specified in initializer
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:938: error: extra brace group at end of initializer
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:938: error: (near initialization for &#8216;driver&#8217;)
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:947: warning: excess elements in struct initializer
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:947: warning: (near initialization for &#8216;driver&#8217;)
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c: In function &#8216;dvb_bt8xx_init&#8217;:
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:952: warning: implicit declaration of function &#8216;bttv_sub_register&#8217;
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c: In function &#8216;dvb_bt8xx_exit&#8217;:
/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.c:957: warning: implicit declaration of function &#8216;bttv_sub_unregister&#8217;
make[3]: *** [/home/myself/downloads/^src/dvb-kernel/build-2.6/dvb-bt8xx.o] Error 1
make[2]: *** [_module_/home/myself/downloads/^src/dvb-kernel/build-2.6] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-22-k7'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/myself/downloads/^src/dvb-kernel/build-2.6'
make: *** [all] Error 2
myself@home:~/downloads/^src/dvb-kernel$


```

---

### Post by hotcha3 on 2006-05-11
Ok, hope someone from antoher part of the globe can help xD

So i'll copy those two files too, so that i'm at the same step as you...thanks alot for the help man, u can't immagine how desperate i am...

Well, i copied those 2 files to the build-2.6 directory, but it didn't gave me the same error as you :

> sunil@ubuntusun:~/dvb-kernel/build-2.6$ make
[ -L saa7146_video.c ] || ./getlinks
rm -rf video-buf.c
ln -s /lib/modules/2.6.15-22-386/source/drivers/media/video/video-buf.c video-buf.c
make -C /lib/modules/2.6.15-22-386/source  SUBDIRS=/home/sunil/dvb-kernel/build-2.6 AV7110_FIRMWARE= AV7110_OSD=y
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.15-22'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.15-22/Module.symvers
           is missing; modules will have no dependencies and modversions.

make[2]: Atención: El archivo `/home/sunil/dvb-kernel/build-2.6/.version_check.o.cmd' tiene una hora de modificación 4,8e+03 en el futuro
  CC [M]  /home/sunil/dvb-kernel/build-2.6/flexcop-pci.o
  CC [M]  /home/sunil/dvb-kernel/build-2.6/flexcop-usb.o
  CC [M]  /home/sunil/dvb-kernel/build-2.6/flexcop.o
/bin/sh: scripts/genksyms/genksyms: No existe el fichero o el directorio
make[2]: *** [/home/sunil/dvb-kernel/build-2.6/flexcop.o] Error 1
make[1]: *** [_module_/home/sunil/dvb-kernel/build-2.6] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.15-22'
make: *** [all] Error 2

---

### Post by hotcha3 on 2006-05-12
Don't worry anymore dude, i finally knew that i didn't have to compile (the guides i saw where older than the kernel). It was a firmware issue, i didn't know that in dapper the firmware folder changes. I put the firmware in the right folder (/lib/firmware/2.6.15.22) and the blue light of the avertv dvb was on. 

The problem now is, how to scan channels, coz kaffeine hasn't found anything, any idea of what should i do before?

---

### Post by louis_nichols on 2006-05-12
That's good news! No need to compile the whole thing anymore. THAT certainly lifts a weight. :)

As for the rest, I have no idea, cause I don't have any device like that. Sorry. Do a search, here on the forum. You should sind something.

---

### Post by hotcha3 on 2006-05-12
I'll try to, but the most importnt thing is done (hope so xD). Thanks for all the help.

---

