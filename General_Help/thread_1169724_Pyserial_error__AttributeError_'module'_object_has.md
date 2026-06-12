---
title: "Pyserial error : AttributeError: 'module' object has no attribute 'serial'"
date: 2009-05-25
forum: General Help
---

### Post by bkbn1234 on 2009-05-25
I am having trouble with the pyserial command in python to access the sparkfun GM862 evaluation board connected to the USB on my Ubuntu machine which has the 2.6.29 kernel. I am able to get this to work on my windows machine. Any ideas on why I might be getting this error and how to fix it would be greatly appreciated.
   
   
  Test.py contains these two lines:
  Import serial
  Ser=serial.serial(‘/dev/ttyUSB0’, 9600)
   
  I get the following message:
   
  root@ubuntu:~# python test.py
  Traceback (most recent call last):
    File "test.py", line 2, in <module>
      ser=serial.serial('/dev/ttyUSB0', 9600)
  AttributeError: 'module' object has no attribute 'serial'
   
   
  The device is connected to the linux machine. It shows up in the lsusb and dmesg as shown below:  
   
  root@ubuntu:~# lsusb
  Bus 001 Device 003: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
  Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
   
   
  root@ubuntu:~# dmesg | grep tty
  [    0.004000] console [tty0] enabled
  [    3.961214] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
  [    3.963134] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
  [    4.944190] usb 1-1: generic converter now attached to ttyUSB0
  [12685.672935] generic ttyUSB0: generic converter now disconnected from ttyUSB0
  [62990.174403] usb 1-1: generic converter now attached to ttyUSB0

---

### Post by bkbn1234 on 2009-05-29
In addition to python, I also tried using GTK term. When I tried to configure the /dev/ttyUSB0 port and click OK I get a square box with 0 0 on top line and 1 1 at the bottom line inside the box. the box keeps reprinting as if a key was held down. The only way to stop this was to quit. When I changed the setting in view from asci to hexadecimal I get 11 60 repeating.......

Please let me know if you have any suggestion on getting this ttyusb0 to work.

---

