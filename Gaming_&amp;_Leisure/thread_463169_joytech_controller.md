---
title: "joytech controller"
date: 2007-06-03
forum: Gaming &amp; Leisure
---

### Post by lowebb on 2007-06-03
Hi guys,

I'm running kubuntu fiesty with an up-to-date kernel and trying to get a usb controller working

I've read all the threads to do with xbox360 controllers on this forum and they all say the joytech controller will work but I cant get mine to work at all. It seems to be recognising the controller but it isnt operating.

When I plug the controller in and look at dmesg I get:

[  125.008000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[  125.220000] usb 1-1: configuration #1 chosen from 1 choice
[  212.304000] usbcore: registered new interface driver xpad
[  212.304000] /home/brendan/.xpad360/xpad360/xpad.c: X-Box pad driver:v0.0.7

The output of lsusb is:

Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 162e:beef
Bus 001 Device 001: ID 0000:0000


The output of lsmod | grep xpad is:

xpad                   10244  0
usbcore               134280  6 xpad,visor,usbserial,ehci_hcd,uhci_hcd

However I dont have a /dev/input/js0 device and the jscalibrate tool cant detect the pad

Any help guys, please!!!

---

### Post by lowebb on 2007-06-04
for the morning crew. any help??

---

### Post by gigaferz on 2007-06-04
jscal /dev/input/js1 -c

or js0

also try jstest

anyway install that package, probably your axis will endup inverted so write down which ones are 

also, it maight not detect it because it might not be in that location just trying to help here...i went trough that and i gave up,,

---

