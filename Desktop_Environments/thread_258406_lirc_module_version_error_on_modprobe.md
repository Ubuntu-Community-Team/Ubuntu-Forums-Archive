---
title: "lirc module version error on modprobe"
date: 2006-09-15
forum: Desktop Environments
---

### Post by tytus on 2006-09-15
I am runnin Ubuntu 6.06 with standard kernel 2.6.15-26-amd64-generic. I have installed lirc 0.8.0 from source as suggestged by Hyams Mythtv howto 
[http://hyams.webhop.net/mythtv/myth_ubuntu.html]("http://hyams.webhop.net/mythtv/myth_ubuntu.html")
Everhing went smoothly until I tried to load the module:
```
# modprobe lirc_i2c
#dmesg
```


```
[  165.198239] lirc_dev: IR Remote Control driver registered, at major 61 
[  165.204068] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[  165.273220] bttv: disagrees about version of symbol tveeprom_hauppauge_analog
[  165.273227] bttv: Unknown symbol tveeprom_hauppauge_analog
[  165.312700] cx88xx: disagrees about version of symbol tveeprom_hauppauge_analog
[  165.312706] cx88xx: Unknown symbol tveeprom_hauppauge_analog
[  165.318954] cx8800: Unknown symbol cx88_reset
[  165.319001] cx8800: Unknown symbol cx88_call_i2c_clients
[  165.319028] cx8800: Unknown symbol cx88_wakeup
[  165.319081] cx8800: Unknown symbol cx88_risc_stopper
[  165.319115] cx8800: Unknown symbol cx88_print_irqbits
[  165.319142] cx8800: Unknown symbol cx88_set_scale
[  165.319176] cx8800: Unknown symbol cx88_shutdown
[  165.319219] cx8800: Unknown symbol cx88_vdev_init
[  165.319271] cx8800: Unknown symbol cx88_core_put
[  165.319309] cx8800: Unknown symbol cx88_audio_thread
[  165.319352] cx8800: Unknown symbol cx88_core_irq
[  165.319387] cx8800: Unknown symbol cx88_core_get
[  165.319413] cx8800: Unknown symbol cx88_get_stereo
[  165.319480] cx8800: Unknown symbol cx88_set_tvnorm
[  165.319529] cx8800: Unknown symbol cx88_risc_buffer
[  165.319617] cx8800: Unknown symbol cx88_set_stereo
[  165.319715] cx8800: Unknown symbol cx88_sram_channels
[  165.319760] cx8800: Unknown symbol cx88_set_tvaudio
[  165.319786] cx8800: Unknown symbol cx88_sram_channel_dump
[  165.319825] cx8800: Unknown symbol cx88_sram_channel_setup
[  165.319854] cx8800: Unknown symbol cx88_print_ioctl
[  165.319897] cx8800: Unknown symbol cx88_free_buffer
[  165.319922] cx8800: Unknown symbol cx88_boards
[  165.320058] cx8800: Unknown symbol cx88_newstation
[  165.333049] lirc_i2c: chip found @ 0x18 (Hauppauge IR)
[  165.333220] ivtv0: i2c attach to card #0 ok [client=Hauppauge IR, addr=18]
[  165.333707] lirc_dev: lirc_register_plugin: sample_rate: 10

```

I tried running lircd and irw but irw fails. It just exits...

Anybody can tell me what is the problem with "unknow symbol" messages from dmesg? I am relatively new to linux.


Thanks in advance

---

### Post by skattman83 on 2006-09-19
I'm having the same issue.  I'm using a Hauppauge PVR-150 and LIRC 0.8.0 if that helps any.

---

### Post by Prefader on 2006-09-19
Same errors here.
Any help would be GREATLY appreciated.

---

### Post by madscientist on 2006-09-20
Generally this means that your module is trying to access some portion of the kernel which is not available.  Normally that is because your kernel config has not enabled whatever is needed in its configuration.  I often grep for a missing symbol in the source code for the kernel, then try to figure out which CONFIG_* option controls that code.

In this case, it appears that your module wants to access code from the cx88 module, controlled by the config option CONFIG_VIDEO_CX88.  This is "v4l2 device driver for cx2388x based TV cards".  First check if that option is enabled in your kernel (you can look in the /boot/config-`uname -r` file if you've used normal Ubuntu methods to build your kernel (make-kpkg etc.)).  If not, you'll need to enable that option and rebuild your kernel.  If it is enabled already, then it looks like that module is not loaded.  Try running "insmod cx8800" and see if that works.

---

### Post by tytus on 2006-09-24
CONFIG_VIDEO_CX88 is enabled in my config. When I try to load the module however, I am getting errors:
```
root@mythv:/usr/src/lirc-0.8.0# modprobe cx8800
WARNING: Error inserting cx88xx (/lib/modules/2.6.15-26-amd64-generic/kernel/drivers/media/video/cx88/cx88xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting cx8800 (/lib/modules/2.6.15-26-amd64-generic/kernel/drivers/media/video/cx88/cx8800.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```
And dmesg gives me the following:

```
[ 2277.980514] cx88xx: disagrees about version of symbol tveeprom_hauppauge_analog
[ 2277.980946] cx88xx: Unknown symbol tveeprom_hauppauge_analog
[ 2277.982121] cx8800: Unknown symbol cx88_reset
[ 2277.982448] cx8800: Unknown symbol cx88_call_i2c_clients
[ 2277.982719] cx8800: Unknown symbol cx88_wakeup
[ 2277.982981] cx8800: Unknown symbol cx88_risc_stopper
[ 2277.983244] cx8800: Unknown symbol cx88_print_irqbits
[ 2277.983504] cx8800: Unknown symbol cx88_set_scale
[ 2277.983757] cx8800: Unknown symbol cx88_shutdown
[ 2277.984146] cx8800: Unknown symbol cx88_vdev_init
[ 2277.984427] cx8800: Unknown symbol cx88_core_put
[ 2277.984680] cx8800: Unknown symbol cx88_audio_thread
[ 2277.984960] cx8800: Unknown symbol cx88_core_irq
[ 2277.985211] cx8800: Unknown symbol cx88_core_get
[ 2277.985453] cx8800: Unknown symbol cx88_get_stereo
[ 2277.985738] cx8800: Unknown symbol cx88_set_tvnorm
[ 2277.986009] cx8800: Unknown symbol cx88_risc_buffer
[ 2277.986323] cx8800: Unknown symbol cx88_set_stereo
[ 2277.986643] cx8800: Unknown symbol cx88_sram_channels
[ 2277.986921] cx8800: Unknown symbol cx88_set_tvaudio
[ 2277.987160] cx8800: Unknown symbol cx88_sram_channel_dump
[ 2277.987445] cx8800: Unknown symbol cx88_sram_channel_setup
[ 2277.987723] cx8800: Unknown symbol cx88_print_ioctl
[ 2277.988022] cx8800: Unknown symbol cx88_free_buffer
[ 2277.988275] cx8800: Unknown symbol cx88_boards
[ 2277.988620] cx8800: Unknown symbol cx88_newstation

```

---

### Post by bihe on 2006-11-24
Same error here:

my solution was to remove the tveeprom.ko module from /lib/modules/2.6.15-27-386/kernel/drivers/media/video/
(ivtv brings it's own version)

depmod -ae

and ready

---

