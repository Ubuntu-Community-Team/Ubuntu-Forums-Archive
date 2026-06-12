---
title: "GPIB-USB-HS on 14.04"
date: 2015-03-25
forum: Education &amp; Science
---

### Post by thomas48 on 2015-03-25
Hi all,

I am new with Ubuntu.

I am trying to make GPIB-USB-HS work with 14.04.

So far I have done the following:

1) Downloaded linux-gpib from

[HTML]http://sourceforge.net/projects/linux-gpib/files/linux-gpib%20for%203.x.x%20and%202.6.x%20kernels/3.2.21/[/HTML]

then

```
  
cd Downloads/ 
tar -xzf sourcetarball.tar.gz
cd linux-gpib-3.2.21/
sudo su
./configure
make
make install

```

but then when I try

```
 gpib_config 
```

I get

```


failed to configure boardtype: ni_usb_gpib
failed to configure board
main: Invalid argument


```

If i type

```
lsusb
```

i get 

```

Bus 001 Device 004: ID 3923:709b National Instruments Corp. GPIB-USB-HS

```

Then if I go to the test directory in the linux-gpib-3.2.21 folder and type

```
./libgpib_test
```

i get:

```

Finding board...libgpib: error in is_system_controller()!
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
libgpib: invalid descriptor
FAILED: libgpib_test.c line 163, ibsta 0x8000, iberr 0, ibcntl 22


```

Finally if I say:

```
dmesg
```

I get the following:


```
[  411.894111] gpib: registered lpvo_usb_gpib interface
[  411.894116] lpvo_usb_gpib:usb_gpib_init_module - done
[  981.799353] gpib: no gpib board configured on /dev/gpib0
[  981.799366] gpib: no gpib board configured on /dev/gpib0
[  981.799370] gpib: no gpib board configured on /dev/gpib0
[ 1289.303558] gpib: no gpib board configured on /dev/gpib0
[ 1289.303583] gpib: no gpib board configured on /dev/gpib0
[ 1289.303594] gpib: no gpib board configured on /dev/gpib0
[ 2339.752405] perf interrupt took too long (2518 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[ 4967.261157] gpib: no gpib board configured on /dev/gpib0
[ 4967.261183] gpib: no gpib board configured on /dev/gpib0


```

I have been looking around and maybe I have messed it up a bit but I couldn't solve this problem!

Any help would be very much appreciated


Thank you very much for your help and time.

---

### Post by thomas48 on 2015-03-27
Hi again!

I came across this very useful link:

[HTML]http://4hv.org/e107_files/public/1163365705_65_FT17832_linuxgpib.pdf[/HTML]

basically I have used the wrong driver. The (wrong) driver I have been using is shown in

```
[  411.894111] gpib: registered lpvo_usb_gpib interface
[  411.894116] lpvo_usb_gpib:usb_gpib_init_module - done
```

The lpvo_usb_gpib.ko driver is not the correct one. So i had to use ni_usb_gpib.ko (according to the above link). In order to do so I typed:

```
modprobe ni_usb_gpib
```

Then I had to change the board type in the gpib.conf file: 

```
cd etc/
gedit gpib.conf
```

The board_type entry according to the same link i posted above, has to be changed to board_type = "ni_usb_b" 

```
interface {
    minor = 0    /* board index, minor = 0 uses /dev/gpib0, minor = 1 uses /dev/gpib1, etc. */
    board_type = "ni_usb_b"    /* type of interface board being used */
    name = "violet"    /* optional name, allows you to get a board descriptor using ibfind() */
    pad = 0    /* primary address of interface             */
    sad = 0    /* secondary address of interface           */
    timeout = T3s    /* timeout for commands */

    eos = 0x0a    /* EOS Byte, 0xa is newline and 0xd is carriage return */
    set-reos = yes    /* Terminate read if EOS */
    set-bin = no    /* Compare EOS 8-bit */
    set-xeos = no    /* Assert EOI whenever EOS byte is sent */
    set-eot = yes    /* Assert EOI with last byte on writes */

/* settings for boards that lack plug-n-play capability */
    base = 0    /* Base io ADDRESS                  */
    irq  = 0    /* Interrupt request level */
    dma  = 0    /* DMA channel (zero disables)      */

/* pci_bus and pci_slot can be used to distinguish two pci boards supported by the same driver */
/*    pci_bus = 0 */
/*    pci_slot = 7 */

    master = yes    /* interface board is system controller */
}
```


After these changes configuration

```
gpib_config
``` 

runs smoothly and when i send an *IDN? with 

```
ibtest
```

 I get a nice reply from my instrument:

```
trying to read 100 bytes from device...
received string: 'THURLBY THANDAR, QL355TP, 429732, 2.05-2.00
'
Number of bytes read: 45
gpib status is: 
ibsta = 0x2100  < END CMPL >
iberr= 0

ibcnt = 45


``` 

  It seems to be working now but when I run my Labview program I get an error after GPIB WRITE:  

```
Error 0 occurred at GPIB Write in Test.vi

Possible reason(s):

LabVIEW:  Error connecting to GPIB driver or device.
```

  This might be a different(?) story. However I will keep this thread [UNSOLVED] for a bit more and hopefully I will close it asap.

Thanks!

---

### Post by tgalati4 on 2015-03-27
What are the switches availabe for the module?

```
modinfo ni_usb_gpib
```

---

### Post by thomas48 on 2015-03-29
Hi tgalati4,

Thank you very much for your reply

I get the following after typing your code:

```
filename:       /lib/modules/3.16.0-33-generic/gpib/ni_usb/ni_usb_gpib.ko
license:        GPL
srcversion:     FFE9016A84E8E2DF192E7F5
alias:          usb:v3923p725Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v3923p725Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v3923p709Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v3923p702Ad*dc*dsc*dp*ic*isc*ip*in*
depends:        gpib_common
vermagic:       3.16.0-33-generic SMP mod_unload modversions 

```

I have installed both NI GPIB drivers and linux-gpib. Should I uninstall NI?

Apparently is a  Labview problem so since the GPIB issue has been solved i am closing this. Labview issues remain unsolved.

---

