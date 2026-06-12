---
title: "Missing joystick input directories??"
date: 2010-12-08
forum: Gaming &amp; Leisure
---

### Post by aj_the_first on 2010-12-08
I am trying to use a game pad (xbox360, PS3, generic USB, etc.) in Ubuntu 10.10, and I was attempting QJoyPad and all sort of other solutions in another thread until someone had me check the input devices, and I came up with this.
My computer has no idea what a joystick is.
Check it out:

andrew@Linus:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:028f Microsoft Corp. Xbox360 Wireless Controller
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
andrew@Linus:~$ ls /dev/input/js*
ls: cannot access /dev/input/js*: No such file or directory
andrew@Linus:~$ ls /dev/input
by-path event1 event3 event5 mice mouse1
event0 event2 event4 event6 mouse0
andrew@Linus:~$ 

Sure enough, the specified js folder/directory does not even exist... This is definitely the point where I have no idea how to proceed.
 I can see that I am missing the actual js directory/folder, but what can I do about that?

I've upgraded my OS online from 9.10 to 10.04 to 10.10.  I REALLY don't want to do a OS fresh install.  I was considering a fresh install of Ubuntu on a spare hard drive just so that I can put the proper directories onto a USB drive, transfer it to my computer, and then change permissions to make it usable, but there MUST be a better way.
Suggestions anyone?

Thanks,
AJ

---

### Post by nicolastraffic1 on 2010-12-08
my pc have no idea . what joystick it is?

---

### Post by aj_the_first on 2010-12-08
> **nicolastraffic1 said:**
> my pc have no idea . what joystick it is?

Read my post.

---

### Post by thatguruguy on 2010-12-08
As I mentioned before, my computer saw my xbox360 controller automagically.  You may want to try the following command:
```
sudo modprobe xpad
```You may also want to check out the following threads:
[http://ubuntuforums.org/showthread.php?t=330607](http://ubuntuforums.org/showthread.php?t=330607)
[http://ubuntuforums.org/showthread.php?t=338457](http://ubuntuforums.org/showthread.php?t=338457)

---

### Post by aj_the_first on 2010-12-09
> **thatguruguy said:**
> As I mentioned before, my computer saw my xbox360 controller automagically.  You may want to try the following command:
```
sudo modprobe xpad
```You may also want to check out the following threads:
[http://ubuntuforums.org/showthread.php?t=330607](http://ubuntuforums.org/showthread.php?t=330607)
[http://ubuntuforums.org/showthread.php?t=338457](http://ubuntuforums.org/showthread.php?t=338457)

Yes, I've tried that unfortunately.  I have xpad, but still nothing is detected other than in the usb list.
I am still looking for jscalibrator.  I didn't think it was needed in 10.10, but the threads seem to say that nothing will work without it.
Is it the missing input libraries?  Does that sound correct?  I mean, if I don't have a joystick input folder, then it really doesn't matter if I have the xpad module, right?

---

### Post by thatguruguy on 2010-12-09
I've never used jscalibrator, so it doesn't appear to be necessary.

Haven't you had other problems relating to your usb controller? It sounds more and more like you may need a fresh install.

---

### Post by lazypower on 2010-12-24
I dont think a fresh install will fix this as I can verify on Ubuntu 10.10 32 bit I am missing the joystick device inodes as well.

---

