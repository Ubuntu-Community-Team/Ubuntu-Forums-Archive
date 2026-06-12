---
title: "Xilinx ISE 13.2 iMPACT and parallel cable"
date: 2013-09-28
forum: Education &amp; Science
---

### Post by mizery on 2013-09-28
Hi everyone!

I'm trying to set up Xilinx ISE 13.2, using a parallel cable bought from eBay: [http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=271075614688](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=271075614688)
I connect it to my laptop running Xubuntu 13.04 using a Prolific usb-to-parallel adapter: [http://www.prolific.com.tw/US/ShowProduct.aspx?p_id=6&pcid=41](http://www.prolific.com.tw/US/ShowProduct.aspx?p_id=6&pcid=41)
ISE itself seems to work just fine, but connecting to the FPGA through iMPACT is not quite working.

I'm using the libusb-driver from [http://rmdir.de/~michael/xilinx/](http://rmdir.de/~michael/xilinx/), and this is what I do to run iMPACT:
```

cd ~/ISE/usb-driver/
make
export LD_PRELOAD=/home/tausen/ISE/usb-driver/libusb-driver.so
. /opt/Xilinx/13.2/ISE_DS/settings64.sh
./setup_pcusb
impact

```

When plugging in the cable and running dmesg i get:
```

[ 5415.553300] usb 3-1: new full-speed USB device number 12 using xhci_hcd
[ 5415.570393] usb 3-1: New USB device found, idVendor=067b, idProduct=2305
[ 5415.570401] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 5415.570405] usb 3-1: Product: IEEE-1284 Controller
[ 5415.570408] usb 3-1: Manufacturer: Pr\xffffffe3\xffffff81\xffffffaf\xffffff81\xffffffaflific Technology Inc.
[ 5415.571322] usblp 3-1:1.0: usblp1: USB Bidirectional printer dev 12 if 0 alt 1 proto 2 vid 0x067B pid 0x2305

```
And this device shows up in /dev/usb:
```

crw-rw---- 1 root lp   180, 1 Sep 28 13:04 lp1

```

When I run iMPACT and do cable auto-connect, I get this:
```

AutoDetecting cable. Please wait.
PROGRESS_START - Starting Operation.
 Using windrvr6 driver.
Connecting to cable (Usb Port - USB21).
Checking cable driver.
File version of /opt/Xilinx/13.2/ISE_DS/ISE/bin/lin64/xusbdfwu.hex = 1030.
File version of /usr/share/xusbdfwu.hex = 1030.
 libusb-driver.so version: 2013-09-26 18:09:48.
Cable connection failed.
Connecting to cable (Parallel Port - parport0).
 libusb-driver.so version: 2013-09-26 18:09:48.
 parport0: 
 parport1: 
 parport2: 
 parport3: 
 LPT1 Base Address set from env variable = 0.
 LPT base address = 0000h.
 LPT1 Ecp Address set from env variable = 400.
 ECP base address = 0400h.
LPT port is already in use. rc = FFFFFFFFh
Cable connection failed.
Connecting to cable (Parallel Port - parport1).
 libusb-driver.so version: 2013-09-26 18:09:48.
 LPT2 Base Address set from env variable = 10.
 LPT base address = 0010h.
 LPT2 Ecp Address set from env variable = 410.
 ECP base address = 0410h.
LPT port is already in use. rc = FFFFFFFFh
Cable connection failed.
Connecting to cable (Parallel Port - parport2).
 libusb-driver.so version: 2013-09-26 18:09:48.
 LPT3 Base Address set from env variable = 20.
 LPT base address = 0020h.
 LPT3 Ecp Address set from env variable = 420.
 ECP base address = 0420h.
LPT port is already in use. rc = FFFFFFFFh
Cable connection failed.
Connecting to cable (Parallel Port - parport3).
 libusb-driver.so version: 2013-09-26 18:09:48.
 LPT4 Base Address set from env variable = 30.
 LPT base address = 0030h.
 LPT4 Ecp Address set from env variable = 430.
 ECP base address = 0430h.
LPT port is already in use. rc = FFFFFFFFh
Cable connection failed.
PROGRESS_END - End Operation.
Elapsed time =      2 sec.
Cable autodetection failed.

```

And in the terminal, I see:
```

Can't open /dev/parport0: No such file or directory
Can't open /dev/parport1: No such file or directory
Can't open /dev/parport2: No such file or directory
Can't open /dev/parport3: No such file or directory

```

If I open cable setup and choose parallel cable III or IV, the "port" dropdown is empty. I suspect I could specify the port parameters through the "cable plug-in" option if I had any idea what I'm doing.

I also tried making a symlink from /dev/usb/lp1 to /dev/parport0 to no avail - I get pretty much the same result:
```

Connecting to cable (Parallel Port - parport0).
 libusb-driver.so version: 2013-09-26 18:09:48.
 LPT1 Base Address set from env variable = 0.
 LPT base address = 0000h.
 LPT1 Ecp Address set from env variable = 400.
 ECP base address = 0400h.
LPT port is already in use. rc = FFFFFFFFh

```
But no "no such file or directory" in the terminal (for any parportN).

I wonder if I can specify the base address and ecp address properly, somehow?

I've installed fxload libusb-dev and build-essential and my user is in the lp group.

If anyone has any idea how to proceed or debug this issue, I'd be very happy for some input :)

---

