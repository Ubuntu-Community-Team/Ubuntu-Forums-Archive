---
title: "a how to for vx-6000 lifecam"
date: 2009-04-06
forum: General Help
---

### Post by sdowney717 on 2009-04-06
Bus 004 Device 005: ID 045e:00f4 Microsoft Corp. LifeCam VX-6000.

after much searching, I came across this way to get it to work.
And it works in skype. I am running intrepid 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/56171](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/56171)
```


I was able to get my VX-6000 to work on Jaunty using the Microdia driver built from git. Looks like Ubuntu kernel devs wants the microdia driver merged upstream though so they don't have to maintain it out-of-tree. So, for this bug to become fixed what needs to happen is that the microdia git tree needs to be merged into Linus's mainline kernel.

Basically, what I did was:

1. if the webcam is connected, disconnect it temporarily
2. install git and run "git clone http://repo.or.cz/r/microdia.git" to get the source code
3. cd into the directory and type make (you must have kernel headers and build tool installed ofc)
4. run "sudo insmod ./sn9c20x.ko"
5. connect the webcam to a proper USB port on the back of the PC (at first I used an USB connector on my keyboard and that printed some error in dmesg about "insufficient power").
6. the /dev/video0 device becomes available right away when you connect the cable and dmesg prints "SN9C20X USB 2.0 Webcam - 045E:00F4 plugged-in".

I posted some more notes about it along with dmesg output etc here:
https://bugs.edge.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87054/comments/27

```

make sure you have the camera unplugged before you run insmod or it wont work

dmesg output after you run "sudo insmod ./sn9c20x.ko"

```
40569.183776] usbcore: registered new interface driver sn9c20x
[40569.185935] sn9c20x: SN9C20x USB 2.0 Webcam Driver v2009.01 loaded
[40574.980055] usb 1-6: new high speed USB device using ehci_hcd and address 4
[40575.145841] usb 1-6: configuration #1 chosen from 1 choice
[40575.147179] sn9c20x: SN9C20X USB 2.0 Webcam - 045E:00F4 plugged-in.
[40575.289901] sn9c20x: Detected OV9650 Sensor.
[40575.291274] sn9c20x: Webcam device 045E:00F4 is now controlling video device /dev/video1
[40575.300815] input: SN9C20X Webcam as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/input/input6
[40575.342441] sn9c20x: Using yuv420 output format
[40575.394767] 4:2:1: cannot get freq at ep 0x84
[40576.427009] 4:2:1: cannot get freq at ep 0x84

```

this link gives a lot more info and number 7 shows you how to make this work every time you boot up

[http://groups.google.com/group/microdia/web/testing-microdia-driver-draft](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft)

```
7. Installing the Microdia Driver

This step is optional. If you don't do it though you will have to insmod sn9c20x.ko everytime you reboot.


# strip -g sn9c20x.ko
# mkdir -p /lib/modules/`uname -r`/kernel/drivers/media/video/usbvideo/
# cp sn9c20x.ko /lib/modules/`uname -r`/kernel/drivers/media/video/usbvideo/
# depmod -a

```

---

### Post by sdowney717 on 2009-04-06
dont use esycam2 it must be loading a module that intereferes with the one from git

also easycam2 looks like it might work as it seems to identfy the camera, I Tried it and for me it did not work.

Just do a complete remove for easycam with configuration and then you can reload the microdia driver you compiled from git

---

