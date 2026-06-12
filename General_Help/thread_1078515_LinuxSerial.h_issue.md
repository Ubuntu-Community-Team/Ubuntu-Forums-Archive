---
title: "Linux/Serial.h issue"
date: 2009-02-23
forum: General Help
---

### Post by TWarn on 2009-02-23
Hi:

I am fairly new to Linux.  I have an issue trying to compile a ftdi_sio usb serial driver.  The Linux/usb/serial.h header does not contain the correct structures for usb_serial_driver structure as well as other definitions.  I copies the linux/usb/serial.h from a Kubuntu 2.6.24-23-generic and the driver compiled (but doesn't work of course).  Is there a patch for this or a new serial.h?

Thanks for the help
Ted

---

### Post by geraldm on 2009-02-23
It should not be necessary to write a driver for that device, unless it is for some special case.  
The header to use would be found in the libusb  package, named usb.h
I do not have ftdi type, my serial device was made by Prolific, and the generic usb device picks it up OK.

regards,
Gerald

---

### Post by TWarn on 2009-02-23
Thanks for the help.  Yes I need to have a odd-ball baurdrate and must compile the driver.  I will look for the libusb and us the usb.h.  If it works I'll let you know.

Thanks again
Ted

---

### Post by TWarn on 2009-02-23
HI:

I looked at the USB.h and the definitions were not there.

Here is the compiler output

pie@pie-desktop:/lib/modules/2.6.27-11-generic/build/drivers/usb/serial$ sudo make
make -C /lib/modules/2.6.27-11-generic/build SUBDIRS=/usr/src/linux-headers-2.6.27-11/drivers/usb/serial modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /usr/src/linux-headers-2.6.27-11/drivers/usb/serial/ftdi_sio.o
ftdi_sio.c:659: error: unknown field num_interrupt_in specified in initializer
ftdi_sio.c:660: error: unknown field num_bulk_in specified in initializer
ftdi_sio.c:660: warning: missing braces around initializer
ftdi_sio.c:660: warning: (near initialization for ftdi_sio_device.driver_list)
ftdi_sio.c:660: warning: initialization makes pointer from integer without a cast
ftdi_sio.c:661: error: unknown field num_bulk_out specified in initializer
ftdi_sio.c:661: warning: initialization makes pointer from integer without a cast
ftdi_sio.c:666: warning: initialization from incompatible pointer type
ftdi_sio.c:667: warning: initialization from incompatible pointer type
ftdi_sio.c:668: warning: initialization from incompatible pointer type
ftdi_sio.c:669: warning: initialization from incompatible pointer type
ftdi_sio.c:670: warning: initialization from incompatible pointer type
ftdi_sio.c:671: warning: initialization from incompatible pointer type
ftdi_sio.c:672: warning: initialization from incompatible pointer type
ftdi_sio.c:675: warning: initialization from incompatible pointer type
ftdi_sio.c:676: warning: initialization from incompatible pointer type
ftdi_sio.c:677: warning: initialization from incompatible pointer type
ftdi_sio.c:678: warning: initialization from incompatible pointer type
ftdi_sio.c:679: warning: initialization from incompatible pointer type
ftdi_sio.c: In function get_ftdi_divisor:
ftdi_sio.c:882: error: struct usb_serial_port has no member named tty
ftdi_sio.c:961: error: struct usb_serial_port has no member named tty
ftdi_sio.c: In function set_serial_info:
ftdi_sio.c:1015: error: struct usb_serial_port has no member named tty
ftdi_sio.c:1021: error: struct usb_serial_port has no member named tty
ftdi_sio.c:1023: error: struct usb_serial_port has no member named tty
ftdi_sio.c:1025: error: struct usb_serial_port has no member named tty
ftdi_sio.c:1027: error: struct usb_serial_port has no member named tty
ftdi_sio.c:1029: error: struct usb_serial_port has no member named tty
ftdi_sio.c: In function ftdi_open:
ftdi_sio.c:1418: error: struct usb_serial_port has no member named tty
ftdi_sio.c:1419: error: struct usb_serial_port has no member named tty
ftdi_sio.c:1433: error: struct usb_serial_port has no member named tty
ftdi_sio.c:1434: error: struct usb_serial_port has no member named tty
ftdi_sio.c: In function ftdi_close:
ftdi_sio.c:1472: error: struct usb_serial_port has no member named tty
ftdi_sio.c: In function ftdi_read_bulk_callback:
ftdi_sio.c:1730: error: struct usb_serial_port has no member named open_count
ftdi_sio.c:1733: error: struct usb_serial_port has no member named tty
ftdi_sio.c: In function ftdi_process_read:
ftdi_sio.c:1786: error: struct usb_serial_port has no member named open_count
ftdi_sio.c:1789: error: struct usb_serial_port has no member named tty
ftdi_sio.c:1937: error: struct usb_serial_port has no member named open_count
ftdi_sio.c:1950: error: struct usb_serial_port has no member named open_count
ftdi_sio.c: In function ftdi_set_termios:
ftdi_sio.c:2005: error: struct usb_serial_port has no member named tty
ftdi_sio.c:2020: error: struct usb_serial_port has no member named tty
ftdi_sio.c: In function ftdi_init:
ftdi_sio.c:2316: warning: too many arguments for format
make[2]: *** [ftdi_sio.o] Error 1
make[1]: *** [_module_/usr/src/linux-headers-2.6.27-11/drivers/usb/serial] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [default] Error 2
pie@pie-desktop:/lib/modules/2.6.27-11-generic/build/drivers/usb/serial$ 
pie@pie-desktop:/lib/modules/2.6.27-11-generic/build/drivers/usb/serial$ 

The thing that gets me is that is I substitute the serial.h from the Kubuntu 8.04 version, the file will compile, it just doesn't work.

Thanks again for your help
Ted

---

### Post by geraldm on 2009-02-23
usb.h is for out-of-kernel user-space programs.
You are using ftdi_sio.c in the kernel.  Use the version that comes with your kernel source.  Mixing different kernel version files would be just asking for trouble. 

regards, 
Gerald

---

