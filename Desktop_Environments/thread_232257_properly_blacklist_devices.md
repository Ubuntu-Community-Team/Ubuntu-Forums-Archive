---
title: "properly blacklist devices"
date: 2006-08-08
forum: Desktop Environments
---

### Post by Pridkett on 2006-08-08
Hi folks,

I've got a linux system with 2x pcHDTV HD-3000 tuner cards in it.  By and large they work pretty well, but the problem is that Ubuntu keeps on installing the Video 4 Linux NTSC drivers also.  I've tried blacklisting stuff to no avail.  Here's the basic gist:

For the pcHTDV there are two sets of drivers, one for hdtv, cx88_dvb, and one for standard definition (cx8800, bttv, etc).  When I boot 2.6.15-26, it properly detects and installs the modules for the cards to work in HDTV mode but then it also installs the standard def modules too.

Here's the output of my lsmod related to the issue:
```
patrick@spongebob:~$ lsmod | egrep "(bttv|cx88)"
cx8800                 34828  0
v4l1_compat            15620  1 cx8800
bttv                  173456  0
v4l2_common             6336  2 cx8800,bttv
cx88_dvb               10884  0
cx8802                 12996  1 cx88_dvb
cx88xx                 64288  3 cx8800,cx88_dvb,cx8802
i2c_algo_bit           10120  3 bttv,ivtv,cx88xx
ir_common              10308  1 cx88xx
btcx_risc               5512  4 cx8800,bttv,cx8802,cx88xx
tveeprom               15504  2 bttv,cx88xx
mt352                   7492  1 cx88_dvb
or51132                10884  1 cx88_dvb
video_buf_dvb           7172  1 cx88_dvb
video_buf              23108  6 cx8800,bttv,cx88_dvb,cx8802,cx88xx,video_buf_dvb
nxt200x                16132  1 cx88_dvb
videodev               10368  4 cx8800,bttv,ivtv,cx88xx
lgdt330x                8796  1 cx88_dvb
cx22702                 7236  1 cx88_dvb
dvb_pll                11332  4 cx88_dvb,or51132,nxt200x,cx22702
i2c_core               23168  22 bttv,lirc_i2c,i2c_acpi_ec,eeprom,w83627hf,i2c_isa,tda9887,msp3400,saa7115,tuner,nvidia,ivtv,cx88_dvb,cx88xx,i2c_algo_bit,tveeprom,mt352,or51132,i2c_nforce2,nxt200x,lgdt330x,cx22702
```

And the contents of my /etc/modprobe.d/blacklist file related to all this:

```
# don't load the cx8800 drivers
blacklist cx8800
blacklist cx88_blackbird
blacklist bttv
```

You'll notice that NOTHING depends on the bttv driver, but somehow it still managed to wiggle in there and get loaded.  Bad driver, Bad!

Here's the context of my dmesg about the time it's loading:
```
[17179599.284000] eth0: no IPv6 routers present
[17179601.804000] lirc_dev: IR Remote Control driver registered, at major 61
[17179601.816000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[17179601.848000] bttv: driver version 0.9.16 loaded
[17179601.848000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179601.880000] cx2388x v4l2 driver version 0.0.5 loaded
[17179601.880000] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 82
[17179601.880000] cx88[0]/0: found at 0000:01:07.0, rev: 5, irq: 82, latency: 32, mmio: 0xf8000000
[17179601.884000] cx88[0]/0: registered device video1 [v4l2]
[17179601.884000] cx88[0]/0: registered device vbi1
[17179601.884000] cx88[0]/0: registered device radio0
[17179601.884000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 90
[17179601.884000] cx88[1]/0: found at 0000:01:08.0, rev: 5, irq: 90, latency: 32, mmio: 0xfa000000
[17179601.888000] cx88[1]/0: registered device video2 [v4l2]
[17179601.888000] cx88[1]/0: registered device vbi2
[17179601.888000] cx88[1]/0: registered device radio1
[17179601.932000] lirc_i2c: chip found @ 0x18 (Hauppauge IR)
[17179601.932000] ivtv0: i2c attach to card #0 ok [client=Hauppauge IR, addr=18]
[17179601.932000] lirc_dev: lirc_register_plugin: sample_rate: 10
```

Judging by the fact that it's sandwiched between a bunch of lirc stuff, I might guess it has something to do with my lirc driver, however there are no module dependencies listed there.

This leaves me wondering, where in the world is the system getting the crazy idea to load the bttv and cx8800 drivers?  Is there a way to do a more in depth trace of this?  Having the drivers loaded ends up causing problems.  And while I realize that I can add an init.d script at slot 99 that removes the drivers, it's less than an ideal method.

Any hints on tracking the source of this mystery module loading or how I can stop it in the future?

Thanks!

---

### Post by Schugy on 2007-10-14
I still have a similar problem in Dapper.
I have created a new initramfs without these undesired dvb-frontends, I have blacklisted them but they still are loaded.
The same is valid for the ACPI-modules. And there is even a config file in /etc/default that should prevent this.

---

