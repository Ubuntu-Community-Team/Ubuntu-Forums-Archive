---
title: "How can I set up KVM to use alsa or pulseaudio?"
date: 2009-01-17
forum: General Help
---

### Post by chrroessner on 2009-01-17
Hi,

I am testing jaunty here, because it seems to have fixed many sound problems I had with hardy and intrepid.

KVM seems to use OSS per default and I could not find out how to configure it using it alsa or better pulseaudio. Is there some option, environment variable, etc. I could set?

At the moment I loaded the snd-oss-* modules to get it working, but would like the asked varinat to get work.

Here my sample WinXP-config:

```
#!/bin/sh

export QEMU_AUDIO_LOG_TO_MONITOR=1

nice -n -10 -- vdekvm -m 1024M -smp 4 \
  -name winxp \
  -boot c \
  -drive file=/dev/vg01/lv_kvm-winxp,boot=on \
  -net nic,vlan=0,macaddr=00:16:36:58:fb:65,model=rtl8139 \
  -net vde,vlan=0,sock=/var/run/vde2/vde0.ctl,port=11 \
  -k de \
  -vnc 127.0.0.1:1 \
  -monitor tcp:127.0.0.1:2024,server,nowait \
  -localtime \
  -soundhw es1370 hda \
  -usb \
  -usbdevice tablet \
  -pidfile /var/run/kvm-winxp.pid \
  -daemonize > /dev/null 2>&1

# vim: ts=2 sw=2 expandtab

```

Any help is welcome. thanks in advance

Christian

Edit:

See [https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/304649/comments/5](https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/304649/comments/5)

---

