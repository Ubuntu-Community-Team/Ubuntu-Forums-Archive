---
title: "IRDA recognized by kernel, but cannot find it in /dev"
date: 2005-10-13
forum: Desktop Environments
---

### Post by SOMNIVM on 2005-10-13
I have installed Breezy on my laptop, it has found the irda, but I don't know where to find it in /dev - there are no ircomm* devices, and ttyS0 (where it should be, because it's installed as 1st serial port) doesn't work. :confused: 
I wonder what device irdadump uses to show me this - it finds my mobile phone:
[I]somnivm@cyberamphibia:~$ sudo irdadump
21:22:15.348958 xid:cmd b44cbbb1 > ffffffff S=6 s=2 (14)
21:22:15.438580 xid:cmd b44cbbb1 > ffffffff S=6 s=3 (14)
21:22:15.528564 xid:cmd b44cbbb1 > ffffffff S=6 s=4 (14)
21:22:15.618547 xid:cmd b44cbbb1 > ffffffff S=6 s=5 (14)
21:22:15.704299 xid:rsp b44cbbb1 < 04383910 S=6 s=5 SIEMENS CX65 hint=b124 [ PnP Modem Fax IrCOMM IrOBEX ] (29)
21:22:15.708535 xid:cmd b44cbbb1 > ffffffff S=6 s=* cyberamphibia hint=0400 [ Computer ] (29)
[/I]
And then I took a look at lsmod | grep ir
[I]nsc_ircc               19132  0
irtty_sir               7808  0
sir_dev                17324  1 irtty_sir
irda                  159804  3 nsc_ircc,irtty_sir,sir_dev
crc_ccitt               2176  1 irda[/I]
I've tried to make ircomm* in /dev with mknod - they don't work  neither.
I have no idea where the irda port could be accessible...Does anyone have any idea?

---

### Post by mlomker on 2005-10-13
I don't have a reason to use mine, but I always assumed that it was the serial-port/tty that I get in dmesg:

```

mlomker@mlomkernote:~$ dmesg | grep tty
[   16.732087] ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A

```

---

