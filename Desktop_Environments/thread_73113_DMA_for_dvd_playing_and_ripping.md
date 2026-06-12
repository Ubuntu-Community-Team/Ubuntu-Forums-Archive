---
title: "DMA for dvd playing and ripping"
date: 2005-10-08
forum: Desktop Environments
---

### Post by stoeptegel on 2005-10-08
I have problems getting DMA to work on my box. The dvd drive is a Benq DW1620 pro. Reason why a wanna activate DMA is because when i play a dvd the movie shocks on my screen. I assume ripping a dvd will also make bad performence when DMA not enabled, of course this is also a thing i want to be able to do on my ubuntu box.

This is my problem:
```
$ sudo hdparm -d1 /dev/hdc
Password:

/dev/hdc:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)
```

---

### Post by b34r on 2005-10-08
What does hdparm -I /dev/hdc say ?
Is it a custom kernel ?

---

### Post by stoeptegel on 2005-10-08
```
sudo hdparm -I /dev/hdc
Password:

/dev/hdc:

ATAPI CD-ROM, with removable media
        Model Number:       BENQ    DVD DD DW1620
        Serial Number:
        Firmware Revision:  B7V9
Standards:
        Likely used CD-ROM ATAPI-1
Configuration:
        DRQ response: 50us.
        Packet size: 12 bytes
Capabilities:
        LBA, IORDY(cannot be disabled)
        DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns
HW reset results:
        CBLID- above Vih
        Device num = 1

```

Nope not that i am aware of, it's one of synaptic general kernels.

---

### Post by stoeptegel on 2005-10-20
My problem has apparently been solved since i installed breezy.

---

