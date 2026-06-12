---
title: "trust work tablet 400 - need help to get it to work?"
date: 2008-12-14
forum: General Help
---

### Post by simtaalo on 2008-12-14
i have just found the named tablet and wondered if it was possible to get it working. it is apparently a rebranded Aiptek 6000U.

i found this page, but the information seems to be out-of-date.
[http://zeekat.nl/joost/trust-tablet/index.html](http://zeekat.nl/joost/trust-tablet/index.html)

anyone use one of these?

---

### Post by simtaalo on 2008-12-15
i installed this from the repo's xserver-xorg-input-aiptek which should have made a difference but it hasn't.

according to this webpage [http://zeekat.nl/joost/trust-tablet/index.html](http://zeekat.nl/joost/trust-tablet/index.html) i followed the guide of what to add to the xorg.conf but it trashed it so i had to rescue that and put the xorg.conf back to what it was before the addition.

anyone else managed to get one of these tablets working?

---

### Post by DieB on 2008-12-15
checked already here?

[https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet)

if yes i can't help anyfurther, sorry

---

### Post by simtaalo on 2008-12-15
going through that guide now, cheers.

---

### Post by simtaalo on 2008-12-15
i've created the new rules file as instructed here 

```
   2.

      Create an udev rules file called '/etc/udev/rules.d/61-aiptek.rules' and add the following content to it:

      BUS=="usb", DRIVER=="aiptek", KERNEL=="event[0-9]*", SYMLINK+="input/aiptektablet"
      KERNEL=="event[0-9]*", SYSFS{vendor_id}=="0x08ca", SYSFS{product_id}=="0021", SYMLINK+="input/aiptektablet"

Then restart udev with

sudo /etc/init.d/udev restart 
```

but after running the restart command i run
```
ls /dev/input/
```
which outputs
```
by-path  event1  event3  event5  event7  event9  mouse0
event0   event2  event4  event6  event8  mice    mouse1
```

i went onto the troubleshooting page here
[https://help.ubuntu.com/community/AiptekTablet#UDEV-TroubleShooting](https://help.ubuntu.com/community/AiptekTablet#UDEV-TroubleShooting)

but when i run  ```
dmesg | tail
```

i get this output

```
[   67.511546]   groups: 02 01
[   67.511549]   domain 1: span 03
[   67.511550]    groups: 03
[  262.546317] usb 2-1: USB disconnect, address 3
[  265.598563] usb 2-1: new low speed USB device using uhci_hcd and address 4
[  265.840535] usb 2-1: configuration #1 chosen from 1 choice
[  275.202802] /build/buildd/linux-2.6.24/drivers/input/tablet/aiptek.c: input: Aiptek tried all speeds, no sane response
[  275.202850] aiptek: probe of 2-1:1.0 failed with error -12
[  865.285208] intel_rng: FWH not detected
[ 1068.375419] intel_rng: FWH not detected
```

the output doesn't give the reading to carry out the next step.

---

### Post by simtaalo on 2008-12-16
anyone got any ideas?

---

### Post by DieB on 2008-12-16
so u run a version before 8.10, is that right?

there is also an 18 months old one with more detailed instructions (which claims that the aiptek in repos is broke, so that might be agreater help.

[http://ubuntuforums.org/showthread.php?t=122735](http://ubuntuforums.org/showthread.php?t=122735)

sorry if not, i just didn't get to try out mine ;)

---

### Post by simtaalo on 2008-12-16
i'm running 8.04.

i found that other thread and went through the instructions but when making the kernel driver when it came to copying over the old one the directory didn't exist.

it seems the biggest sticking point is the udev rule bit, i've tried several varients of the rules file and none of them work, and as i said above when i tried to go through the troubleshooting bit the output i was getting from a command didn't give me the information i needed to carry out the next step.

thanks for trying DieB, seems everyone else is stumped too. never had a problem post get so many views and hardly any advice :lol:

pretty determined to get it working though, i'm sure theres gotta be a way.

---

### Post by simtaalo on 2008-12-16
when going through the instructions on [http://ubuntuforums.org/showthread.php?t=122735](http://ubuntuforums.org/showthread.php?t=122735)
i get to the step 
```
cp /lib/modules/$(uname -r)/kernel/drivers/usb/input/aiptek.ko aiptek.ko.old

cp: cannot stat `/lib/modules/2.6.24-22-generic/kernel/drivers/usb/input/aiptek.ko': No such file or directory
```

i've searched around but can't see where else the directory could be.

---

### Post by simtaalo on 2008-12-18
ok, so i managed to go through steps 1-6 from this thread [http://ubuntuforums.org/showthread.php?t=122735](http://ubuntuforums.org/showthread.php?t=122735)

when the computer starts up i get the error message
```
USB 1-2: device not accepting address 2, error -71
```
or
```
USB1-1:device descriptor read/all error -71
```

if i run the command
```
ls /dev/input

aiptektablet  by-path  event1   event2  event4  event6  event8  mice    mouse1
by-id         event0   event10  event3  event5  event7  event9  mouse0  mouse2

```

but if i run the command
```
sudo cat /dev/input/aiptektablet 
```

it gives no reaction to the pen.

when i run gimp the device shows up when i goto "input controllers" it's listed, but shows the state of it as "Device not available : Permission denied".

also if i try start the computer without the tablet plugged in it will start in low-graphics mode, my computer is a laptop so its not practical to have the tablet plugged in all the time.

any help?

---

### Post by bmcage on 2008-12-23
What does udevinfo say? 
You really should upgrade to 8.10, then the kernel driver is already included and working. Clearly from your errors it looks like you do not succeed in installing the compiled kernel driver. 
Note that if you follow the other posts guide 1-6, then you obtain driver for linux and X from the sourceforge repo, which is outdated, as the newest version is now in the trees of linux and Xorg.
For 8.10 you follow the community guide and it should work

---

### Post by simtaalo on 2008-12-23
> **bmcage said:**
> What does udevinfo say? 
You really should upgrade to 8.10, then the kernel driver is already included and working....For 8.10 you follow the community guide and it should work

funny you should say that.

3 days ago i installed 8.10 and went through the guide and it didn't work. on the guide it doesn't give any pointers how to troubleshoot if it doesn't work.

do you have any ideas?

---

### Post by bmcage on 2008-12-24
Not very funny I would say myself :-) 

For the kernel driver, in 8.10, lsmod should list it (if not load it), and dmesg should have output that the aiptektablet is there.
Next, read [http://aiptektablet.sourceforge.net/kernel.html](http://aiptektablet.sourceforge.net/kernel.html) and test some of the things there, so eg go into /sys/bus/usb/drivers/aiptek and play with the settings

Also test what usb says, some device codes can be strange and cause things to not work I believe. The command is lsusb

If all above ok, time to go to X settings. Instead of the HAL policy's of the guide, try some things manually. The command is xinput, see the man page. 

If success, please update the community guide to include some of the troubleshooting one can do. Thanks!

---

### Post by simtaalo on 2008-12-24
when i run lsmod i get the following lines with the aiptek 
```
aiptek                 24320  0 
...
usbcore               148848  6 uvcvideo,aiptek,usbhid,ehci_hcd,uhci_hcd

```

output of dmesg
```
 dmesg | grep aiptek
[   22.339246] aiptek: input: Aiptek tried all speeds, no sane response
[   22.339272] aiptek: probe of 1-2:1.0 failed with error -12
[   22.339405] usbcore: registered new interface driver aiptek
[   22.341241] aiptek: v2.3 (May 2, 2007): Bryan W. Headley/Chris Atenasio/Cedric Brun/Rene van Paassen
[   22.341247] aiptek: Aiptek HyperPen USB Tablet Driver (Linux 2.6.x)

```

so it seems like the error -12 is causing the problem?

the output of lsusb is

```
Bus 005 Device 003: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 08ca:0021 Aiptek International, Inc. APT-2 Tablet
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by bmcage on 2009-01-02
Yes, error -12 is the problem.

Looking at the driver code: 
[http://www.google.com/codesearch/p?hl=en#F2YrM2Z3364/trunk/kernel/linux/drivers/input/tablet/aiptek.c&q=aiptek%20sane](http://www.google.com/codesearch/p?hl=en#F2YrM2Z3364/trunk/kernel/linux/drivers/input/tablet/aiptek.c&q=aiptek%20sane)

At line 1828 you see your error being raised. 
Looking at the array speeds, there is a command line override you can try to set up the tablet. Try that, see line 1673 in the driver code.
More info on [http://aiptektablet.sourceforge.net/kernel.html](http://aiptektablet.sourceforge.net/kernel.html) section esoteric features and then read the command line section.
So you must find a delay that works on your tablet, only then you can continue. If you find a delay that works, share it, it should be added to the list of speeds in the kernel driver code.

---

### Post by simtaalo on 2009-01-07
ok, so i looked through the code and the command-line section.

i tried the example line from here [http://aiptektablet.sourceforge.net/kernel.html](http://aiptektablet.sourceforge.net/kernel.html) and got this error
```
depmod aiptek programmableDelay=500
WARNING: Can't read module aiptek: No such file or directory
WARNING: Can't read module programmableDelay=500: No such file or directory
FATAL: Could not open /lib/modules/2.6.27-9-generic/modules.dep.temp for writing: Permission denied

```

---

### Post by bmcage on 2009-01-08
I don't have the aiptek installed at the moment, upgraded some stuff and waiting for kde 4.2 before setting everything up again.

From your line, looking at the kernel page and doing some google, I guess that:

1/aiptek is not build as a dynamically-loadable module so depmod does not work
2/you need to run the command with sudo
3/you should read: man modprobe, man insmod and man modules.conf. The article of aiptek mentions modules.conf, but note [http://www.newlinuxuser.com/reader-question-why-is-there-no-etcmodulesconf-in-ubuntu/](http://www.newlinuxuser.com/reader-question-why-is-there-no-etcmodulesconf-in-ubuntu/) so all is in /etc/modprobe.d/ for ubuntu. 

Ok, I now, not real help, but I believe all the pointers are here to solve it. Without installing aiptek myself again I cannot do more, as the more specific I get the more likely I would be wrong. Best would be if an aiptek user tries to manually set some parameters and writes back on this list

---

### Post by simtaalo on 2009-01-08
> **bmcage said:**
> 
1/aiptek is not build as a dynamically-loadable module so depmod does not work
2/you need to run the command with sudo
3/you should read: man modprobe, man insmod and man modules.conf. The article of aiptek mentions modules.conf, but note [http://www.newlinuxuser.com/reader-question-why-is-there-no-etcmodulesconf-in-ubuntu/](http://www.newlinuxuser.com/reader-question-why-is-there-no-etcmodulesconf-in-ubuntu/) so all is in /etc/modprobe.d/ for ubuntu. 

Ok, I now, not real help, but I believe all the pointers are here to solve it. Without installing aiptek myself again I cannot do more, as the more specific I get the more likely I would be wrong. Best would be if an aiptek user tries to manually set some parameters and writes back on this list

i ran the command with sudo, got the same output apart from the last FATAL error.

i'll have a look through that stuff and see what i come up with. thanks

---

### Post by simtaalo on 2009-01-27
still having no luck with this, anyone able to help?

---

