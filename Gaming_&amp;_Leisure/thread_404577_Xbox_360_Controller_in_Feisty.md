---
title: "Xbox 360 Controller in Feisty"
date: 2007-04-08
forum: Gaming &amp; Leisure
---

### Post by molex on 2007-04-08
I am attempting to run this tutorial I found here:
[http://ubuntuforums.org/showthread.php?t=318382&highlight=xbox+360+edgy](http://ubuntuforums.org/showthread.php?t=318382&highlight=xbox+360+edgy)

Unfortunatly this doesn't work on my PC.

I keep getting the following error when I try and make the module
```
molex@molex-desktop:~/.xpad360$ sudo make
make modules -C /usr/src/linux-headers-2.6.20-14-generic SUBDIRS=/home/molex/.xpad360
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-14-generic'
  CC [M]  /home/molex/.xpad360/xpad.o
/home/molex/.xpad360/xpad.c:54:26: error: linux/config.h: No such file or directory
/home/molex/.xpad360/xpad.c:62:29: error: linux/usb_input.h: No such file or directory
/home/molex/.xpad360/xpad.c: In function ‘xpad_process_packet’:
/home/molex/.xpad360/xpad.c:161: warning: implicit declaration of function ‘input_regs’
/home/molex/.xpad360/xpad.c: In function ‘xpad_probe’:
/home/molex/.xpad360/xpad.c:368: error: ‘SLAB_ATOMIC’ undeclared (first use in this function)
/home/molex/.xpad360/xpad.c:368: error: (Each undeclared identifier is reported only once
/home/molex/.xpad360/xpad.c:368: error: for each function it appears in.)
/home/molex/.xpad360/xpad.c:386: warning: implicit declaration of function ‘usb_to_input_id’
/home/molex/.xpad360/xpad.c:451: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
make[2]: *** [/home/molex/.xpad360/xpad.o] Error 1
make[1]: *** [_module_/home/molex/.xpad360] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-14-generic'
make: *** [all] Error 2

```

Suggestions?

I NEED TO PLAY FRETS ON FIRE WITH MY NEW X-PLORER! :guitar:

---

### Post by beg1689 on 2007-04-09
if you want it to compile you will need to make a few small changes to xpad.c:
Change
    #include <linux/usb_input.h>
to
    /* #include <linux/usb/input.h> */


and change
    input_regs(dev, regs);
to
    /* input_regs(dev, regs); */

finally, change
    SLAB_ATOMIC
to
    GFP_ATOMIC

these are all results of recent kernel changes. Should compile fine after that. Doesn't mean it'll work though :)

---

### Post by proxess on 2007-04-20
> **beg1689 said:**
> if you want it to compile you will need to make a few small changes to xpad.c:
Change
    #include <linux/usb_input.h>
to
    #include <linux/usb/input.h>

and change
    input_regs(dev, regs);
to
    /* input_regs(dev, regs); */

finally, change
    SLAB_ATOMIC
to
    GFP_ATOMIC

these are all results of recent kernel changes. Should compile fine after that. Doesn't mean it'll work though :)


also Change
    #include <linux/config.h>
to
   #include <linux/autoconf.h>

---

### Post by EEVOL on 2007-04-21
I'm having the same problem, I've tried the above suggested advice but yet I still get these errors:

```
joe@joe-laptop:~/.xpad360$ sudo make
make modules -C /usr/src/linux-headers-2.6.20-15-generic SUBDIRS=/home/joe/.xpad360
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/joe/.xpad360/xpad.o
/home/joe/.xpad360/xpad.c:60:23: warning: extra tokens at end of #include directive
/home/joe/.xpad360/xpad.c:62:29: error: linux/usb_input.h: No such file or directory
/home/joe/.xpad360/xpad.c: In function &#8216;xpad_probe&#8217;:
/home/joe/.xpad360/xpad.c:386: warning: implicit declaration of function &#8216;usb_to_input_id&#8217;
/home/joe/.xpad360/xpad.c:451: warning: passing argument 6 of &#8216;usb_fill_int_urb&#8217; from incompatible pointer type
make[2]: *** [/home/joe/.xpad360/xpad.o] Error 1
make[1]: *** [_module_/home/joe/.xpad360] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [all] Error 2

```

Please help!!  I am using the new Feisty Fawn release with kernel linux-headers-2.6.20-15-generic.

---

### Post by bhuthogg on 2007-04-22
i am also having probs with this :( 

make modules -C /usr/src/linux-headers-2.6.20-12-generic SUBDIRS=
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-12-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  HOSTCC  scripts/basic/fixdep
scripts/basic/fixdep.c:105:23: error: sys/types.h: No such file or directory
scripts/basic/fixdep.c:106:22: error: sys/stat.h: No such file or directory
scripts/basic/fixdep.c:107:22: error: sys/mman.h: No such file or directory
scripts/basic/fixdep.c:108:20: error: unistd.h: No such file or directory
scripts/basic/fixdep.c:109:19: error: fcntl.h: No such file or directory
scripts/basic/fixdep.c:110:20: error: string.h: No such file or directory
scripts/basic/fixdep.c:111:20: error: stdlib.h: No such file or directory
scripts/basic/fixdep.c:112:19: error: stdio.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from scripts/basic/fixdep.c:113:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
scripts/basic/fixdep.c:114:19: error: ctype.h: No such file or directory
scripts/basic/fixdep.c:115:23: error: arpa/inet.h: No such file or directory
scripts/basic/fixdep.c: In function ‘usage’:
scripts/basic/fixdep.c:129: warning: implicit declaration of function ‘fprintf’
scripts/basic/fixdep.c:129: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:129: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:129: error: (Each undeclared identifier is reported only once
scripts/basic/fixdep.c:129: error: for each function it appears in.)
scripts/basic/fixdep.c:130: warning: implicit declaration of function ‘exit’
scripts/basic/fixdep.c:130: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c: In function ‘print_cmdline’:
scripts/basic/fixdep.c:138: warning: implicit declaration of function ‘printf’
scripts/basic/fixdep.c:138: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:141: error: ‘NULL’ undeclared here (not in a function)
scripts/basic/fixdep.c: In function ‘grow_config’:
scripts/basic/fixdep.c:154: warning: implicit declaration of function ‘realloc’
scripts/basic/fixdep.c:154: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:156: warning: implicit declaration of function ‘perror’
scripts/basic/fixdep.c:156: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c: In function ‘is_defined_config’:
scripts/basic/fixdep.c:172: warning: implicit declaration of function ‘memcmp’
scripts/basic/fixdep.c: In function ‘define_config’:
scripts/basic/fixdep.c:185: warning: implicit declaration of function ‘memcpy’
scripts/basic/fixdep.c:185: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/basic/fixdep.c: In function ‘use_config’:
scripts/basic/fixdep.c:204: error: ‘PATH_MAX’ undeclared (first use in this function)
scripts/basic/fixdep.c:212: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/basic/fixdep.c:218: warning: implicit declaration of function ‘tolower’
scripts/basic/fixdep.c:220: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/basic/fixdep.c:204: warning: unused variable ‘s’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:223: error: expected declaration specifiers or ‘...’ before ‘size_t’
scripts/basic/fixdep.c: In function ‘parse_config_file’:
scripts/basic/fixdep.c:225: error: ‘len’ undeclared (first use in this function)
scripts/basic/fixdep.c:231: warning: implicit declaration of function ‘ntohl’
scripts/basic/fixdep.c:242: warning: implicit declaration of function ‘isalnum’
scripts/basic/fixdep.c: In function ‘strrcmp’:
scripts/basic/fixdep.c:255: warning: implicit declaration of function ‘strlen’
scripts/basic/fixdep.c:255: warning: incompatible implicit declaration of built-in function ‘strlen’
scripts/basic/fixdep.c: In function ‘do_config_file’:
scripts/basic/fixdep.c:266: error: storage size of ‘st’ isn’t known
scripts/basic/fixdep.c:270: warning: implicit declaration of function ‘open’
scripts/basic/fixdep.c:270: error: ‘O_RDONLY’ undeclared (first use in this function)
scripts/basic/fixdep.c:272: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:272: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:274: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c:276: warning: implicit declaration of function ‘fstat’
scripts/basic/fixdep.c:278: warning: implicit declaration of function ‘close’
scripts/basic/fixdep.c:281: warning: implicit declaration of function ‘mmap’
scripts/basic/fixdep.c:281: error: ‘PROT_READ’ undeclared (first use in this function)
scripts/basic/fixdep.c:281: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
scripts/basic/fixdep.c:281: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:288: error: too many arguments to function ‘parse_config_file’
scripts/basic/fixdep.c:290: warning: implicit declaration of function ‘munmap’
scripts/basic/fixdep.c:266: warning: unused variable ‘st’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:295: error: expected declaration specifiers or ‘...’ before ‘size_t’
scripts/basic/fixdep.c: In function ‘parse_dep_file’:
scripts/basic/fixdep.c:298: error: ‘len’ undeclared (first use in this function)
scripts/basic/fixdep.c:300: error: ‘PATH_MAX’ undeclared (first use in this function)
scripts/basic/fixdep.c:302: warning: implicit declaration of function ‘strchr’
scripts/basic/fixdep.c:302: warning: incompatible implicit declaration of built-in function ‘strchr’
scripts/basic/fixdep.c:304: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:304: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:305: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c:307: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/basic/fixdep.c:308: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/basic/fixdep.c:300: warning: unused variable ‘s’
scripts/basic/fixdep.c: In function ‘print_deps’:
scripts/basic/fixdep.c:337: error: storage size of ‘st’ isn’t known
scripts/basic/fixdep.c:341: error: ‘O_RDONLY’ undeclared (first use in this function)
scripts/basic/fixdep.c:343: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:343: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:345: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c:349: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:353: error: ‘PROT_READ’ undeclared (first use in this function)
scripts/basic/fixdep.c:353: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
scripts/basic/fixdep.c:353: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:360: error: too many arguments to function ‘parse_dep_file’
scripts/basic/fixdep.c:337: warning: unused variable ‘st’
scripts/basic/fixdep.c: In function ‘traps’:
scripts/basic/fixdep.c:372: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:372: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:374: warning: incompatible implicit declaration of built-in function ‘exit’
make[2]: *** [scripts/basic/fixdep] Error 1
make[1]: *** [scripts_basic] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-12-generic'
make: *** [all] Error 2


has anyone made a 7.04 guide?

---

### Post by po0f on 2007-04-22
To people who can't get Xbox 360 controllers working with Feisty,

Attached are a modified xpad.c, xpad.h, and accompanying Makefile to get it working.  I found a modified-for-Feisty set of source files somewhere on these forums (I'd link it if I could find it), but the d-pad didn't work.  I've hacked d-pad support back into it.  Enjoy.

---

### Post by ADRez on 2007-04-23
^ Thanks so much!! It works OK! :guitar:

---

### Post by proxess on 2007-04-24
po0f your a life saver!

---

### Post by Uranium235 on 2007-04-29
Would you mind telling me how to utilize that makefile please?

---

### Post by po0f on 2007-04-29
Uranium235,

Sure thing:

```
$ tar xvzf /path/to/xpad360.tar.gz
$ cd xpad360
$ make
$ sudo make install
```

If you want to back up the original xpad driver (run **before** `sudo make install` above):

```
$ cp /lib/modules/`uname -r`/kernel/drivers/usb/input/xpad.ko xpad.ko.orig
```

---

### Post by Uranium235 on 2007-04-29
Ok thanks do I need to do a reboot before it will work then?

---

### Post by po0f on 2007-04-30
Uranium235,

A reboot couldn't hurt, but the new module should be available for use after running:

```
$ sudo modprobe -r xpad
$ sudo update-modules
$ sudo modprobe xpad
```

I've actually had problems getting the controller working if it is plugged in at boot (a lot of `modprobe -r xpad`ing, replugging the controller, etc).  Keep it unplugged during boot and plug it in when you want to use it and you should be fine.

HTH

---

### Post by Uranium235 on 2007-04-30
I tried a calibration and it comes up with a whole bunch of axises and no buttons??  I'll try a reboot without it plugged in.

---

### Post by Uranium235 on 2007-04-30
Thanks man.  Rebooting without it plugged in fixed the issue.  I have to remember to unplug the thing every time I'm not using it.  Now I wonder if Unreal Tournament for linux maps the analog sticks correctly (windows didn't) :)

---

### Post by po0f on 2007-04-30
Uranium235,

Yeah, I'm a little lazy and forget to unplug it when I reboot.

I haven't tried using a controller beyond emulators (don't really play other "games"), so here's hoping it'll work for you.  :)

---

### Post by konman2k4 on 2007-05-01
I downloaded the modified xpad.c/xpad.h files but they would not work with my Mad Catz XBOX 360 controller (the cheap walmart one).  I modified the xpad.c file to include the id for my controller and to added it to the "Static Struct" section.  It works pretty good now.  Just need to get the back trigger buttons and the right analog control to fully work.

If anybody has any suggestions please let me know.

---

### Post by ignitionnight on 2007-05-03
How do I calibrate this?

edit:
I am using this to get the GH2 Xplorer controller to work.

---

### Post by coldstatue on 2007-05-04
I am also trying to folllow the instructions at 
[http://ubuntuforums.org/showthread.php?t=318382&highlight=xbox+360+edgy](http://ubuntuforums.org/showthread.php?t=318382&highlight=xbox+360+edgy)
with the updated packages from this thread. 

However, my system doesn't recognize the uname -r in reference to my kernel. 
in my lib/modules, I have both the edgy and feisty kernels. 

so I tried to do 

sudo apt-get install linux-headers-'uname -r' build-essential

as instructed in the tutorial linked above, but I get

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-uname -r

can anyone tell me what source I need to add? Or am I way off here?

---

### Post by coldstatue on 2007-05-04
I am not getting any errors with the updated packages, but because I was having problems in the original tutorial with the 'uname -r' reference, I thought maybe it was causing problems. Here's what I did with the updated packages.

```
[email]coldstatue@Mercury:~/.xpad[/email]360$ sudo make
make modules -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/coldstatue/.xpad360
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/coldstatue/.xpad360/xpad.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
[email]coldstatue@Mercury:~/.xpad[/email]360$ sudo make install
mv -f xpad.ko /lib/modules/2.6.20-15-generic/kernel/drivers/usb/input
[email]coldstatue@Mercury:~/.xpad[/email]360$ modprobe -r xpad
[email]coldstatue@Mercury:~/.xpad[/email]360$ sudo update-modules
[email]coldstatue@Mercury:~/.xpad[/email]360$ sudo modprobe xpad
```

 As you can see, there are no errors, but I am not getting any controller response - regardless of rebooting with it unplugged. Do I need to modprobe again after reboot? The light is blinking on the controller. How will I know if it's working? Will it move my cursor, or is there a game that it should just work on? Thanks,.

---

### Post by po0f on 2007-05-04
coldstatue,

Is this a Microsoft controller or a third party one?  It's possible that the driver doesn't recognize it if it's a third party controller.  Please post the output of what's printed to the terminal after running this command (unplug the controller, run command, replug controller):

```
$ sudo tail -fn0 /var/log/messages
```

[EDIT]

Oh, and if you would have bothered reading the whole thread you linked, in post #9, I commented that those are backticks, not single quotes; that's why you're apt-get command wasn't working.  ;)

---

### Post by coldstatue on 2007-05-05
ok, I fixed the back-ticks and tried again. I am not sure how to test it, but here's what I get when I ran the command you gave.
coldstatue@Mercury:~$ sudo tail -fn0 /var/log/messages
Password:
May  5 16:27:31 Mercury kernel: [  150.713656] usb 2-4: new full speed USB device using ohci_hcd and address 4
May  5 16:27:31 Mercury kernel: [  150.930603] usb 2-4: configuration #1 chosen from 1 choice
May  5 16:27:31 Mercury kernel: [  150.968765] input: Microsoft Xbox 360 Controller as /class/input/input7


So, does that mean it's working?

It is a microsoft controller.

Thanks.

---

### Post by coldstatue on 2007-05-05
I did reboot with it unplugged, then plugged it back in. It shows here, but I still have a blinking light, and it doesn't seem to work. How do I test it? 
coldstatue@Mercury:~$ lsusb
Bus 003 Device 003: ID 13b1:0014 Linksys 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 045e:028e Microsoft Corp. 
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04a9:10a0 Canon, Inc. 
Bus 001 Device 005: ID 058f:9360 Alcor Micro Corp. 
Bus 001 Device 004: ID 046d:092f Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
coldstatue@Mercury:~$

---

### Post by po0f on 2007-05-05
coldstatue,

Is a device node created for it (/dev/input/js0 usually for the first controller plugged in)?  If not, post the output of this command (it will print a bunch of stuff, attach the resulting file to a reply please):

```
$ udevinfo -q all -a -p /class/input/input7 | tee udev-output.txt
```

This is assuming you haven't un-/replugged your controller.

---

### Post by coldstatue on 2007-05-05
I have rebooted and replugged, so I don't know if this will do any good, but here are the results. Thanks for your time. I really appreciate it.

```
Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/class/input/input7':
    KERNEL=="input7"
    SUBSYSTEM=="input"
    DRIVER==""
    ATTR{uniq}==""
    ATTR{phys}=="usb-0000:00:13.1-4/input0"
    ATTR{name}=="Microsoft Xbox 360 Controller"

  looking at parent device '/devices/pci0000:00/0000:00:13.1/usb2/2-4/2-4:1.0':
    KERNELS=="2-4:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="xpad"
    ATTRS{modalias}=="usb:v045Ep028Ed0110dcFFdscFFdpFFicFFisc5Dip01"
    ATTRS{bInterfaceProtocol}=="01"
    ATTRS{bInterfaceSubClass}=="5d"
    ATTRS{bInterfaceClass}=="ff"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bInterfaceNumber}=="00"

  looking at parent device '/devices/pci0000:00/0000:00:13.1/usb2/2-4':
    KERNELS=="2-4"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{serial}=="043106C"
    ATTRS{product}=="Controller"
    ATTRS{maxchild}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{devnum}=="4"
    ATTRS{speed}=="12"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="ff"
    ATTRS{bDeviceSubClass}=="ff"
    ATTRS{bDeviceClass}=="ff"
    ATTRS{bcdDevice}=="0110"
    ATTRS{idProduct}=="028e"
    ATTRS{idVendor}=="045e"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 4"
    ATTRS{configuration}==""

  looking at parent device '/devices/pci0000:00/0000:00:13.1/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{serial}=="0000:00:13.1"
    ATTRS{product}=="OHCI Host Controller"
    ATTRS{manufacturer}=="Linux 2.6.20-15-generic ohci_hcd"
    ATTRS{maxchild}=="4"
    ATTRS{version}==" 1.10"
    ATTRS{devnum}=="1"
    ATTRS{speed}=="12"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bcdDevice}=="0206"
    ATTRS{idProduct}=="0000"
    ATTRS{idVendor}=="0000"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{configuration}==""

  looking at parent device '/devices/pci0000:00/0000:00:13.1':
    KERNELS=="0000:00:13.1"
    SUBSYSTEMS=="pci"
    DRIVERS=="ohci_hcd"
    ATTRS{msi_bus}==""
    ATTRS{broken_parity_status}=="0"
    ATTRS{modalias}=="pci:v00001002d00004375sv00001462sd00007248bc0Csc03i10"
    ATTRS{local_cpus}=="ff"
    ATTRS{irq}=="17"
    ATTRS{class}=="0x0c0310"
    ATTRS{subsystem_device}=="0x7248"
    ATTRS{subsystem_vendor}=="0x1462"
    ATTRS{device}=="0x4375"
    ATTRS{vendor}=="0x1002"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

coldstatue@Mercury:~$ 
```

---

### Post by coldstatue on 2007-05-05
The light is off now, and I can't find a game that will respond to it.

---

### Post by po0f on 2007-05-05
coldstatue,

But is there a /dev/input/jsX device node for it?  (X will be a number)

[EDIT]

You could also try different USB ports.  Also, if there is a device node for it, try running this command and pushing buttons on the controller (press Ctrl-C to quit):

```
$ cat /dev/input/jsX
```

---

### Post by coldstatue on 2007-05-05
Oh, sorry. I thought was something you would get back from the last code. I misunderstood
Yes, js0

---

### Post by ebruce on 2007-05-05
Hi, I have the same probem, and i resolved unpluging the pads (2 MS xbox 360 usb) but in Edgy that was not necesary. How we can fix the driver to  always leave them connected?

thanks..

---

### Post by thewizard5001 on 2007-05-11
I have a friend whose XBox 360 controllers are cordless, and he will need a USB Adapter so that he can make use of them. What USB Adapter will work either as a standard USB HID device, or with this module (driver)? Will this one work? : [http://www.target.com/gp/detail.html/ref=br_1_22/602-7869288-2756621?ie=UTF8&frombrowse=1&asin=B000HZFCT2](http://www.target.com/gp/detail.html/ref=br_1_22/602-7869288-2756621?ie=UTF8&frombrowse=1&asin=B000HZFCT2)

---

### Post by po0f on 2007-05-11
thewizard5001,

I'm (almost) sure that if they don't work right off the bat, they can be made to work.

---

### Post by Silent_Hunter on 2007-05-11
I have a Wireless Xbox 360 controller for the Xbox.  I don't have a cord to connect it to pc, so that wireless hub would work perfect for me.   How would you get it to work?  How much trouble is it?  Has anyone else done it and can explain instructions?

---

### Post by coldstatue on 2007-05-11
BTW, poof

cat /dev/input/js0

definitely worked. I had all kinds on info spitting out, so I guess I just need to get it working with a game. Thanks for all of your help;

---

### Post by po0f on 2007-05-13
coldstatue,

Does jscalibrator recognize it?  I'd like to know if it works out for you.  What games are you trying it with?

Me personally, my gaming is limited to emulators mainly; this works perfectly for it.


Silent_Hunter,

I don't own one of the wireless controllers, so I can't provide any more info.  (I'm actually interested in maybe picking up a SIXAXIS controller (for the PS3) to see if I can get that one to work.)

---

### Post by coldstatue on 2007-05-13
@poof

Yes, jscalibrator sees it.  Because I don't know what facilitates interaction between the controller and games, I've just been trying whatever i can find, from Tux Racer to sauerbraten. I haven't found any that work. Can you tell me what emulator(s) and games you are using. I would love to have a couple of time-killers, and to make use of my 360 controller.

---

### Post by po0f on 2007-05-13
coldstatue,

[list]
[*][zsnes](http://www.zsnes.com/) : it's in the repos, but I compiled 1.51 from source
[*][pSX](http://psxemulator.gazaxian.com/) : **excellent** PSX emulator, I used to pimp ePSXe out to all my friends, but this one is my new fave (not in the repos)
[/list]

I know that this controller also works with [rRootage](http://www.asahi-net.or.jp/~cs8k-cyu/windows/rr_e.html) (*crazy* hard game).  This is also in the repos.

HTH

---

### Post by Deathshrimp316 on 2007-05-13
I attempted to edit the xpad.c file for the wireless reciever, changing the device IDs to suit the wireless reciever as per [http://ubuntuforums.org/showthread.php?t=368414](http://ubuntuforums.org/showthread.php?t=368414) but it wont assign the driver to the device it seems

```
patrick@patrick-pc:~/xpad360$ sudo tail -fn0 /var/log/messages
May 13 16:06:20 patrick-pc kernel: [  880.360352] usb 3-1: new full speed USB device using uhci_hcd and address 14
May 13 16:06:20 patrick-pc kernel: [  880.607626] usb 3-1: configuration #1 chosen from 1 choice

```

device shows up in lsusb:

```
patrick@patrick-pc:~/xpad360$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 045e:003c Microsoft Corp. SideWinder Joystick
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:0719 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```

The 045e:0719 is the correct vendor and product ID for the receiver

---

### Post by coldstatue on 2007-05-13
cool stuff, poof. 

I have to go away for a few days, but when I get back, I am playing the $%*7 out of these.

Thanks. That rRootage looks cool.

---

### Post by coldstatue on 2007-05-13
can you give me a hint on how to find some roms? I'm looking for snes, and finding a million ad sites with no files.I guess it's time I got a decent torrent program on my linux box.  BTW, rrooter works with my 360 controller,  That game is awesome. I can't remember the name of it, but I have seen a very similar platform side-scrolling version on you tube. It gets pretty crazy. I did ok on level 1, but jumping to 28 shortened my lifespan.

---

### Post by Twich0514 on 2007-05-16
I have my GH2 360 controller that won't connect. It is connected but there is no "/dev/input/js0". The lights flash when i first plug it in but they die. Frets On Fire won't pick up the joystick.

---

### Post by coldstatue on 2007-05-17
found some roms, poof. Thanks again. It works great!!!

---

### Post by po0f on 2007-05-19
To the people with the GH2 controller,

I'm not familiar with what this is, is it a guitar controller used with Guitar Heroes?  If it is, I have no way of testing if it works or not, since I neither own one nor do I know someone with one of these controllers.  Sorry.


coldstatue,

Glad you got it all figured out.  ;)

---

### Post by goemon_h on 2007-05-22
> **Twich0514 said:**
> I have my GH2 360 controller that won't connect. It is connected but there is no "/dev/input/js0". The lights flash when i first plug it in but they die. Frets On Fire won't pick up the joystick.

Is this still the case?  Has anyone gotten this working?

---

### Post by monachetti on 2007-05-23
i'm also having the aforementioned problem with the x-plorer controller


I found some files that worked for me. Hope it helps....

[http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c](http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c)
[http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h](http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h)

---

### Post by senorsalsa on 2007-05-30
Thanks poof, your files worked great.

---

### Post by po0f on 2007-05-31
monachetti,

Are you using Feisty / kernel version >2.6.19?  If you are, I don't see how those files worked for you.  Last time I checked, those source files only worked with kernel version <=2.6.18.


senorsalsa,

Glad I could help.  :)


GH2 X-Plorer controller users,

I might eventually pick up one of these controllers to see if I can get it working myself.  Are there any third party controllers like this available yet?

---

### Post by monachetti on 2007-05-31
qwax@libra:~$ ls /usr/src
linux-headers-2.6.20-15          linux-headers-2.6.20-16
linux-headers-2.6.20-15-generic  linux-headers-2.6.20-16-generic


If you're curious, I found the files at this link
[http://www.phoronix.net/forums/showthread.php?t=1003](http://www.phoronix.net/forums/showthread.php?t=1003)

---

### Post by srt4play on 2007-06-01
po0f, if you do pick up a sixaxis PS3 controller and get it working please post a howto. I would love to be able to use it on my PC.

---

### Post by 2dere on 2007-06-07
Okay my first post was me saying that I couldn't get my controller to work, but it was just me not following the instructions right. Thanks all for the info and links I'm off to play Star Ocean with me controller now yay ^-^

---

### Post by jack_teagarden on 2007-06-10
Heyo,

Same deal, Fiesty and same kernel, *but* those files didn't work, and It still doesn't mount the controller. the GH2 controllers aren't microsoft, so do I need to do something else?

---

### Post by po0f on 2007-06-11
jack_teagarden,

Please post the output of:

```
$ lsusb
```

---

### Post by KneeTie on 2007-06-13
i downloaded the xpad360.tar.gz but i dont know what to do with it im new to ubuntu but im not a complete computer noob im getting used to ubuntu , the problem is i dont know where to enter this >


Code:

$ tar xvzf /path/to/xpad360.tar.gz
$ cd xpad360
$ make
$ sudo make install


is it in the terminal or the make install file because i got this after entering into the terminal

nitai@nitai-laptop:~$ /home/nitai/Desktop/xpad360
bash: /home/nitai/Desktop/xpad360: is a directory
nitai@nitai-laptop:~$ make
make: *** No targets specified and no makefile found.  Stop.
nitai@nitai-laptop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
nitai@nitai-laptop:~$ 

any help greatly appreciated.

---

### Post by po0f on 2007-06-19
KneeTie,

You forgot a command in one of your steps.  ;)

```
nitai@nitai-laptop:~$ /home/nitai/Desktop/xpad360
```

should be:

```
nitai@nitai-laptop:~$ **cd** /home/nitai/Desktop/xpad360
```

---

### Post by dwink1217 on 2007-06-20
can anbody help me get this running on Ubuntu Studio? It's 

heres what happens...

[email]nick@Hessfamily:~/.xpad[/email]360$ sudo make
make modules -C /lib/modules/2.6.20-16-lowlatency/build SUBDIRS=/home/nick/.xpad360
make: *** /lib/modules/2.6.20-16-lowlatency/build: No such file or directory.  Stop.
make: *** [all] Error 2

---

### Post by po0f on 2007-06-20
dwink1217,

You will need to install the kernel headers appropriate for your kernel.  Try something like this:

```
$ sudo apt-get install linux-headers-2.6.20-16-lowlatency
```

Hopefully, Ubuntu Studio devs have made the headers available to you.  ;)

Oh, and when building the module, there is no need to prefix the `make` command with sudo.  Only when installing the module is this necessary.

---

### Post by adt41287 on 2007-06-21
i cant seem to get my guitar working.... everything compiled and everything but all it does is flash around the 360 guide button on the controller

---

### Post by KneeTie on 2007-06-21
thx a bunch po0f i got it working in Zsnes with no problems , someone had posted a way to see if it  was working in the terminal were you would press buttons and weird  characters would show up and it is working but i cant get it to work in xmame, gxmame , or kxmame i dont know what the deal is it should detect it any help appreciated. Thx again there po0f  for the help

---

### Post by po0f on 2007-06-21
KneeTie,

Sometimes in the configuration dialog of applications, you can find a setting that points to the joystick device you want to use.  This might be set incorrectly in your case.  Check to see if the device is set to `/dev/js0`; if it is, change it to `/dev/input/js0`.


adt41287,

Sorry, I still have no guitar to test.  :(

---

### Post by KneeTie on 2007-06-21
WOW you are a true Helper to the forum , i did the > /dev/input/js0 and it fixed it right away po0f !!!!  Thx alot man , not being able to use my 360 controller in mame was the only reason why i hadn't gotten rid of windows completely , now its time for me to say good bye to windows for good .   P.S  im showing ubuntu off to all my pals and stuff in the university and everyone likes it  even real noobs and everyone's downloading it and stuff my family computers just got switched to ubuntu as well Woot.  THX ALOT

---

### Post by Hunkadoodledoo on 2007-06-25
I am trying to get my Red Octane X-plorer guitar (model #95065) working in Feisty, and I compiled the update to xpad, but my controller still doesn't register as a joystick.  I am using the Red Octane guitar that is sold separate from the game, and when I run lsusb, its ID is this:

Bus 002 Device 003: ID 1430:4748

What might I need to do to get it recognized?  Thanks!

---

### Post by po0f on 2007-06-26
Hunkadoodledoo,

If you would be so kind, maybe try the attached sources instead.  I have no way of testing if they work or not, so don't be surprised if they don't.  ;)

---

### Post by Hunkadoodledoo on 2007-06-26
poof,

Nothing happened that hasn't already happened.  I plug it in and the guide button flashes three times and then stays off.  lsusb still shows the same ID, and it isn't recognized in FoF.  Thanks for the quick reply, though.  How hard would it be for me to ship you my guitar and you write a driver for it?

---

### Post by po0f on 2007-06-26
Hunkadoodledoo,

I wouldn't go that far.  :)

I might at some point pick up one of these controllers.  Right now, I'm more interested in the PS3's controller though (SIXAXIS).

(Oh, and by the way, I don't write drivers, I just hack them a little here and there.  Maybe someday... )  ;)

---

### Post by yimmmy on 2007-06-28
Ok im way confused how do i get my paddel to work ???

---

### Post by Flac on 2007-06-29
alright hoping someone might be able to help me. using poof's makefile and what not, following the instructions listed on first page. Controler flashes once when i plug it in then goes blank.

jscalibrator recognizes that i have an xbox 360 controler plugged in(at least in name) but nothing i do on it puts out any output anywhere. tried cat /dev/input/js0 and it doesnt do anything when i input button's or anything

lsusb returns
> Bus 002 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 045e:028e Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000  

Any help would be appriciated :)

---

### Post by Flac on 2007-06-30
Update: nevermind, Solved problem sorry

---

### Post by Hunkadoodledoo on 2007-07-08
Any ideas po0f?  Anyone else?  I really know almost zero about C or device drivers in Linux, but I read through the updated xpad.c, and saw the ```
0x1430, 0x4748, "RedOctane X-plorer"
``` that wasn't in the earlier version, but Ubuntu still doesn't recognize it.  Hmmmm...

---

### Post by po0f on 2007-07-08
Hunkadoodledoo,

The (new) guitar controller may behave differently from a standard Xbox 360 controller in ways; I don't know.  If you can wait until Halo 3 comes out (when I plan on picking up a 360 for myself and since I've no real reason right now to get Guitar Heroes), I might be able to figure it out then.  I just can't justify spending $90 on a game I can't play, sorry.

Yeah, I through the manufacturer ID into the xpad.c source file thinking that might help, but alas, as you already know, no dice.  :)

---

### Post by Typwn on 2007-07-09
I have a PS2 to PC adapter and my PS2 Guitar Hero (Original Black) controller hooked up. Joystick Calibrator  reads it perfectly, but in Frets on Fire the paddle wont set as a key. Any help would be welcome. Thanks.

---

### Post by po0f on 2007-07-10
Typwn,

You'd be better off starting a new thread, or even posting in [this](http://ubuntuforums.org/showthread.php?t=497458) one (which is about trying to get a PS2 guitar working on your PC).  This thread is for Xbox 360 controllers.

---

### Post by Energia on 2007-07-14
> **po0f said:**
> To people who can't get Xbox 360 controllers working with Feisty,

Attached are a modified xpad.c, xpad.h, and accompanying Makefile to get it working.  I found a modified-for-Feisty set of source files somewhere on these forums (I'd link it if I could find it), but the d-pad didn't work.  I've hacked d-pad support back into it.  Enjoy.


i used this file and all was applied, but when i start jscalibration, it recognize my only Microsoft Wireless Receiver!!! :confused:

I ve two Microsoft Xbox 360 controllers but they are not wireless they are with USB port

so, Can I use this solution for USB xbox 360 controller?!?

what solutions for USB gamepads?!? 

thank's in advance and excuse me for my bad english...

---

### Post by goonies on 2007-07-16
My question is, what 360 controller does these instructions apply to? Wired or Wireless?

I have a wireless controller and the way I plug it to my computer is with the wire the charge and play kit came with.  Now is this what you guys are also connecting your controllers to your computers with or is it some other device/wire?

---

### Post by po0f on 2007-07-16
Energia,

Are these third-party (ie, non-Microsoft) controllers you are using?  I only have a Microsoft one, and it works perfectly.  And yes, it's connected via USB cable, wired, not the wireless jobs.  If it's not a Microsoft controller, please post the output of `lsusb` with the controller connected.


goonies,

Wired.  I'm not sure if this driver will work for the wireless ones.  As I said further up in my post, maybe posting the output of `lsusb` will help me get it working for you.  :)


[EDIT]

The `lsusb` command is to be run from a terminal, sorry for not being clear about that.

---

### Post by goonies on 2007-07-16
Can these instructions be used for the microsoft wireless receiver?

---

### Post by GrandTheftHobo on 2007-07-17
Alright ladies and gentlemen,

I don't know about anyone else but after reading through all of theses instructions and using fragments from both guides, I'm having a bit of trouble. 

Maybe somebody could be so kind as to put all of this useful info into a definitive guide for using the Xbox 360 controller (namely the wired X-plorer guitar) in Feisty?

---

### Post by po0f on 2007-07-17
GrandTheftHobo,

Well, seeing as how the driver doesn't even support those controllers (yet), there is no point to a guide.  ;)

(Not trying to sound smart or anything, it's just how it is.)

---

### Post by Alexandum on 2007-07-19
I was having trouble getting my Pelican TSZ360 PAD working with kubuntu feisty, but finally made it work.  Just adding the controller to the xpad_device structure wasn't working, but making the following change got it working this time. 

static struct usb_device_id xpad_table [] = {
	{ USB_INTERFACE_INFO('X', 'B', 0) },	/* X-Box USB-IF not approved class */
/*	{ USB_INTERFACE_INFO(0xFF,0x5D ,1) }, */ /* Xbox 360 */
	{ USB_DEVICE(0xE6F,0x201) }, /*TSZ360 pad's id, was MS 360 controller's vend & product  code*/
	{ }
};

I'd tried this earlier without it working and I'm not sure why it worked this time. Only difference is maybe using caps in vendor and product code. The axis on the left stick and the triggers are mixed up in jscalibrator, I don't know if thats unusual. When I tried this before it created 4 joysticks in /dev/input none of which worked.

---

### Post by Energia on 2007-07-21
> **po0f said:**
> Energia,

Are these third-party (ie, non-Microsoft) controllers you are using?  I only have a Microsoft one, and it works perfectly.  And yes, it's connected via USB cable, wired, not the wireless jobs.  If it's not a Microsoft controller, please post the output of `lsusb` with the controller connected.


goonies,

Wired.  I'm not sure if this driver will work for the wireless ones.  As I said further up in my post, maybe posting the output of `lsusb` will help me get it working for you.  :)


[EDIT]

The `lsusb` command is to be run from a terminal, sorry for not being clear about that.

I have original MICROSOFT WIRED XBOX contrell 360 (usb), for windows, and when I run jscalibration, after the install guide on this tread, if I move buttons and axis, nothing move on jscalibration pannel...

So how can I see if gamepad works!?!

thank's in advances... (Im new in linux world, so excuse me for my stupids questions...and for my bad english...)

PS: I use UBUNTU FEISTY 7.04 AMD64 (64 bit)

---

### Post by po0f on 2007-07-21
Energia,

Is a device node created at /dev/input/js0?  If so, try running this command from a terminal:

```
$ cat /dev/input/js0
```

If the device node isn't created, unplug your controller and run these series of commands:

```
$ sudo modprobe -r xpad joydev
$ sudo tail -fn0 /var/log/messages
```

and try replugging the controller in.  If it still doesn't work after this, try reinstalling the module.

---

### Post by Energia on 2007-07-21
> **po0f said:**
> Energia,

Is a device node created at /dev/input/js0?  If so, try running this command from a terminal:

```
$ cat /dev/input/js0
```

If the device node isn't created, unplug your controller and run these series of commands:

```
$ sudo modprobe -r xpad joydev
$ sudo tail -fn0 /var/log/messages
```

and try replugging the controller in.  If it still doesn't work after this, try reinstalling the module.

the gamepad seem to work (i played with Mario cronicles, and super tux), but in this two games, when in option s I configure buttons, triggers dont works as two separates buttons... when (for example) I configure in Mario, shoot with right TRIGGER (nothing appens), if I use another button, the configuration work...

however, if I open Joystick calibration (the controll pannel), I cant see move direction and buttons if i move the gamepad...

Is it all ok in this way?!? :confused:

PS: in super tux, it s very difficult for me chose from menù, with gamepad, because seem very sensible and the menù choise run up and down continually... (dead zone?!? )

could you release a correct procedure to install since first step the 360 controller in FEISTY AMD64

If I must  remove all since now, please tell me how make this.. thank's in advance...

---

### Post by Energia on 2007-07-22
UP!

Please someone help me... :(

---

### Post by Bohlio on 2007-07-22
I'm a tad bit confused here... Are we talking about the Official Xbox 360 Wireless controller that works with both Xbox and the PC?? If so, has anyone gotten this working in Ubuntu? I am expecting it in the mail within a few weeks.

---

### Post by po0f on 2007-07-23
Energia,

If you want to try reinstalling the driver, just `cd` into the directory you extracted and built the module and run `sudo make install` again.  It will overwrite the old module.

As for why jscalibrator isn't recognizing any input from it, are you sure you have the correct device selected in the drop-down menu, or that a device is recognized at all?

I don't see how these instructions would be different for a 64-bit platform (I only use 32-bit (buy me a new box and I'll work on it  ;))), but I wouldn't think that it would pose a problem.


Bohlio,

AFAIK, no one has been able to get this to work with the Microsoft wireless controller, and I don't own one.  When you do get your's, plug it in and post the output of running `lsusb` from a terminal and I'll see if I can't help you get it working.

---

### Post by Hunkadoodledoo on 2007-07-23
Bohlio,

I suppose it depends on what you mean by "official".  I have the Official Red Octane XBOX 360 Xplorer guitar that ships *without* the Guitar Hero game.  I have checked it, and it works fine in Windows.  It would seem that everyone else is using the Official Red Octane XBOX 360 Xplorer guitar that came *with* the video game, and they seem to be having much more success.  So...if the version you bought comes with the game in the package, you may be in luck.  Otherwise, you may be waiting for the kernel driver hackers to get their hands on the version of the guitar I have.  Good luck!

---

### Post by po0f on 2007-07-23
Hunkadoodledoo,

Where did you get just the controller and no game?  Everywhere I've seen it for sale, it was bundled with the game.

---

### Post by Bohlio on 2007-07-23
> **Hunkadoodledoo said:**
> Bohlio,

I suppose it depends on what you mean by "official".  I have the Official Red Octane XBOX 360 Xplorer guitar that ships *without* the Guitar Hero game.  I have checked it, and it works fine in Windows.  It would seem that everyone else is using the Official Red Octane XBOX 360 Xplorer guitar that came *with* the video game, and they seem to be having much more success.  So...if the version you bought comes with the game in the package, you may be in luck.  Otherwise, you may be waiting for the kernel driver hackers to get their hands on the version of the guitar I have.  Good luck!

Ohhh... Im sorry, I thought we were talking about a type of Xbox controller, not the Xbox *guitar* controllers. Sorry then... carry on :)

---

### Post by Hunkadoodledoo on 2007-07-23
You can buy different versions of bundles from the publisher's (Red Octane) webstore.  I have seen the one wired guitar and game bundle, the two wired guitar and game bundle and the single guitar only.  Here is the purchase page for only the guitar:

[http://www.redoctane.com/guitarhero2x-explorer.html](http://www.redoctane.com/guitarhero2x-explorer.html)

---

### Post by Gasten on 2007-07-26
Hey, how does the module work with gutsy's kernel? I'm both thinking about investing AND upgrading, so I want to be sure... :)

---

### Post by po0f on 2007-07-26
Gasten,

I personally haven't tried it.  I'll upgrade to Gutsy tomorrow to try it out (been meaning to anyway).  I'll let you know then.

---

### Post by NormInNorman on 2007-07-29
hey, if anybody finds out how to get the x-plorer to work in feisty, will you please post it in here?  I found a used one a gamestop for $40 and bought it for my son so he can play FoF without the keyboard.  I've spent a couple of days trying to get it to work now and it just ain't happening.  At first it would do nothing - it wouldn't show up in the devices or anything and the light wouldn't stay on.  At some point after downloading and installing various drivers I had a small victory - the light was blinking and it was showing up in jscalibrator.  It didn't work in the slightest, but at least the machine knew it was there.  Now I'm back to nothing again.  I'm pretty frustrated.  I've just switched from Windows to Ubuntu last week and I'm not sure if I'm stay with it or not.

Well, now I'm going to connect it to the old windows box and see if I can get it working.  I'm sure someone will figure it out for feisty eventually.  If there is anything I can do to help, let me know.

---

### Post by NormInNorman on 2007-07-29
> **NormInNorman said:**
> hey, if anybody finds out how to get the x-plorer to work in feisty, will you please post it in here?  I found a used one a gamestop for $40 and bought it for my son so he can play FoF without the keyboard.  I've spent a couple of days trying to get it to work now and it just ain't happening.  At first it would do nothing - it wouldn't show up in the devices or anything and the light wouldn't stay on.  At some point after downloading and installing various drivers I had a small victory - the light was blinking and it was showing up in jscalibrator.  It didn't work in the slightest, but at least the machine knew it was there.  Now I'm back to nothing again.  I'm pretty frustrated.  I've just switched from Windows to Ubuntu last week and I'm not sure if I'm stay with it or not.

Well, now I'm going to connect it to the old windows box and see if I can get it working.  I'm sure someone will figure it out for feisty eventually.  If there is anything I can do to help, let me know.
HA!  The controller works great in XP but FoF crashes.  Wonderful.

---

### Post by johnnyoc3 on 2007-08-05
i am having simmilar problems.

lsusb says:
john@familyguy:~/Desktop/xpad360$ lsusb
Bus 005 Device 004: ID 1307:0163  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 006: ID 1430:4748  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  

and

john@familyguy:~/Desktop/xpad360$ sudo tail -fn0 /var/log/messages
Aug  4 21:37:13 familyguy kernel: [ 1321.944000] usb 3-1: USB disconnect, address 6
Aug  4 21:37:16 familyguy kernel: [ 1325.272000] usb 3-1: new full speed USB device using uhci_hcd and address 7
Aug  4 21:37:17 familyguy kernel: [ 1325.484000] usb 3-1: configuration #1 chosen from 1 choice


it apears the driver will not initialize

dev/input/jsX

doesnt exist.


when the controler is pluged in the light flashes 3 times then disapears.
is there know hope?

---

### Post by paullyjunge on 2007-08-05
Has anyone gotten the Red Octane  X-plorer to work?

---

### Post by NormInNorman on 2007-08-19
<sniff> Anyone? X-plorer?  Please?  FoF just doesn't work as well in Vista.

---

### Post by Azzco on 2007-08-21
I've got a GHII X-plorerguitar controller by redoctane, I read this thread before I bought it today and thought I'd help out getting it to work.

I've installed the the contents of the xpad360.tar.gz archive in the first thread in this topic successfully (no problems there).

I did the tail command as you mentioned before by po0f, and got this output:
```
azzco@Azzco-Desktop:~/.xpad360/xpad360$ sudo tail -fn0 /var/log/messages
Aug 21 20:41:00 Azzco-Desktop kernel: [  462.563577] usb 4-1: new full speed USB device using uhci_hcd and address 3
Aug 21 20:41:00 Azzco-Desktop kernel: [  462.789246] usb 4-1: configuration #1 chosen from 1 choice
```

and the output from lsusb looks like this:
```
azzco@Azzco-Desktop:~$ lsusb
Bus 006 Device 001: ID 0000:0000
Bus 007 Device 006: ID 0f30:0112 Jess Technology Co., Ltd
Bus 007 Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 007 Device 004: ID 03f0:1411 Hewlett-Packard
Bus 007 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 007 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 003: ID 1430:4748
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
```

I hope that this helps in anyway (I guess it doesn't though :roll:).

Oh and BTW this is a wired white guitar with a black neck

---

### Post by Azzco on 2007-08-21
It seems that [this guy](http://blogs.msdn.com/lokeuei/archive/2007/04/07/redoctane-x-plorer-and-frets-on-fire.aspx) got it to work...

Looking at his fix it doesn't really differ from po0fs that much.

---

### Post by NormInNorman on 2007-08-22
Are we talking Feisty?  i think it works in Edgy but not Feisty - or at least I can't get it to work.  Can someone please verify they have it working in Feisty.

---

### Post by Azzco on 2007-08-23
Arrgh this controller works perfectly on windows but XP is to laggy for me... Can't even start up a web browser on windows w/o using cursewords... I hope it'll work in gutsy if it won't in feisty, I've tried recompiling the two files several times with different xpad.c (only once with the redoctane guitar included) but no progress...

---

### Post by po0f on 2007-08-24
Azzco (and others),

I'm going to go out on a limb and say that the guy in the blog post linked is using Edgy, as that is what the guide has instructions for in the guide he linked to.  If you *absolutely have* to use your guitar controller under Ubuntu, use Edgy.  :)

You are correct in thinking that the xpad.c that the guy uses is not much different from the one I posted (I especially like the part where he really doesn't explain exactly what to do/where to place that line of code).  The difference lies in the way the kernel interacts with USB devices.  Sorry I am not a kernel dev (I am just a humble user  :D), or I would be happy to actually get this working for everyone.

---

### Post by Azzco on 2007-08-26
Well great thanks for your help anyways ;)
I hope that I can have my controller work in a future ubuntu distro I'm happy playing with my keyboard so far and those 50&#8364; or what it would be in $ seems a bit thrown away though. If there'll be a fix someday I'll most likely dance of joy but right now it's okay without. ;)

I just hope that other can live without it for the time being and that we'll see a working module in the near future. :)

---

### Post by SeanS on 2007-09-03
Hi poOf, 

Firstly mate.. hats off to you for all the work you've done in this thread :)

I've got a wireless Xbox 360 controller and I'm wondering if there is a fix for it yet?

It seems really close to working..

<Unplug controller>
sean@sean:~$ sudo modprobe -r xpad joydev
sean@sean:~$ sudo tail -fn0 /var/log/messages
<plug controller in>
Sep  4 06:21:31 sean kernel: [  893.316431] usb 2-1.4: new full speed USB device using ohci_hcd and address 5
Sep  4 06:21:31 sean kernel: [  893.427414] usb 2-1.4: configuration #1 chosen from 1 choice
 

So very close!

lsusb shows me,
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 045e:028f Microsoft Corp. 
Bus 002 Device 003: ID 046d:c012 Logitech, Inc. Optical Mouse
Bus 002 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

Which all seems good too, it's recognising it.. 

Any thoughts? Thanks again for your help with this.

Sean

---

### Post by KSI on 2007-09-03
At risk of looking like an idiot, I'm bumping this. I've installed the xp360 files, ran modprobe, restarted, unplugged and replugged and I've yet to get the controller to work. Using a Joytech Advanced controller. Yes, I editted xpad.c to reflect this.

sudo tail -fn0 /var/log/messages
```
josh-laptop kernel: [  181.671217] usb 1-1: USB disconnect, address 3
Sep  3 13:57:55 josh-laptop kernel: [  184.580216] usb 1-1: new full speed USB device using ohci_hcd and address 4
Sep  3 13:57:55 josh-laptop kernel: [  184.688772] usb 1-1: configuration #1 chosen from 1 choice
```
After this, it lists my eth0 devices.

lsusb
```
Bus 003 Device 005: ID 059b:0272 Iomega Corp. 
Bus 003 Device 004: ID 1058:0903 Western Digital Technologies, Inc. 
Bus 003 Device 003: ID 05e3:0608 Genesys Logic, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 1241:1166 Belkin 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 162e:beef  
Bus 001 Device 001: ID 0000:0000  
```
Top three are extranals. Belkin is a mouse. No idea what 001/004 is.

udevinfo -q all -a -p /class/input/input7 | tee udev-output.txt
```
  looking at device '/class/input/input7':
    KERNEL=="input7"
    SUBSYSTEM=="input"
    DRIVER==""
    ATTR{modalias}=="input:b0019v0000p0005e0000-e0,5,kramlsfw0,"
    ATTR{uniq}==""
    ATTR{phys}=="PNP0C0D/button/input0"
    ATTR{name}=="Lid Switch"
```
That's the only one it gives me.

Does not recognize dev/input/js*

Just wondering if I missed anything or if I should toss this controller out and go get a proprietary one.

---

### Post by po0f on 2007-09-04
SeanS / KSI,

Try the following, please:

```
$ sudo modprobe -r xpad
$ sudo update-modules && sudo depmod
```

Reboot if you feel like it (not needed, I just checked), and run the `sudo tail...` command and try plugging your controller in.  Hopefully it recognizes it.

I just did a fresh install 2 weeks ago and I'm just now getting around to installing the xpad360 module.  At first it wasn't working.  Couldn't for the life of me figure out why.  Turns out I forgot to run `depmod`.  I don't know if I mentioned having to run this command earlier; if not, OOPS!  :)

---

### Post by KSI on 2007-09-04
With a fresh copy of the files:

```
josh@josh-laptop:~$ cd xpad360
josh@josh-laptop:~/xpad360$ make
make modules -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/josh/xpad360
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/josh/xpad360/xpad.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/josh/xpad360/xpad.mod.o
  LD [M]  /home/josh/xpad360/xpad.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
josh@josh-laptop:~/xpad360$ sudo make install
mv -f xpad.ko /lib/modules/2.6.20-16-generic/kernel/drivers/usb/input
josh@josh-laptop:~/xpad360$ sudo modprobe -r xpad
josh@josh-laptop:~/xpad360$ sudo update-modules
josh@josh-laptop:~/xpad360$ sudo depmod
josh@josh-laptop:~/xpad360$ sudo tail -fn0 /var/log/messages
Sep  4 19:39:21 josh-laptop kernel: [  632.142511] usb 1-1: USB disconnect, address 4
Sep  4 19:39:22 josh-laptop kernel: [  632.902244] usb 1-1: new full speed USB device using ohci_hcd and address 5
Sep  4 19:39:22 josh-laptop kernel: [  633.010827] usb 1-1: configuration #1 chosen from 1 choice

```

Then it's back to the eth0 traffic.

---

### Post by po0f on 2007-09-05
KSI,

Weird.  Would you mind uploading the source files you're using?

---

### Post by KSI on 2007-09-05
Just using the ones you attached on page one.

---

### Post by paxmaniac on 2007-09-10
In case anyone is trying to get this working in Gutsy, you need to know that the joystick modules now go in:
```

/lib/modules/$(shell uname -r)/kernel/drivers/input/joystick

```
(instead of drivers/usb/input), so you need to change the makefile accordingly.

---

### Post by loctorn on 2007-09-11
KSI,

I'm having the same problem as you.....I even went as far as to completely trash my system and go through the entire process again still with no luck.  jscalibration show's it's there and that other function (forgot what it was) gives me some garble trash message once it's ran so I dunno what else to do till someone else figures it out.  

I just started using Ubuntu Feisty Fawn about 1 week ago and don't plan on having to continuously install/reinstall to see if I can get this to work.

So if anyone is lucky enough to do so please post here as to EXACTLY what files and exact word for word install you done that way if that doesn't work I won't feel so bad when I bash my 360 controller on the asphault.

Thanks

---

### Post by Surkow on 2007-09-11
> **paxmaniac said:**
> In case anyone is trying to get this working in Gutsy, you need to know that the joystick modules now go in:
```

/lib/modules/$(shell uname -r)/kernel/drivers/input/joystick

```
(instead of drivers/usb/input), so you need to change the makefile accordingly.

I just wanted to post the same. After this I'm finally getting some feedback from jscalibrator.

Edit: not all programs recognize the LT and the RT buttons as pressure buttons. I can't seem to get mupen64 to recognize the buttons (not even like a normal button). Sadly enough PCSX2 doesn't get any feedback from the controller at all.

---

### Post by paxmaniac on 2007-09-11
> **Surkow said:**
> 
Edit: not all programs recognize the LT and the RT buttons as pressure buttons. I can't seem to get mupen64 to recognize the buttons (not even like a normal button). Sadly enough PCSX2 doesn't get any feedback from the controller at all.

Did they work under Feisty?

The LT and RT 'triggers' are registered, not as buttons, but as axes (indices 4 and 5).  Any program should be able to access these if they look at the right index.  Is PCSX2 looking at the right device file (e.g /dev/input/js0)?  Some programs will look for /dev/js0 by default so you may have to use a symbolic link e.g:

sudo ln -s /dev/input/js0 /dev/js0

---

### Post by Surkow on 2007-09-12
> **paxmaniac said:**
> Did they work under Feisty?

The LT and RT 'triggers' are registered, not as buttons, but as axes (indices 4 and 5).  Any program should be able to access these if they look at the right index.  Is PCSX2 looking at the right device file (e.g /dev/input/js0)?  Some programs will look for /dev/js0 by default so you may have to use a symbolic link e.g:

sudo ln -s /dev/input/js0 /dev/js0

I already found out they were registered as axes (see this [thread]("http://www.emutalk.net/showthread.php?t=41632")). I will try to create a symbolic link. Hopefully it can be solved as easily as that.

Edit: the symbolic link didn't work.

---

### Post by The Catalyst on 2007-09-12
I've read every post in this topic and the additional topic linked in the first post.

I've followed the instructions given to anyone with my symptoms, and it's left me at this point (still):

I have all the drivers and headers and all that good stuff, and I ran those modprobe commands, and I've done "sudo tail..." which *DOES* recognize my controller, and "cat..." which *DOES NOT* recognize my controller.  My Device Manager *DOES* recognize the controller, while "jscalibrator" also *DOES NOT* recognize my controller.

This seems really strange to me.  Needless to say I can't use my controller for my emulators.

For the record I'm on Fiesty.

Any help would be appriciated.

---

### Post by acoustibop on 2007-09-12
jscalibrator may be the problem, The Catalyst.  It's been known to disable directional controls for controllers: try uninstalling it and rebooting (to make sure anything it was masking is re-detected).

In Ubuntu, controllers are in /dev/input (eg /dev/input/js0 for your first controller), but many applications will look for it in /dev.  Solutions for this are to put a symlink in /dev to your controller in /dev/input, or to redirect each application to /dev/input.

---

### Post by po0f on 2007-09-14
The Catalyst,

I'm a little confused about your situation.  You said the kernel recognizes the controller (via `sudo ..`), but no device is created for it (usually /dev/input/js0).  This doesn't make any sense.

Please post the output of:

```
$ sudo tail -fn0 /var/log/messages
```

when you plug in your controller.  Just to make sure.  ;)

---

### Post by proxess on 2007-09-23
moving onwards in time... seems that the drivers don't work on gutsy (damned kernel updates) so I was wondering if anyone's made a move and worked on the situation?

---

### Post by eslin on 2007-09-24
Hello, I just bought a "Microsoft Wireless Gaming reciever for windows", this thread is kind of a mess with lots of different controllers and demands.

my question is if this xpad.tar.gz file attached to some of the answers supports the adapter that i bought together with my WIRELESS xbox 360 controllers.

I also found this guide [http://ubuntuforums.org/showthread.php?t=368414](http://ubuntuforums.org/showthread.php?t=368414)

I dont know if this info has been merged into the driver attathced to this thread.

here is the output of my lsusb:

```
Bus 001 Device 007: ID 045e:0719 Microsoft Corp. 

```

Best regards 
eslin

---

### Post by eslin on 2007-09-24
> **eslin said:**
> Hello, I just bought a "Microsoft Wireless Gaming reciever for windows", this thread is kind of a mess with lots of different controllers and demands.

my question is if this xpad.tar.gz file attached to some of the answers supports the adapter that i bought together with my WIRELESS xbox 360 controllers.

I also found this guide [http://ubuntuforums.org/showthread.php?t=368414](http://ubuntuforums.org/showthread.php?t=368414)

I dont know if this info has been merged into the driver attathced to this thread.

here is the output of my lsusb:

```
Bus 001 Device 007: ID 045e:0719 Microsoft Corp. 

```

Best regards 
eslin

I solved it.
Used information from [http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux](http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux)

I fetched these files
```

# wget "http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c"
# wget "http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h"

```

then I used the Makefile from ....... tar.gz-file
slightly modified for gutsy:
```

root@mcgusto:~/FILES/xpad/gentoo# cat Makefile 
obj-m := xpad.o
KDIR := /lib/modules/$(shell uname -r)/build
EXTRA_CFLAGS=-I$(shell pwd)
all:
        $(MAKE) modules -C $(KDIR) SUBDIRS=$(shell pwd)
install:
        mv -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick

```

make && make install
update-modules && sudo depmod
modprobe -r xpad
modprobe joydev usbhid xpad

now I was able to run jscalibrator on my "wireless xbox 360 controller".

As the gentoo-page states there are quirks with the wireless support:
[http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux#Wireless_360_controller](http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux#Wireless_360_controller)

Best regards
eslin

---

### Post by proxess on 2007-09-26
Nice guide, worked ALMOST perfectly... but when I boot up with the controller connected, it crashes saying "bad call to modprobe" or something like that, so the pc stops booting.

---

### Post by Silent_Hunter on 2007-10-03
> **eslin said:**
> I solved it.
Used information from [http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux](http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux)

I fetched these files
```

# wget "http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c"
# wget "http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h"

```

then I used the Makefile from ....... tar.gz-file
slightly modified for gutsy:
```

root@mcgusto:~/FILES/xpad/gentoo# cat Makefile 
obj-m := xpad.o
KDIR := /lib/modules/$(shell uname -r)/build
EXTRA_CFLAGS=-I$(shell pwd)
all:
        $(MAKE) modules -C $(KDIR) SUBDIRS=$(shell pwd)
install:
        mv -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick

```

make && make install
update-modules && sudo depmod
modprobe -r xpad
modprobe joydev usbhid xpad

now I was able to run jscalibrator on my "wireless xbox 360 controller".

As the gentoo-page states there are quirks with the wireless support:
[http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux#Wireless_360_controller](http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux#Wireless_360_controller)

Best regards
eslin

I followed the guide. I do not have a /dev/input/js0 or any other js* devices, so jscalibrator cannot calibrate anything. I checked dmesg. Here is the output I get.

```
[296159.772791] : Add. Sense: Medium not present - tray closed
[296159.772795] end_request: I/O error, dev sr0, sector 0
[296159.772796] Buffer I/O error on device sr0, logical block 0
[296159.772799] Buffer I/O error on device sr0, logical block 1
[296159.772800] Buffer I/O error on device sr0, logical block 2
[296159.772802] Buffer I/O error on device sr0, logical block 3
[296159.772803] Buffer I/O error on device sr0, logical block 4
[296159.772804] Buffer I/O error on device sr0, logical block 5
[296159.772806] Buffer I/O error on device sr0, logical block 6
[296159.772807] Buffer I/O error on device sr0, logical block 7
[296159.773817] sr 4:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[296159.773819] : Add. Sense: Medium not present - tray closed
[296159.773822] end_request: I/O error, dev sr0, sector 0
[296159.773823] Buffer I/O error on device sr0, logical block 0
[296159.774746] sr 4:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[296159.774748] : Add. Sense: Medium not present - tray closed
[296159.774751] end_request: I/O error, dev sr0, sector 4
[296159.774752] Buffer I/O error on device sr0, logical block 1
[306206.589987] usbcore: deregistering interface driver xpad
[306563.977375] usbcore: registered new interface driver xpad
[306563.977378] /usr/src/linux-headers-2.6.22-12-generic/xpad360/xpad.c: X-Box pad driver:v0.0.7
mike@mi:~$ 

```

I'm using gutsy.

---

### Post by vaineh on 2007-10-05
can someone clarify which of the xbox guitar heroes controllers ppl have had success with? i'd quite like to get one for using with frets on fire on ubuntu.

cheers.

---

### Post by eslin on 2007-10-05
> **Silent_Hunter said:**
> I followed the guide. I do not have a /dev/input/js0 or any other js* devices, so jscalibrator cannot calibrate anything. I checked dmesg. Here is the output I get.

```
[296159.772791] : Add. Sense: Medium not present - tray closed
[296159.772795] end_request: I/O error, dev sr0, sector 0
[296159.772796] Buffer I/O error on device sr0, logical block 0
[296159.772799] Buffer I/O error on device sr0, logical block 1
[296159.772800] Buffer I/O error on device sr0, logical block 2
[296159.772802] Buffer I/O error on device sr0, logical block 3
[296159.772803] Buffer I/O error on device sr0, logical block 4
[296159.772804] Buffer I/O error on device sr0, logical block 5
[296159.772806] Buffer I/O error on device sr0, logical block 6
[296159.772807] Buffer I/O error on device sr0, logical block 7
[296159.773817] sr 4:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[296159.773819] : Add. Sense: Medium not present - tray closed
[296159.773822] end_request: I/O error, dev sr0, sector 0
[296159.773823] Buffer I/O error on device sr0, logical block 0
[296159.774746] sr 4:0:0:0: [sr0] Device not ready: <6>: Sense Key : Not Ready [current] 
[296159.774748] : Add. Sense: Medium not present - tray closed
[296159.774751] end_request: I/O error, dev sr0, sector 4
[296159.774752] Buffer I/O error on device sr0, logical block 1
[306206.589987] usbcore: deregistering interface driver xpad
[306563.977375] usbcore: registered new interface driver xpad
[306563.977378] /usr/src/linux-headers-2.6.22-12-generic/xpad360/xpad.c: X-Box pad driver:v0.0.7
mike@mi:~$ 

```

I'm using gutsy.

I dont think you have successfully inserted the module to your running kernel.
in my dmesg i get:
```

root@mcgusto:~# dmesg | grep box
[   24.136000] input: Microsoft Xbox 360 Wireless Controller (PC) as /class/input/input5
[   24.136000] input: Microsoft Xbox 360 Wireless Controller (PC) as /class/input/input6
[   24.136000] input: Microsoft Xbox 360 Wireless Controller (PC) as /class/input/input7
[   24.136000] input: Microsoft Xbox 360 Wireless Controller (PC) as /class/input/input8
[   24.136000] /home/eslin/FILES/xpad/gentoo/xpad.c: driver for Xbox controllers v0.1.7

```

but your module seems to report v0.0.7

br
eslin

---

### Post by aparedes on 2007-10-05
I have the M$ Xbox 360 Wireless Receiver but what i want to use is the headset. Acutally it is the zx-6000 headset. has anyone been able to use it on ubuntu? how?
Thanks

---

### Post by ouellettesr on 2007-10-07
OK, thanks to silent_hunter for solving my problem. This is how I got my wired 360 controller working on Gutsy.

Code:

$mkdir //home/<user name>/.xpad360
$cd //home/<user name>/.xpad360
$wget "http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c"
$wget "http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h"
#gedit Makefile

Copy and Paste this text:

obj-m := xpad.o
KDIR := /lib/modules/$(shell uname -r)/build
EXTRA_CFLAGS=-I$(shell pwd)
all:
$(MAKE) modules -C $(KDIR) SUBDIRS=$(shell pwd)
install:
mv -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick

Make sure you hit tab before, $make, and mv -f so it looks lke this:

obj-m := xpad.o
KDIR := /lib/modules/$(shell uname -r)/build
EXTRA_CFLAGS=-I$(shell pwd)
all:
      $(MAKE) modules -C $(KDIR) SUBDIRS=$(shell pwd)
install:
      mv -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick

Save and exit.

$make
$make install
$update-modules
$sudo depmod
$modprobe -r xpad
$modprobe joydev usbhid xpad

Now to see if everything worked:

$cat /dev/input/js0

You should see a bunch of weird characters.

You can now install jscalibrator.

Thanks again Poof, and Silent Hunter for bringing me 360 controller support to my Ubuntu.

---

### Post by Silent_Hunter on 2007-10-09
> **ouellettesr said:**
> OK, thanks to silent_hunter for solving my problem. This is how I got my wired 360 controller working on Gutsy.

Code:

$mkdir //home/<user name>/.xpad360
$cd //home/<user name>/.xpad360
$wget "http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c"
$wget "http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h"
#gedit Makefile

Copy and Paste this text:

obj-m := xpad.o
KDIR := /lib/modules/$(shell uname -r)/build
EXTRA_CFLAGS=-I$(shell pwd)
all:
$(MAKE) modules -C $(KDIR) SUBDIRS=$(shell pwd)
install:
mv -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick

Make sure you hit tab before, $make, and mv -f so it looks lke this:

obj-m := xpad.o
KDIR := /lib/modules/$(shell uname -r)/build
EXTRA_CFLAGS=-I$(shell pwd)
all:
      $(MAKE) modules -C $(KDIR) SUBDIRS=$(shell pwd)
install:
      mv -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick

Save and exit.

$make
$make install
$update-modules
$sudo depmod
$modprobe -r xpad
$modprobe joydev usbhid xpad

Now to see if everything worked:

$cat /dev/input/js0

You should see a bunch of weird characters.

You can now install jscalibrator.

Thanks again Poof, and Silent Hunter for bringing me 360 controller support to my Ubuntu.

You're welcome. I tried using your instructions for the wireless xbox360 controller, but I still do not have it working. I need some help. Here is what I did.

```
mike@mi:/usr/src$ sudo ln -s /usr/src/linux-headers-"`uname -r`" /usr/src/linux
```

Then I put this in a Makefile.

```
obj-m := xpad.o
KDIR := /lib/modules/$(shell uname -r)/build
EXTRA_CFLAGS=-I$(shell pwd)
all:
        $(MAKE) modules -C $(KDIR) SUBDIRS=$(shell pwd)
install:
        mv -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick
```

```
mike@mi:~/a$ wget "http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/k
ernel-2.6/drivers/usb/input/xpad.h"
Warning: wildcards not supported in HTTP.
--12:37:21--  http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h
           => `xpad.h'
Resolving xbox-linux.cvs.sourceforge.net... 66.35.250.90
Connecting to xbox-linux.cvs.sourceforge.net|66.35.250.90|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]

    [ <=>                                 ] 4,677         --.--K/s

12:37:21 (55.60 KB/s) - `xpad.h' saved [4677]

mike@mi:~/a$ wget "http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c"
Warning: wildcards not supported in HTTP.
--12:37:43--  http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c
           => `xpad.c'
Resolving xbox-linux.cvs.sourceforge.net... 66.35.250.90
Connecting to xbox-linux.cvs.sourceforge.net|66.35.250.90|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]

    [  <=>                                ] 22,485        89.05K/s

12:37:44 (89.02 KB/s) - `xpad.c' saved [22485]

mike@mi:~/a$ make
make modules -C /lib/modules/2.6.22-13-generic/build SUBDIRS=/home/mike/a
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-13-generic'
  CC [M]  /home/mike/a/xpad.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/mike/a/xpad.mod.o
  LD [M]  /home/mike/a/xpad.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-13-generic'
mike@mi:~/a$ make install
mv -f xpad.ko /lib/modules/2.6.22-13-generic/kernel/drivers/input/joystick
mv: cannot move `xpad.ko' to `/lib/modules/2.6.22-13-generic/kernel/drivers/input/joystick/xpad.ko': Permission denied
make: *** [install] Error 1
mike@mi:~/a$ sudo make install
mv -f xpad.ko /lib/modules/2.6.22-13-generic/kernel/drivers/input/joystick
mike@mi:~/a$ sudo su -
root@mi:~# update-modules
root@mi:~# depmod
root@mi:~# modprobe -r xpad
root@mi:~# modprobe joydev usbhid xpad
root@mi:~# cat /dev/input/js0
cat: /dev/input/js0: No such file or directory
```

The device does not exist, so I tried unplugging the xbox controller and plugging it back in.

```
mike@mi:~/a$ dmesg | tail
[59846.589017] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: closing device
[60282.153847] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: opening device
[60282.153917] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: closing device
[60282.155386] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: opening device
[60282.155403] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: closing device
[60282.179164] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: opening device
[60324.122180] usb 3-1.1: USB disconnect, address 4
[60324.122183] usb 3-1.1.1: USB disconnect, address 5
[60324.123272] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: closing device
[61445.451545] usbcore: deregistering interface driver xpad
```

```
mike@mi:~/a$ tail /var/log/messages
Oct  8 11:52:28 mi kernel: [60282.155386] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: opening device
Oct  8 11:52:28 mi kernel: [60282.155403] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: closing device
Oct  8 11:52:28 mi kernel: [60282.179164] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: opening device
Oct  8 11:53:10 mi kernel: [60324.122180] usb 3-1.1: USB disconnect, address 4
Oct  8 11:53:10 mi kernel: [60324.122183] usb 3-1.1.1: USB disconnect, address 5
Oct  8 11:53:10 mi kernel: [60324.123272] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: closing device
Oct  8 12:05:18 mi -- MARK --
Oct  8 12:11:54 mi kernel: [61445.451545] usbcore: deregistering interface driver xpad
Oct  8 12:25:18 mi -- MARK --
Oct  8 12:45:18 mi -- MARK --
mike@mi:~/a$ 
```

---

### Post by ouellettesr on 2007-10-16
You know man im not really sure whats going on with your setup, I do know as soon as I got a kernel upgrade from the gutsy updates, It stopped working. One other thing is that I am using a wired controller. So im not really sure how the process goes for your wireless controller. Sorry I cant be of any help to you.

---

### Post by Gasten on 2007-10-19
Hey, can't we have a Ubuntu Kernel dev have a quick look at this and maybe include this in the official kernel? If not in gutsy, but in Hardy?

---

### Post by soulbreak on 2007-10-22
The jsX directory never gets created.   Its the same problem KSI is having.  I'm using a Joytech wired 360 controller.

modprobe then unplug and replug.
orion@nixtop:~$ sudo modprobe -r xpad joydev
orion@nixtop:~$ sudo tail -fn0 /var/log/messages
Oct 22 11:30:49 nixtop kernel: [ 5380.568000] usb 1-1: new full speed USB device using uhci_hcd and address 5
Oct 22 11:30:50 nixtop kernel: [ 5380.780000] usb 1-1: configuration #1 chosen from 1 choice
Oct 22 11:30:50 nixtop kernel: [ 5381.124000] usbcore: registered new interface driver xpad
Oct 22 11:30:50 nixtop kernel: [ 5381.124000] /home/orion/.xpad360/xpad.c: X-Box pad driver:v0.0.7

I'm using po0fs files.

---

### Post by soulbreak on 2007-10-22
bump

---

### Post by darundal on 2007-10-22
None of those worked for me...

---

### Post by soulbreak on 2007-10-23
when you say none do you mean the source files as well because that is my next step I guess.  That or buy a controller I know will work with fiesty, any suggestions?

---

### Post by FighterOfTheNightMan on 2007-10-29
Hi,

I'm using Gutsy Gibbon and am trying to get a 360 controller working.  I'm using one of the ones that came with the system and a recharge kit to connect it via USB.  I don't have a *wired* controller.  I'm using the guide made by ouellettesr.  I've downloaded everything necessary, but when I get to the point where I type in 'modprobe joydev usbhid xpad' (without the quotes), I get the following error:  

[email]elwood@elwood-desktop:~/.xpad[/email]360$ sudo modprobe joydev usbhid xpad
[sudo] password for elwood:
FATAL: Error inserting joydev (/lib/modules/2.6.22-14-generic/kernel/drivers/input/joydev.ko): Unknown symbol in module, or unknown parameter (see dmesg)

This is what dmesg has to say in regard to joydev:

  277.009393] joydev: Unknown parameter `usbhid'

I could be wrong, but is this just a simple matter of changing some text or is it because I don't have a genuine wired controller?  I would be grateful for any suggestions.

Regards,

Brandon

---

### Post by Crafty Kisses on 2007-10-29
> **po0f said:**
> To people who can't get Xbox 360 controllers working with Feisty,

Attached are a modified xpad.c, xpad.h, and accompanying Makefile to get it working.  I found a modified-for-Feisty set of source files somewhere on these forums (I'd link it if I could find it), but the d-pad didn't work.  I've hacked d-pad support back into it.  Enjoy.

That should solve the issue right there. :)

---

### Post by FighterOfTheNightMan on 2007-10-29
*Update*

I tried using the hack versions of xpad.c and xpad.h and I'm still not getting anywhere.  I'm still getting to the same spot and failing.  dmesg is yielding something new:

[  681.800533] usbcore: registered new interface driver xpad
[  681.800542] /home/elwood/.xpad360/xpad.c: driver for Xbox controllers v0.1.7
[  795.127445] usb 1-3: USB disconnect, address 3
[  819.175430] usb 1-3: new full speed USB device using ohci_hcd and address 4
[  819.387376] usb 1-3: configuration #1 chosen from 1 choice

It just doesn't seem to put anything into /dev/input/  Any idea on what could be the problem now?

Regards,

Brandon

---

### Post by atlfalcons866 on 2007-11-02
i compiled 2.6.23.1 and i selected xbox 360 remote support and it worked

---

### Post by go_beep_yourself on 2007-11-03
> **atlfalcons866 said:**
> i compiled 2.6.23.1 and i selected xbox 360 remote support and it worked

Where do you find that option in menuconfig?

---

### Post by go_beep_yourself on 2007-11-03
> **atlfalcons866 said:**
> i compiled 2.6.23.1 and i selected xbox 360 remote support and it worked

Do you have a wireless or wired controller. What is the module name of what you enabled?

---

### Post by atlfalcons866 on 2007-11-04
wired i selected it in menuconfig

---

### Post by Kratos on 2007-11-04
> **FighterOfTheNightMan said:**
> *Update*

I tried using the hack versions of xpad.c and xpad.h and I'm still not getting anywhere.  I'm still getting to the same spot and failing.  dmesg is yielding something new:

[  681.800533] usbcore: registered new interface driver xpad
[  681.800542] /home/elwood/.xpad360/xpad.c: driver for Xbox controllers v0.1.7
[  795.127445] usb 1-3: USB disconnect, address 3
[  819.175430] usb 1-3: new full speed USB device using ohci_hcd and address 4
[  819.387376] usb 1-3: configuration #1 chosen from 1 choice

It just doesn't seem to put anything into /dev/input/  Any idea on what could be the problem now?

Regards,

Brandon


I have the same problem. I'm not using a Microsoft-branded Xbox 360 controller, but a Logitech Chillstream, which is supported by the xpad driver. I am using the CVS version, though.

---

### Post by Jojo12a on 2007-11-05
To easify the creation of new compiles after kernel updates, I have created a basic module-assistant package. Install it as follows:

```

# first, download [ATTACH]49205[/ATTACH]
# install prerequisites and package (has to be executed wherever you have put the deb
sudo apt-get install module-assistant
sudo dpkg -i xpad360-source_0.0.7_all.deb
# go to the compilation directory
cd /usr/src
# this compiles and installs a new module package
sudo m-a a-i xpad360
```

I also attached the source package ([ATTACH]49206[/ATTACH]) from which I created this. This package could damage your system, kill your cat or set your house on fire, so I don't guarantee anything. It works for me anyway.

---

### Post by desertboy on 2007-12-02
> **ouellettesr said:**
> OK, thanks to silent_hunter for solving my problem. This is how I got my wired 360 controller working on Gutsy.

Code:

$mkdir //home/<user name>/.xpad360
$cd //home/<user name>/.xpad360
$wget "http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c"
$wget "http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h"
#gedit Makefile

Copy and Paste this text:

obj-m := xpad.o
KDIR := /lib/modules/$(shell uname -r)/build
EXTRA_CFLAGS=-I$(shell pwd)
all:
$(MAKE) modules -C $(KDIR) SUBDIRS=$(shell pwd)
install:
mv -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick

Make sure you hit tab before, $make, and mv -f so it looks lke this:

obj-m := xpad.o
KDIR := /lib/modules/$(shell uname -r)/build
EXTRA_CFLAGS=-I$(shell pwd)
all:
      $(MAKE) modules -C $(KDIR) SUBDIRS=$(shell pwd)
install:
      mv -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick

Save and exit.

$make
$make install
$update-modules
$sudo depmod
$modprobe -r xpad
$modprobe joydev usbhid xpad

Now to see if everything worked:

$cat /dev/input/js0

You should see a bunch of weird characters.

You can now install jscalibrator.

Thanks again Poof, and Silent Hunter for bringing me 360 controller support to my Ubuntu.


Thanks works perfectly

---

### Post by Helmi on 2007-12-12
Did anyone yet get the wireless Xpad360 working under gutsy? I tried the installation instructions from the post before mine but that doesn't seem to work.

Any ideas?

---

### Post by elcasey on 2007-12-19
Is something still hosed? I get errors for either joydev or usbhid in Gutsy using the X-plorer wired GH2 controller. What gives?

---

### Post by Jeice on 2007-12-23
Does anyone know how to get the Mad Catz Xbox 360 controller working in Gutsy? I tried to use the directions for a normal xbox 360 controller in feisty, but as you can guess, that didn't work. What should I do?


PS: I'm not a complete beginner, but pretty close to one

---

### Post by sorak on 2007-12-28
using two gamepads, mad catz 360, and joytech neo se 360

okay, so i had the following problem, and found no solutions in the forums:

xpad driver compiles fine
module loads fine
no freaking /dev/input/js0!

solution:

static struct usb_device_id xpad_table [] = {
        { USB_INTERFACE_INFO(  'X',  'B',   0 ) }, /* Xbox USB-IF not approved class */
        { USB_INTERFACE_INFO(   3 ,   0 ,   0 ) }, /* for Joytech Advanced Controller */
/* for some reasons USB_INTERFACE_INFO won't work when more than
 * one identical info is there. Therefore the IDs are added. */
//      { USB_INTERFACE_INFO( 255 ,  93 ,   1 ) }, /* Xbox 360 */
//      { USB_INTERFACE_INFO( 255 ,  93 , 129 ) }, /* Xbox 360 Wireless */
        { USB_DEVICE(0x045e, 0x028e) }, /* Xbox 360 Controller */
        { USB_DEVICE(0x045e, 0x0291) }, /* Xbox 360 Wireless Controller */
        { USB_DEVICE(0x045e, 0x0719) }, /* Xbox 360 Wireless PC Receiver */
        { USB_DEVICE(0x1430, 0x4748) }, /* RedOctane Guitar Hero X-plorer */
        { USB_DEVICE(0x0738, 0x4716) }, /* Mad Catz 360 */
        { USB_DEVICE(0x162e, 0xbeef) }, /* Joytech Neo Se */
        { }
};

notice the two entries at the end. you need also need the following definitions:
static const struct xpad_device xpad_device[] = {
        /* please keep those ordered wrt. vendor/product ids
          vendor, product, name, type     
        { 0x0738, 0x4716, "Mad Catz Xbox 360 Controller", GAMEPAD_XBOX360 },
        { 0x162e, 0xbeef, "Joytech Neo Se", GAMEPAD_XBOX360 },

i got the hex device ids from lsusb
please note im using xpad v0.1.7
both of my controllers now work simultaneously

good luck!

---

### Post by littl3b0y on 2007-12-31
Thanks for pointing me in the right direction although I still can´t get my mad catz 360 to work
this is my lsusb:
Bus 003 Device 005: ID 0738:4716 Mad Catz, Inc. 


modprobe loads xpad.ko just fine


/dev/input/js0  still doesn´t exist


this is my modified xpad.c as per your post

```
/*
 * X-Box gamepad - v0.0.7
 *
 * Copyright (c) 2002 Marko Friedemann <mfr@bmx-chemnitz.de>
 *               2004 Oliver Schwartz <Oliver.Schwartz@gmx.de>,
 *                    Steven Toth <steve@toth.demon.co.uk>,
 *                    Franz Lehner <franz@caos.at>,
 *                    Ivan Hawkes <blackhawk@ivanhawkes.com>
 *               2005 Dominic Cerquetti <binary1230@yahoo.com>
 *               2006 Adam Buchbinder <adam.buchbinder@gmail.com>
 *               2007 satore <satoren@gmail.com>
 *		
 * This program is free software; you can redistribute it and/or
 * modify it under the terms of the GNU General Public License as
 * published by the Free Software Foundation; either version 2 of
 * the License, or (at your option) any later version.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA
 *
 *
 * This driver is based on:
 *  - information from     http://euc.jp/periphs/xbox-controller.ja.html
 *  - the iForce driver    drivers/char/joystick/iforce.c
 *  - the skeleton-driver  drivers/usb/usb-skeleton.c
 *
 * Thanks to:
 *  - ITO Takayuki for providing essential xpad information on his website
 *  - Vojtech Pavlik     - iforce driver / input subsystem
 *  - Greg Kroah-Hartman - usb-skeleton driver
 *  - XBOX Linux project - extra USB id's
 *
 * TODO:
 *  - fine tune axes (especially trigger axes)
 *  - fix "analog" buttons (reported as digital now)
 *  - get rumble working
 *  - need USB IDs for other dance pads
 *
 * History:
 *
 * 2002-06-27 - 0.0.1 : first version, just said "XBOX HID controller"
 *
 * 2002-07-02 - 0.0.2 : basic working version
 *  - all axes and 9 of the 10 buttons work (german InterAct device)
 *  - the black button does not work
 *
 * 2002-07-14 - 0.0.3 : rework by Vojtech Pavlik
 *  - indentation fixes
 *  - usb + input init sequence fixes
 *
 * 2002-07-16 - 0.0.4 : minor changes, merge with Vojtech's v0.0.3
 *  - verified the lack of HID and report descriptors
 *  - verified that ALL buttons WORK
 *  - fixed d-pad to axes mapping
 *
 * 2002-07-17 - 0.0.5 : simplified d-pad handling
 *
 * 2004-10-02 - 0.0.6 : DDR pad support
 *  - borrowed from the XBOX linux kernel
 *  - USB id's for commonly used dance pads are present
 *  - dance pads will map D-PAD to buttons, not axes
 *  - pass the module paramater 'dpad_to_buttons' to force
 *    the D-PAD to map to buttons if your pad is not detected
 * 2007-3-11 - 0.0.7 : XBox 360 Controller support
 */

#include <linux/kernel.h>
#include <linux/init.h>
#include <linux/slab.h>
#include <linux/stat.h>
#include <linux/module.h>
#include <linux/moduleparam.h>
#include <linux/smp_lock.h>
#include <linux/usb/input.h>

#define DRIVER_VERSION "v0.0.7"
#define DRIVER_AUTHOR "Marko Friedemann <mfr@bmx-chemnitz.de>"
#define DRIVER_DESC "X-Box pad driver"

#define XPAD_PKT_LEN 32

/* xbox d-pads should map to buttons, as is required for DDR pads
   but we map them to axes when possible to simplify things */
#define MAP_DPAD_TO_BUTTONS    0
#define MAP_DPAD_TO_AXES       1
#define MAP_DPAD_TO_AXES_X360       2
#define MAP_DPAD_UNKNOWN       -1

static int dpad_to_buttons;
module_param(dpad_to_buttons, bool, S_IRUGO);
MODULE_PARM_DESC(dpad_to_buttons, "Map D-PAD to buttons rather than axes for unknown pads");

static const struct xpad_device {
	u16 idVendor;
	u16 idProduct;
	char *name;
	u8 dpad_mapping;
} xpad_device[] = {
	{ 0x045e, 0x0202, "Microsoft X-Box pad v1 (US)", MAP_DPAD_TO_AXES },
	{ 0x045e, 0x0289, "Microsoft X-Box pad v2 (US)", MAP_DPAD_TO_AXES },
	{ 0x045e, 0x0285, "Microsoft X-Box pad (Japan)", MAP_DPAD_TO_AXES },
	{ 0x045e, 0x0287, "Microsoft Xbox Controller S", MAP_DPAD_TO_AXES },
	{ 0x045e, 0x028e, "Microsoft Xbox 360 Controller", MAP_DPAD_TO_AXES_X360},
	{ 0x0c12, 0x8809, "RedOctane Xbox Dance Pad", MAP_DPAD_TO_BUTTONS },
	{ 0x044f, 0x0f07, "Thrustmaster, Inc. Controller", MAP_DPAD_TO_AXES },
	{ 0x046d, 0xca84, "Logitech Xbox Cordless Controller", MAP_DPAD_TO_AXES },
	{ 0x046d, 0xca88, "Logitech Compact Controller for Xbox", MAP_DPAD_TO_AXES },
	{ 0x05fd, 0x1007, "Mad Catz Controller (unverified)", MAP_DPAD_TO_AXES },
	{ 0x05fd, 0x107a, "InterAct 'PowerPad Pro' X-Box pad (Germany)", MAP_DPAD_TO_AXES },
	{ 0x0738, 0x4516, "Mad Catz Control Pad", MAP_DPAD_TO_AXES },
	{ 0x0738, 0x4522, "Mad Catz LumiCON", MAP_DPAD_TO_AXES },
	{ 0x0738, 0x4526, "Mad Catz Control Pad Pro", MAP_DPAD_TO_AXES },
	{ 0x0738, 0x4536, "Mad Catz MicroCON", MAP_DPAD_TO_AXES },
	{ 0x0738, 0x4540, "Mad Catz Beat Pad", MAP_DPAD_TO_BUTTONS },
	{ 0x0738, 0x4556, "Mad Catz Lynx Wireless Controller", MAP_DPAD_TO_AXES },
	{ 0x0738, 0x6040, "Mad Catz Beat Pad Pro", MAP_DPAD_TO_BUTTONS },
	{ 0x0c12, 0x8802, "Zeroplus Xbox Controller", MAP_DPAD_TO_AXES },
	{ 0x0c12, 0x8810, "Zeroplus Xbox Controller", MAP_DPAD_TO_AXES },
	{ 0x0c12, 0x9902, "HAMA VibraX - *FAULTY HARDWARE*", MAP_DPAD_TO_AXES },
	{ 0x0e4c, 0x1097, "Radica Gamester Controller", MAP_DPAD_TO_AXES },
	{ 0x0e4c, 0x2390, "Radica Games Jtech Controller", MAP_DPAD_TO_AXES},
	{ 0x0e6f, 0x0003, "Logic3 Freebird wireless Controller", MAP_DPAD_TO_AXES },
	{ 0x0e6f, 0x0005, "Eclipse wireless Controller", MAP_DPAD_TO_AXES },
	{ 0x0e6f, 0x0006, "Edge wireless Controller", MAP_DPAD_TO_AXES },
	{ 0x0e8f, 0x0201, "SmartJoy Frag Xpad/PS2 adaptor", MAP_DPAD_TO_AXES },
	{ 0x0f30, 0x0202, "Joytech Advanced Controller", MAP_DPAD_TO_AXES },
	{ 0x0f30, 0x8888, "BigBen XBMiniPad Controller", MAP_DPAD_TO_AXES },
	{ 0x102c, 0xff0c, "Joytech Wireless Advanced Controller", MAP_DPAD_TO_AXES },
	{ 0x12ab, 0x8809, "Xbox DDR dancepad", MAP_DPAD_TO_BUTTONS },
	{ 0x1430, 0x8888, "TX6500+ Dance Pad (first generation)", MAP_DPAD_TO_BUTTONS },
	{ 0xffff, 0xffff, "Chinese-made Xbox Controller", MAP_DPAD_TO_AXES },
	{ 0x0000, 0x0000, "Generic X-Box pad", MAP_DPAD_UNKNOWN },
	{ 0x0738, 0x4716, "Mad Catz Xbox 360 Controller", MAP_DPAD_TO_AXES_X360 },
	{ 0x162e, 0xbeef, "Joytech Neo Se", MAP_DPAD_TO_AXES_X360 }
};

static const signed short xpad_btn[] = {
	BTN_A, BTN_B, BTN_C, BTN_X, BTN_Y, BTN_Z,	/* "analog" buttons */
	BTN_START, BTN_BACK, BTN_THUMBL, BTN_THUMBR,	/* start/back/sticks */
	-1						/* terminating entry */
};
/* only used if MAP_DPAD_TO_AXES_X360 */
static const signed short xpad_btn_x360[] = {
	BTN_0, BTN_1, BTN_2, BTN_3,			/* d-pad as buttons */
	BTN_TL, BTN_TR,					/* Button LB/RB */
	BTN_MODE,					/* The big X */
	-1		
};

/* only used if MAP_DPAD_TO_BUTTONS */
static const signed short xpad_btn_pad[] = {
	BTN_LEFT, BTN_RIGHT,		/* d-pad left, right */
	BTN_0, BTN_1,			/* d-pad up, down (XXX names??) */
	-1				/* terminating entry */
};

static const signed short xpad_abs[] = {
	ABS_X, ABS_Y,		/* left stick */
	ABS_RX, ABS_RY,		/* right stick */
	ABS_Z, ABS_RZ,		/* triggers left/right */
	-1			/* terminating entry */
};

/* only used if MAP_DPAD_TO_AXES */
static const signed short xpad_abs_pad[] = {
	ABS_HAT0X, ABS_HAT0Y,	/* d-pad axes */
	-1			/* terminating entry */
};


/* only used if MAP_DPAD_TO_AXES_X360 */
static const signed short xpad_abs_x360[] = {
	/* Commented out first entry!!!  NOT */
	ABS_HAT0X, ABS_HAT0Y,	/* d-pad axes */
	ABS_HAT1X, ABS_HAT1Y,	/* analogue buttons A + B */
	ABS_HAT2X, ABS_HAT2Y,	/* analogue buttons C + X */
	ABS_HAT3X, ABS_HAT3Y,	/* analogue buttons Y + Z */
	-1			/* terminating entry */
};


static struct usb_device_id xpad_table [] = {
	{ USB_INTERFACE_INFO('X', 'B', 0) },	/* X-Box USB-IF not approved class */
{ USB_INTERFACE_INFO( 3 , 0 , 0 ) }, /* for Joytech Advanced Controller */
/* for some reasons USB_INTERFACE_INFO won't work when more than
* one identical info is there. Therefore the IDs are added. */
// { USB_INTERFACE_INFO( 255 , 93 , 1 ) }, /* Xbox 360 */
// { USB_INTERFACE_INFO( 255 , 93 , 129 ) }, /* Xbox 360 Wireless */
{ USB_DEVICE(0x045e, 0x028e) }, /* Xbox 360 Controller */
{ USB_DEVICE(0x045e, 0x0291) }, /* Xbox 360 Wireless Controller */
{ USB_DEVICE(0x045e, 0x0719) }, /* Xbox 360 Wireless PC Receiver */
//{ USB_DEVICE(0x1430, 0x4740 }, /* RedOctane Guitar Hero X-plorer */
{ USB_DEVICE(0x0738, 0x4716) }, /* Mad Catz 360 */
{ USB_DEVICE(0x162e, 0xbeef) }, /* Joytech Neo Se */
	{ }
};

MODULE_DEVICE_TABLE (usb, xpad_table);

struct usb_xpad {
	struct input_dev *dev;		/* input device interface */
	struct usb_device *udev;	/* usb device */

	struct urb *irq_in;		/* urb for interrupt in report */
	unsigned char *idata;		/* input data */
	dma_addr_t idata_dma;

	char phys[65];			/* physical device path */

	int dpad_mapping;		/* map d-pad to buttons or to axes */
};

/*
 *	xpad_process_packet
 *
 *	Completes a request by converting the data into events for the
 *	input subsystem.
 *
 *	The used report descriptor was taken from ITO Takayukis website:
 *	 http://euc.jp/periphs/xbox-controller.ja.html
 */

static void xpad_process_packet(struct usb_xpad *xpad, u16 cmd, unsigned char *data)
{
	struct input_dev *dev = xpad->dev;

	if(xpad->dpad_mapping == MAP_DPAD_TO_AXES_X360)
	{
		/* start/back buttons and stick press left/right */
		input_report_key(dev, BTN_START,  data[2] & 0x10);
		input_report_key(dev, BTN_BACK,   data[2] & 0x20);
		input_report_key(dev, BTN_THUMBL, data[2] & 0x40);
		input_report_key(dev, BTN_THUMBR, data[2] & 0x80);

		/* "analog" buttons A, B, X, Y */
		input_report_key(dev, BTN_A, (data[3] & 0x10) >> 4);
		input_report_key(dev, BTN_B, (data[3] & 0x20) >> 5);
		input_report_key(dev, BTN_Y, (data[3] & 0x80) >> 7);
		input_report_key(dev, BTN_X, (data[3] & 0x40) >> 6);
		input_report_key(dev, BTN_TL, data[3] & 0x01 );
		input_report_key(dev, BTN_TR, (data[3] & 0x02) >> 1);
		input_report_key(dev, BTN_MODE, (data[3] & 0x04) >> 2);

		/* Added all of the following... */
		/* dpad as... */
		/* AXES */
		/*input_report_abs(dev, ABS_HAT0X, !!(data[2] & 0x08) - !!(data[2] & 0x04));
		input_report_abs(dev, ABS_HAT0Y, !!(data[2] & 0x02) - !!(data[2] & 0x01));*/
		/* BUTTONS */
		input_report_key(dev, BTN_0, (data[2] & 0x04)); /*left*/
		input_report_key(dev, BTN_1, (data[2] & 0x08)); /*right*/
		input_report_key(dev, BTN_2, (data[2] & 0x01)); /*up*/
		input_report_key(dev, BTN_3, (data[2] & 0x02)); /*down*/

		/* triggers left/right */
		input_report_abs(dev, ABS_Z, data[4]);
		input_report_abs(dev, ABS_RZ, data[5]);

		/* left stick (Y axis needs to be flipped) */
		input_report_abs(dev, ABS_X, (__s16)(((__s16)data[7] << 8) | (__s16)data[6]));
		input_report_abs(dev, ABS_Y, ~(__s16)(((__s16)data[9] << 8) | data[8]));

		/* right stick */
		input_report_abs(dev, ABS_RX, (__s16) (((__s16)data[13] << 8) | data[12]));
		input_report_abs(dev, ABS_RY, (__s16) (((__s16)data[11] << 8) | data[10]));
	}
	else
	{
		/* left stick */
		input_report_abs(dev, ABS_X, (__s16) (((__s16)data[13] << 8) | data[12]));
		input_report_abs(dev, ABS_Y, (__s16) (((__s16)data[15] << 8) | data[14]));

		/* right stick */
		input_report_abs(dev, ABS_RX, (__s16) (((__s16)data[17] << 8) | data[16]));
		input_report_abs(dev, ABS_RY, (__s16) (((__s16)data[19] << 8) | data[18]));

		/* triggers left/right */
		input_report_abs(dev, ABS_Z, data[10]);
		input_report_abs(dev, ABS_RZ, data[11]);

		/* digital pad */
		if (xpad->dpad_mapping == MAP_DPAD_TO_AXES ) {
			input_report_abs(dev, ABS_HAT0X, !!(data[2] & 0x08) - !!(data[2] & 0x04));
			input_report_abs(dev, ABS_HAT0Y, !!(data[2] & 0x02) - !!(data[2] & 0x01));
		} else /* xpad->dpad_mapping == MAP_DPAD_TO_BUTTONS */ {
			input_report_key(dev, BTN_LEFT,  data[2] & 0x04);
			input_report_key(dev, BTN_RIGHT, data[2] & 0x08);
			input_report_key(dev, BTN_0,     data[2] & 0x01); // up
			input_report_key(dev, BTN_1,     data[2] & 0x02); // down
		}

		/* start/back buttons and stick press left/right */
		input_report_key(dev, BTN_START,  data[2] & 0x10);
		input_report_key(dev, BTN_BACK,   data[2] & 0x20);
		input_report_key(dev, BTN_THUMBL, data[2] & 0x40);
		input_report_key(dev, BTN_THUMBR, data[2] & 0x80);

		/* "analog" buttons A, B, X, Y */
		input_report_key(dev, BTN_A, data[4]);
		input_report_key(dev, BTN_B, data[5]);
		input_report_key(dev, BTN_X, data[6]);
		input_report_key(dev, BTN_Y, data[7]);

		/* "analog" buttons black, white */
		input_report_key(dev, BTN_C, data[8]);
		input_report_key(dev, BTN_Z, data[9]);
	}
	input_sync(dev);
}

static void xpad_irq_in(struct urb *urb)
{
	struct usb_xpad *xpad = urb->context;
	int retval;

	switch (urb->status) {
	case 0:
		/* success */
		break;
	case -ECONNRESET:
	case -ENOENT:
	case -ESHUTDOWN:
		/* this urb is terminated, clean up */
		dbg("%s - urb shutting down with status: %d", __FUNCTION__, urb->status);
		return;
	default:
		dbg("%s - nonzero urb status received: %d", __FUNCTION__, urb->status);
		goto exit;
	}

	xpad_process_packet(xpad, 0, xpad->idata);

exit:
	retval = usb_submit_urb (urb, GFP_ATOMIC);
	if (retval)
		err ("%s - usb_submit_urb failed with result %d",
		     __FUNCTION__, retval);
}

static int xpad_open (struct input_dev *dev)
{
	struct usb_xpad *xpad = dev->private;

	xpad->irq_in->dev = xpad->udev;
	if (usb_submit_urb(xpad->irq_in, GFP_KERNEL))
		return -EIO;

	return 0;
}

static void xpad_close (struct input_dev *dev)
{
	struct usb_xpad *xpad = dev->private;

	usb_kill_urb(xpad->irq_in);
}

static void xpad_set_up_abs(struct input_dev *input_dev, signed short abs)
{
	set_bit(abs, input_dev->absbit);

	switch (abs) {
	case ABS_X:
	case ABS_Y:
	case ABS_RX:
	case ABS_RY:	/* the two sticks */
		input_set_abs_params(input_dev, abs, -32768, 32767, 16, 128);
		break;
	case ABS_Z:
	case ABS_RZ:	/* the triggers */
	case ABS_HAT1X:	/* analogue button A */
	case ABS_HAT1Y:	/* analogue button B */
	case ABS_HAT2X:	/* analogue button C */
	case ABS_HAT2Y:	/* analogue button X */
	case ABS_HAT3X:	/* analogue button Y */
	case ABS_HAT3Y:	/* analogue button Z */
		input_set_abs_params(input_dev, abs, 0, 255, 0, 0);
		break;
	case ABS_HAT0X:
	case ABS_HAT0Y:	/* the d-pad (only if MAP_DPAD_TO_AXES) */
		input_set_abs_params(input_dev, abs, -1, 1, 0, 0);
		break;
	}
}

static int xpad_probe(struct usb_interface *intf, const struct usb_device_id *id)
{
	struct usb_device *udev = interface_to_usbdev (intf);
	struct usb_xpad *xpad;
	struct input_dev *input_dev;
	struct usb_endpoint_descriptor *ep_irq_in;
	int i;
	int probedDevNum = -1;	/* this takes the index into the known devices
				   array for the recognized device */

	for (i = 0; xpad_device[i].idVendor; i++) {
		if ((le16_to_cpu(udev->descriptor.idVendor) == xpad_device[i].idVendor) &&
		    (le16_to_cpu(udev->descriptor.idProduct) == xpad_device[i].idProduct))
		{
			probedDevNum=i;
			break;
		}
	}
	/* sanity check, did we recognize this device? if not, fail */
	if ((probedDevNum == -1) || (!xpad_device[probedDevNum].idVendor &&
				     !xpad_device[probedDevNum].idProduct))
	{
		return -ENODEV;
	}

	if(xpad_device[probedDevNum].dpad_mapping == MAP_DPAD_TO_AXES_X360)
	{
		if(intf->cur_altsetting->desc.bInterfaceProtocol != 1)
		{
			return -ENODEV;
		}
	}
	xpad = kzalloc(sizeof(struct usb_xpad), GFP_KERNEL);
	input_dev = input_allocate_device();
	if (!xpad || !input_dev)
		goto fail1;

	xpad->idata = usb_buffer_alloc(udev, XPAD_PKT_LEN,
				       GFP_ATOMIC, &xpad->idata_dma);
	if (!xpad->idata)
		goto fail1;

	xpad->irq_in = usb_alloc_urb(0, GFP_KERNEL);
	if (!xpad->irq_in)
		goto fail2;

	xpad->udev = udev;
	xpad->dpad_mapping = xpad_device[probedDevNum].dpad_mapping;
	if (xpad->dpad_mapping == MAP_DPAD_UNKNOWN)
		xpad->dpad_mapping = dpad_to_buttons;
	xpad->dev = input_dev;
	usb_make_path(udev, xpad->phys, sizeof(xpad->phys));
	strlcat(xpad->phys, "/input0", sizeof(xpad->phys));

	input_dev->name = xpad_device[probedDevNum].name;
	input_dev->phys = xpad->phys;
	usb_to_input_id(udev, &input_dev->id);
	input_dev->cdev.dev = &intf->dev;
	input_dev->private = xpad;
	input_dev->open = xpad_open;
	input_dev->close = xpad_close;

	input_dev->evbit[0] = BIT(EV_KEY) | BIT(EV_ABS);

	/* set up buttons */
	for (i = 0; xpad_btn[i] >= 0; i++)
		set_bit(xpad_btn[i], input_dev->keybit);
	if (xpad->dpad_mapping == MAP_DPAD_TO_BUTTONS)
		for (i = 0; xpad_btn_pad[i] >= 0; i++)
			set_bit(xpad_btn_pad[i], input_dev->keybit);

	if (xpad->dpad_mapping == MAP_DPAD_TO_AXES_X360)
		for (i = 0; xpad_btn_x360[i] >= 0; i++)
			set_bit(xpad_btn_x360[i], input_dev->keybit);

	/* set up axes */
	for (i = 0; xpad_abs[i] >= 0; i++)
		xpad_set_up_abs(input_dev, xpad_abs[i]);
	if (xpad->dpad_mapping == MAP_DPAD_TO_AXES)
		for (i = 0; xpad_abs_pad[i] >= 0; i++)
		    xpad_set_up_abs(input_dev, xpad_abs_pad[i]);
	if(xpad->dpad_mapping == MAP_DPAD_TO_AXES_X360)
		for (i = 0; xpad_abs_x360[i] >= 0; i++)
		    xpad_set_up_abs(input_dev, xpad_abs_x360[i]);

	ep_irq_in = &intf->cur_altsetting->endpoint[0].desc;
	usb_fill_int_urb(xpad->irq_in, udev,
			 usb_rcvintpipe(udev, ep_irq_in->bEndpointAddress),
			 xpad->idata, XPAD_PKT_LEN, xpad_irq_in,
			 xpad, ep_irq_in->bInterval);
	xpad->irq_in->transfer_dma = xpad->idata_dma;
	xpad->irq_in->transfer_flags |= URB_NO_TRANSFER_DMA_MAP;
	input_register_device(xpad->dev);

	usb_set_intfdata(intf, xpad);

	if(xpad->dpad_mapping == MAP_DPAD_TO_AXES_X360){
		char ledcmd[] = {1, 3, 0}; /* The LED-off command for Xbox-360 controllers */
    		int j;
		usb_bulk_msg(udev, usb_sndbulkpipe(udev,2), ledcmd, sizeof(ledcmd), &j, 1*HZ);/* 1*HZ = 1sec? */
	}
	return 0;

fail2:	usb_buffer_free(udev, XPAD_PKT_LEN, xpad->idata, xpad->idata_dma);
fail1:	input_free_device(input_dev);
	kfree(xpad);
	return -ENOMEM;

}

static void xpad_disconnect(struct usb_interface *intf)
{
	struct usb_xpad *xpad = usb_get_intfdata (intf);

	usb_set_intfdata(intf, NULL);
	if (xpad) {
		usb_kill_urb(xpad->irq_in);
		input_unregister_device(xpad->dev);
		usb_free_urb(xpad->irq_in);
		usb_buffer_free(interface_to_usbdev(intf), XPAD_PKT_LEN,
				xpad->idata, xpad->idata_dma);
		kfree(xpad);
	}
}

static struct usb_driver xpad_driver = {
	.name		= "xpad",
	.probe		= xpad_probe,
	.disconnect	= xpad_disconnect,
	.id_table	= xpad_table,
};

static int __init usb_xpad_init(void)
{
	int result = usb_register(&xpad_driver);
	if (result == 0)
		info(DRIVER_DESC ":" DRIVER_VERSION);
	return result;
}

static void __exit usb_xpad_exit(void)
{
	usb_deregister(&xpad_driver);
}

module_init(usb_xpad_init);
module_exit(usb_xpad_exit);

MODULE_AUTHOR(DRIVER_AUTHOR);
MODULE_DESCRIPTION(DRIVER_DESC);
MODULE_LICENSE("GPL");
```

Perhaps you could post your xpad.c ?

many thanks

---

### Post by Silent_Hunter on 2007-12-31
If you have a wireless controller I would read this thread.  [http://ubuntuforums.org/showthread.php?t=570642](http://ubuntuforums.org/showthread.php?t=570642)

Scroll down to this post:
[http://ubuntuforums.org/showpost.php?p=3744600&postcount=5](http://ubuntuforums.org/showpost.php?p=3744600&postcount=5)

---

### Post by HIM_Tattoos on 2008-01-05
Bump as i can't get xpad.h to download need some help, if anyone has it I could really use it.

---

### Post by EnsignR on 2008-01-06
> **HIM_Tattoos said:**
> Bump as i can't get xpad.h to download need some help, if anyone has it I could really use it.

xpad.h
```
wget "http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h"

```

xpad.c
```
wget "http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c
```

Paste that into your teminal and the files will be saved to the current directory. Otherwise they are available within the many archives in this thread.

cheers :KS

ps. I am so happy as I just got my X360 Wireless controller working by following the instructions from Nicolae in this thread:
[http://ubuntuforums.org/showthread.php?t=570642](http://ubuntuforums.org/showthread.php?t=570642)

---

### Post by Amirith on 2008-02-04
Sorry, miss post

---

### Post by Shadow Crest on 2008-02-09
(Ubuntu  7.10, HP Pavillion dv6449t laptop)

Hey, I used Jojo's installation method, and something happened during the install: 

```
shadowcrest@shadowcrest-laptop:~$ sudo dpkg -i xpad360-source_0.0.7_all.deb
(Reading database ... 125124 files and directories currently installed.)
Preparing to replace xpad360-source 0.0.7 (using xpad360-source_0.0.7_all.deb) ...
Unpacking replacement xpad360-source ...
Setting up xpad360-source (0.0.7) ...
shadowcrest@shadowcrest-laptop:~$ cd /usr/src
shadowcrest@shadowcrest-laptop:/usr/src$ sudo m-a a-i xpad360

Updated infos about 1 packages
Getting source for kernel version: 2.6.22-14-generic
Kernel headers available in /usr/src/linux
Creating symlink...
Couldn't create the /usr/src/linux symlink!
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package xpad360-module-2.6.22-14-generic needs to be reinstalled, but I can't find an archive for it.

Done!
unpack 
Extracting the package tarball, /usr/src/xpad360.tar.bz2, please wait...
"/usr/share/modass/packages/default.sh" build KVERS=2.6.22-14-generic KSRC=/usr/src/linux-headers-2.6.22-14-generic KDREV=2.6.22-14.47 kdist_image
Done with /usr/src/xpad360-module-2.6.22-14-generic_0.0.7+2.6.22-14.47_amd64.deb .
dpkg -Ei /usr/src/xpad360-module-2.6.22-14-generic_0.0.7+2.6.22-14.47_amd64.deb 
(Reading database ... 125124 files and directories currently installed.)
Preparing to replace xpad360-module-2.6.22-14-generic 0.0.7+2.6.22-14.46 (using .../xpad360-module-2.6.22-14-generic_0.0.7+2.6.22-14.47_amd64.deb) ...
Leaving `diversion of /lib/modules/2.6.22-14-generic/kernel/drivers/input/joystick/xpad.ko to /lib/modules/2.6.22-14-generic/kernel/drivers/input/joystick/xpad.ko.distrib by xpad360-module-2.6.22-14-generic'
Unpacking replacement xpad360-module-2.6.22-14-generic ...
Removing `diversion of /lib/modules/2.6.22-14-generic/kernel/drivers/input/joystick/xpad.ko to /lib/modules/2.6.22-14-generic/kernel/drivers/input/joystick/xpad.ko.distrib by xpad360-module-2.6.22-14-generic'
dpkg-divert: rename involves overwriting `/lib/modules/2.6.22-14-generic/kernel/drivers/input/joystick/xpad.ko' with
  different file `/lib/modules/2.6.22-14-generic/kernel/drivers/input/joystick/xpad.ko.distrib', not allowed
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
Removing `diversion of /lib/modules/2.6.22-14-generic/kernel/drivers/input/joystick/xpad.ko to /lib/modules/2.6.22-14-generic/kernel/drivers/input/joystick/xpad.ko.distrib by xpad360-module-2.6.22-14-generic'
dpkg-divert: rename involves overwriting `/lib/modules/2.6.22-14-generic/kernel/drivers/input/joystick/xpad.ko' with
  different file `/lib/modules/2.6.22-14-generic/kernel/drivers/input/joystick/xpad.ko.distrib', not allowed
dpkg: error processing /usr/src/xpad360-module-2.6.22-14-generic_0.0.7+2.6.22-14.47_amd64.deb (--install):
 subprocess new post-removal script returned error exit status 2
Leaving `diversion of /lib/modules/2.6.22-14-generic/kernel/drivers/input/joystick/xpad.ko to /lib/modules/2.6.22-14-generic/kernel/drivers/input/joystick/xpad.ko.distrib by xpad360-module-2.6.22-14-generic'
Removing `diversion of /lib/modules/2.6.22-14-generic/kernel/drivers/input/joystick/xpad.ko to /lib/modules/2.6.22-14-generic/kernel/drivers/input/joystick/xpad.ko.distrib by xpad360-module-2.6.22-14-generic'
dpkg-divert: rename involves overwriting `/lib/modules/2.6.22-14-generic/kernel/drivers/input/joystick/xpad.ko' with
  different file `/lib/modules/2.6.22-14-generic/kernel/drivers/input/joystick/xpad.ko.distrib', not allowed
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 /usr/src/xpad360-module-2.6.22-14-generic_0.0.7+2.6.22-14.47_amd64.deb

I: Direct installation failed, trying to post-install the dependencies

apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package xpad360-module-2.6.22-14-generic needs to be reinstalled, but I can't find an archive for it.
shadowcrest@shadowcrest-laptop:/usr/src$ FATAL: Could not rename /lib/modules/2.6.22-14-generic/modules.dep.temp into /lib/modules/2.6.22-14-generic/modules.dep: No such file or directory
FATAL: Could not rename /lib/modules/2.6.22-14-generic/modules.dep.temp into /lib/modules/2.6.22-14-generic/modules.dep: No such file or directory

```

Now, synaptic doesn't work, and I can't remove the xpad files.  Long story short: Help!

---

### Post by mehpluhmeh on 2008-02-28
alright, what about using the controller with pclinuxos? i tried a few different ways to do it but i'm not going to mod my kernel for it.. i tried to download the rmp for it and that wont work either.

---

### Post by roderick on 2008-03-09
I finally got my Mad Catz Beat Pad working. I initially tried using the source from CVS, but it apparently has some issues related to usb that are out of sync with the general Linux kernel. 

After three days of playing with that, I went back and downloaded the ubuntu kernel source tree and extracted the xpad.c and xpad.h from there. Version 0.0.6, which is included in the Ubuntu kernel, required the following two changes in order to make my beat pad work (who knew it was this simple:

```

--- xpad.c.orig 2008-03-09 23:58:32.000000000 -0230
+++ xpad.c      2008-03-10 00:39:56.000000000 -0230
@@ -121,6 +121,7 @@
        { 0x0738, 0x4540, "Mad Catz Beat Pad", MAP_DPAD_TO_BUTTONS, XTYPE_XBOX },
        { 0x0738, 0x4556, "Mad Catz Lynx Wireless Controller", MAP_DPAD_TO_AXES, XTYPE_XBOX },
        { 0x0738, 0x4716, "Mad Catz Wired Xbox 360 Controller", MAP_DPAD_TO_AXES, XTYPE_XBOX360 },
+       { 0x0738, 0x4740, "Mad Catz Beat Pad", MAP_DPAD_TO_BUTTONS, XTYPE_XBOX360 },
        { 0x0738, 0x6040, "Mad Catz Beat Pad Pro", MAP_DPAD_TO_BUTTONS, XTYPE_XBOX },
        { 0x0c12, 0x8802, "Zeroplus Xbox Controller", MAP_DPAD_TO_AXES, XTYPE_XBOX },
        { 0x0c12, 0x8810, "Zeroplus Xbox Controller", MAP_DPAD_TO_AXES, XTYPE_XBOX },
@@ -182,6 +183,7 @@
        { USB_INTERFACE_INFO('X', 'B', 0) },    /* X-Box USB-IF not approved class */
        { USB_DEVICE_INTERFACE_PROTOCOL(0x045e, 0x028e, 1) },   /* X-Box 360 controller */
        { USB_DEVICE_INTERFACE_PROTOCOL(0x1430, 0x4748, 1) },   /* RedOctane Guitar Hero X-plorer */
+       { USB_DEVICE_INTERFACE_PROTOCOL(0x0738, 0x4740, 1) },   /* Mad Catz Beat Pad */
        { }
 };

```

Anyway, works with the above changes using ver 0.0.6 (against kernel 2.6.24 at least).

---

### Post by geoffjay on 2008-03-29
Using page 14 of this thread I was able to get a wireless controller going on 7.10 with only a small amount of trouble. What I'd like to know is whether it's possible to get 2 (or more) to work. If I try to connect using the sync button on both the controller and receiver nothing comes up in the dmesg output like it did when connecting the first. When I installed the modules it put a js0 -> js3 in my /dev/inputs dir so I would assume that that's meant for 4 joysticks. To test I also used jscalibrator and none of the input devices worked for the second controller. Has anyone made this work before?

---

### Post by Grumbel on 2008-04-11
I started a userspace driver using libusb, its available at:

[http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)

Should be pretty easy to get running, since it doesn't involve any Kernel recompilation. It is just a normal program that you start and then gives you a /dev/input/js0

It supports Xbox1 devices, Xbox360 USB gamepads and Xbox360 wireless gamepads. Xbox1 dancemats work too, but haven't been tested.

---

### Post by wootah on 2008-06-10
> **Grumbel said:**
> I started a userspace driver using libusb, its available at:

[http://pingus.seul.org/~grumbel/xboxdrv/]("http://pingus.seul.org/%7Egrumbel/xboxdrv/")

Should be pretty easy to get running, since it doesn't involve any Kernel recompilation. It is just a normal program that you start and then gives you a /dev/input/js0

It supports Xbox1 devices, Xbox360 USB gamepads and Xbox360 wireless gamepads. Xbox1 dancemats work too, but haven't been tested.

I'm going to give this a try and perhaps write a nice how-to for you :)

---

### Post by wootah on 2008-06-11
Howto posted here for use of grumbel's driver!
[URL="http://ubuntuforums.org/showthread.php?t=825464"]
http://ubuntuforums.org/showthread.php?t=825464[/URL] - Howto: Use Xbox Controllers (original, 360, 360 wireless, 360 guitar) with Linux

---

### Post by midkniht on 2008-07-24
mod to driver and userspace driver to add support for rockband guitar instructions here:
[http://www.jamminnet.com/rockbandguitarandlinux]("http://www.jamminnet.com/rockbandguitarandlinux")

---

### Post by schiz on 2008-08-13
How about support for the wireless guitar, the "Les Paul" for the 360?
It doesn't seem to hard to get it to work, it is supposed to work under windows, and I really hope you could get that to work as well.
Anyways I really like what has been done already! Many thanks!

---

### Post by Mistrblank on 2008-08-14
> **schiz said:**
> How about support for the wireless guitar, the "Les Paul" for the 360?
It doesn't seem to hard to get it to work, it is supposed to work under windows, and I really hope you could get that to work as well.
Anyways I really like what has been done already! Many thanks!

I will confirm that with the MS Wireless Receiver configured, a wireless Les Paul will work just like the wired Explorer guitars.

---

### Post by Ectara on 2008-11-10
> **Silent_Hunter said:**
> You're welcome. I tried using your instructions for the wireless xbox360 controller, but I still do not have it working. I need some help. Here is what I did.

```
mike@mi:/usr/src$ sudo ln -s /usr/src/linux-headers-"`uname -r`" /usr/src/linux
```

Then I put this in a Makefile.

```
obj-m := xpad.o
KDIR := /lib/modules/$(shell uname -r)/build
EXTRA_CFLAGS=-I$(shell pwd)
all:
        $(MAKE) modules -C $(KDIR) SUBDIRS=$(shell pwd)
install:
        mv -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick
```

```
mike@mi:~/a$ wget "http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/k
ernel-2.6/drivers/usb/input/xpad.h"
Warning: wildcards not supported in HTTP.
--12:37:21--  http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h
           => `xpad.h'
Resolving xbox-linux.cvs.sourceforge.net... 66.35.250.90
Connecting to xbox-linux.cvs.sourceforge.net|66.35.250.90|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]

    [ <=>                                 ] 4,677         --.--K/s

12:37:21 (55.60 KB/s) - `xpad.h' saved [4677]

mike@mi:~/a$ wget "http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c"
Warning: wildcards not supported in HTTP.
--12:37:43--  http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c
           => `xpad.c'
Resolving xbox-linux.cvs.sourceforge.net... 66.35.250.90
Connecting to xbox-linux.cvs.sourceforge.net|66.35.250.90|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]

    [  <=>                                ] 22,485        89.05K/s

12:37:44 (89.02 KB/s) - `xpad.c' saved [22485]

mike@mi:~/a$ make
make modules -C /lib/modules/2.6.22-13-generic/build SUBDIRS=/home/mike/a
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-13-generic'
  CC [M]  /home/mike/a/xpad.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/mike/a/xpad.mod.o
  LD [M]  /home/mike/a/xpad.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-13-generic'
mike@mi:~/a$ make install
mv -f xpad.ko /lib/modules/2.6.22-13-generic/kernel/drivers/input/joystick
mv: cannot move `xpad.ko' to `/lib/modules/2.6.22-13-generic/kernel/drivers/input/joystick/xpad.ko': Permission denied
make: *** [install] Error 1
mike@mi:~/a$ sudo make install
mv -f xpad.ko /lib/modules/2.6.22-13-generic/kernel/drivers/input/joystick
mike@mi:~/a$ sudo su -
root@mi:~# update-modules
root@mi:~# depmod
root@mi:~# modprobe -r xpad
root@mi:~# modprobe joydev usbhid xpad
root@mi:~# cat /dev/input/js0
cat: /dev/input/js0: No such file or directory
```

The device does not exist, so I tried unplugging the xbox controller and plugging it back in.

```
mike@mi:~/a$ dmesg | tail
[59846.589017] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: closing device
[60282.153847] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: opening device
[60282.153917] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: closing device
[60282.155386] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: opening device
[60282.155403] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: closing device
[60282.179164] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: opening device
[60324.122180] usb 3-1.1: USB disconnect, address 4
[60324.122183] usb 3-1.1.1: USB disconnect, address 5
[60324.123272] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: closing device
[61445.451545] usbcore: deregistering interface driver xpad
```

```
mike@mi:~/a$ tail /var/log/messages
Oct  8 11:52:28 mi kernel: [60282.155386] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: opening device
Oct  8 11:52:28 mi kernel: [60282.155403] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: closing device
Oct  8 11:52:28 mi kernel: [60282.179164] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: opening device
Oct  8 11:53:10 mi kernel: [60324.122180] usb 3-1.1: USB disconnect, address 4
Oct  8 11:53:10 mi kernel: [60324.122183] usb 3-1.1.1: USB disconnect, address 5
Oct  8 11:53:10 mi kernel: [60324.123272] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: closing device
Oct  8 12:05:18 mi -- MARK --
Oct  8 12:11:54 mi kernel: [61445.451545] usbcore: deregistering interface driver xpad
Oct  8 12:25:18 mi -- MARK --
Oct  8 12:45:18 mi -- MARK --
mike@mi:~/a$ 
```
I'm actually a Debian user myself, but @Silent_Hunter,
You might have to put in a sudo or two before make and mv -f,
or doing a $su before hand

---

### Post by Ectara on 2008-11-10
> **eslin said:**
> I solved it.
Used information from [http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux](http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux)

I fetched these files
```

# wget "http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c"
# wget "http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h"

```

then I used the Makefile from ....... tar.gz-file
slightly modified for gutsy:
```

root@mcgusto:~/FILES/xpad/gentoo# cat Makefile 
obj-m := xpad.o
KDIR := /lib/modules/$(shell uname -r)/build
EXTRA_CFLAGS=-I$(shell pwd)
all:
        $(MAKE) modules -C $(KDIR) SUBDIRS=$(shell pwd)
install:
        mv -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick

```

make && make install
update-modules && sudo depmod
modprobe -r xpad
modprobe joydev usbhid xpad

now I was able to run jscalibrator on my "wireless xbox 360 controller".

As the gentoo-page states there are quirks with the wireless support:
[http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux#Wireless_360_controller](http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux#Wireless_360_controller)

Best regards
eslin

I try to compile the xpad driver for Debian sid, 2.6.25-2-686, and i get the following error.

[email]ectara@Valmar:~/.xpad[/email]360/xpad360/xpad360$ make
make modules -C /lib/modules/2.6.25-2-686/build SUBDIRS=/home/ectara/.xpad360/xpad360/xpad360
make[1]: Entering directory `/usr/src/linux-headers-2.6.25-2-686'
  CC [M]  /home/ectara/.xpad360/xpad360/xpad360/xpad.o
/home/ectara/.xpad360/xpad360/xpad360/xpad.c: In function ‘xpad_probe’:
/home/ectara/.xpad360/xpad360/xpad360/xpad.c:441: error: ‘struct input_dev’ has no member named ‘cdev’
/home/ectara/.xpad360/xpad360/xpad360/xpad.c:476: warning: ignoring return value of ‘input_register_device’, declared with attribute warn_unused_result
make[2]: *** [/home/ectara/.xpad360/xpad360/xpad360/xpad.o] Error 1
make[1]: *** [_module_/home/ectara/.xpad360/xpad360/xpad360] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.25-2-686'
make: *** [all] Error 2

Can anyone assist in this?

---

### Post by ncanna1 on 2008-11-10
I'm having the same problem as Ectara in Intrepid.  Anyone know why these errors are being returned?

---

### Post by ncanna1 on 2008-11-10
I'm actually having another problem with the controller now.  I accidentally used debconf -a while messing around with the 360 controller, which was also controlling the mouse, and now it forces the cursor to the top left corner of the screen.  Even when I try to calibrate it using jscalibrator, it will not let the cursor out of the top left corner.  If there is a way to undo the change made by debconf or a way to get the controller working, please help.

---

### Post by schenier on 2008-11-15
Hi,

I had the guitar controller working when in Ubuntu 8.04, but now that I upgraded it to 8.10, it it not seen at all.

I tried to redo everything, in case it was removed in the upgrade, and when I try to 'Make' the Makefile, this it the error I get :


[COLOR="Red"]make modules -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/schenier/.xpad360
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/schenier/.xpad360/xpad.o
/home/schenier/.xpad360/xpad.c: In function ‘xpad_open’:
/home/schenier/.xpad360/xpad.c:383: error: ‘struct input_dev’ has no member named ‘private’
/home/schenier/.xpad360/xpad.c: In function ‘xpad_close’:
/home/schenier/.xpad360/xpad.c:409: error: ‘struct input_dev’ has no member named ‘private’
/home/schenier/.xpad360/xpad.c: In function ‘xpad_probe’:
/home/schenier/.xpad360/xpad.c:497: error: ‘struct input_dev’ has no member named ‘cdev’
/home/schenier/.xpad360/xpad.c:498: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/schenier/.xpad360/xpad.o] Error 1
make[1]: *** [_module_/home/schenier/.xpad360] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [all] Error 2[/COLOR]


Are there some new changes to be made to the files (Makefile, xpad.c and xpad.h) since 8.10? Can we get them somewhere?

thank you,

---

### Post by crasherball on 2009-01-10
> **schenier said:**
> Hi,

I had the guitar controller working when in Ubuntu 8.04, but now that I upgraded it to 8.10, it it not seen at all.

I tried to redo everything, in case it was removed in the upgrade, and when I try to 'Make' the Makefile, this it the error I get :


[COLOR="Red"]make modules -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/schenier/.xpad360
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/schenier/.xpad360/xpad.o
/home/schenier/.xpad360/xpad.c: In function ‘xpad_open’:
/home/schenier/.xpad360/xpad.c:383: error: ‘struct input_dev’ has no member named ‘private’
/home/schenier/.xpad360/xpad.c: In function ‘xpad_close’:
/home/schenier/.xpad360/xpad.c:409: error: ‘struct input_dev’ has no member named ‘private’
/home/schenier/.xpad360/xpad.c: In function ‘xpad_probe’:
/home/schenier/.xpad360/xpad.c:497: error: ‘struct input_dev’ has no member named ‘cdev’
/home/schenier/.xpad360/xpad.c:498: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/schenier/.xpad360/xpad.o] Error 1
make[1]: *** [_module_/home/schenier/.xpad360] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [all] Error 2[/COLOR]


Are there some new changes to be made to the files (Makefile, xpad.c and xpad.h) since 8.10? Can we get them somewhere?

thank you,

i have exactly the same problem
does anybody know a solution?

---

### Post by Grumbel on 2009-01-10
> **crasherball said:**
> i have exactly the same problem
does anybody know a solution?
You have to use a version of xpad.c that is compatible with your kernel version.

Or alternatively simply use the xpad that already comes with the kernel or the xboxdrv userspace driver.

---

### Post by yoKenny on 2009-01-10
> **Grumbel said:**
> You have to use a version of xpad.c that is compatible with your kernel version.

There's any place where we can find the filename changes between every kernel version?

---

### Post by Grumbel on 2009-01-10
> **yoKenny said:**
> There's any place where we can find the filename changes between every kernel version?
I don't think so, but as said, the easiest way is to just use the xpad in the kernel. Why do you want to compile your own xpad anyway? The current one in the Ubuntu 8.10 kernel looks pretty solid and even has rumble support.

---

### Post by crasherball on 2009-01-10
> **Grumbel said:**
> You have to use a version of xpad.c that is compatible with your kernel version.

where exactly do i find this?
how do I make it?
do I have to make it at all?

---

### Post by Grumbel on 2009-01-10
> **crasherball said:**
> do I have to make it at all?
As said, xpad is part of the kernel and newer versions seem to work fine. So all you have to do is install a new enough kernel (i.e. the one that comes with Ubuntu 8.10 is fine). 

Or alternativly use xboxdrv:

[http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)

---

### Post by crasherball on 2009-01-11
I am using 8.10, and I still get this error-message
and I am using the kernel that came with 8.10 (2.6.27-9-generic)

---

### Post by Grumbel on 2009-01-11
> **crasherball said:**
> I am using 8.10, and I still get this error-message
Just use the xpad that comes with your kernel or xboxdrv if you prefer.

---

### Post by crasherball on 2009-01-11
well sorry, I dont get you.
how to I use "the xpad that comes with my kernel"
where is it?

---

### Post by Grumbel on 2009-01-11
> **crasherball said:**
> where is it?
Right there with all the other modules in /lib/modules/..., just plug in your gamepad and it should work automatically. Check dmesg after you have plugged in your gamepad.

---

### Post by crasherball on 2009-01-11
well, problem is:
when I "just" plug in the controller, the apad controls my mouse-curser. and the other buttons do noting at all O.o

not even in jscalibrator

---

### Post by Grumbel on 2009-01-11
> **crasherball said:**
> well, problem is:
when I "just" plug in the controller, the apad controls my mouse-curser. and the other buttons do noting at all O.o
Thats ok, it means its working :) To get rid of the mouse control thing see the "Xorg Trouble" section of:

[http://pingus.seul.org/~grumbel/tmp/md5/46b59180547f8ef58259b9fadb952d10-README](http://pingus.seul.org/~grumbel/tmp/md5/46b59180547f8ef58259b9fadb952d10-README)

Note: When you modify /etc/hal/fdi/policy/preferences.fdi you have to use "Microsoft X-Box 360 pad" instead of "Xbox Gamepad (userspace driver)".

---

### Post by lunarcloud on 2009-01-31
> **Grumbel said:**
> ... When you modify /etc/hal/fdi/policy/preferences.fdi ...

Where are you supposed to add the lines?
At the end?

---

### Post by The Joe on 2009-01-31
Ignore this post - I didn't mean to put it here

---

### Post by Grumbel on 2009-01-31
> **zarquad said:**
> Where are you supposed to add the lines?
At the end?
At the end will not work, you have to insert them in the middle of the <device> section. You can also create a new file, like this:

/etc/hal/fdi/policy/xboxdrv_policy.fdi
```
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
    <match key="input.product" string="Xbox Gamepad (userspace driver)">     
      <remove key="input.x11_driver" />
    </match>
  </device>
</deviceinfo>
```

In addition when you want to use keyboard emulation a file like this can help:

/etc/hal/fdi/preprobe/xboxdrv_preprobe.fdi
```
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
   <match key="input.product" string="Xbox Gamepad (userspace driver) - Keyboard Emulation">
     <addset key="info.capabilities" type="strlist">input.keys</addset>
   </match>
  </device>
</deviceinfo>
```

---

### Post by arsonistarchitect on 2009-03-05
i've looked over this thread and i still can't figure out...why?
sudo ./xboxdrv --id 0
gives me the error
command not found
also why when i typed 
 lsmod | grep uinput
nothing seemed to happen
i apologize if this is an easy fix or a stupid question i am new to this.

---

### Post by Grumbel on 2009-03-05
> **arsonistarchitect said:**
> sudo ./xboxdrv --id 0
gives me the error
command not found
You are either in the wrong directory or haven't yet compiled xboxdrv. See:

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

>  lsmod | grep uinput
nothing seemed to happen
Thats ok, it just means that uinput hasn't been loaded, type:

modprobe uinput

---

### Post by arsonistarchitect on 2009-03-05
modprobe uinput
doesn't seem to do anything:(

---

### Post by Grumbel on 2009-03-05
> **arsonistarchitect said:**
> modprobe uinput
doesn't seem to do anything:(
It means it works as expected. Most command line applications don't output stuff unless things go wrong.

---

### Post by thelastunavail on 2009-04-11
Ok im haveing the same problem and am useing a 3rd party xbox 360 controller called a "Pelican model #PL-3601" .. i tried the tread and did everything it still does not work in jscalibrator or my snes emulator games.. this is driving me crazy plz help! 

here is the output

```
lsusb
Bus 001 Device 005: ID 0e6f:0201  
Bus 001 Device 003: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 001 Device 002: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
```

```

$ sudo tail -fn0 /var/log/messages
Apr 11 18:12:16 jay-desktop kernel: [ 4159.967947] usb 1-4: USB disconnect, address 5
Apr 11 18:12:20 jay-desktop kernel: [ 4161.819893] usb 1-4: new full speed USB device using ohci_hcd and address 6
Apr 11 18:12:20 jay-desktop kernel: [ 4161.927615] usb 1-4: configuration #1 chosen from 1 choice

```

when I run jscalibrator it does not find the "xpad" and when i try to calibrate it by manually typeing xpad into the top, it will not move. I uninstalled and reinstalled jscalibrator earlier as well.

---

### Post by Grumbel on 2009-04-11
> **thelastunavail said:**
> Ok im haveing the same problem and am useing a 3rd party xbox 360 controller called a "Pelican model #PL-3601" ..
From a quick look it seems your controller is simply not recognized by the kernel module or the module isn't loaded (check lsmod output).

If the module is loaded and the controller still not recognized, please post the full output of "lsusb -v" or just the section that refers your to controller if you know how to find it.

You could also try the userspace Xbox pad driver:

* [http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)

---

### Post by thelastunavail on 2009-04-11
here is the output for lsusb -v

```
Bus 002 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 004: ID 0e6f:0201  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0         8
  idVendor           0x0e6f 
  idProduct          0x0201 
  bcdDevice            1.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          153
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass     93 
      bInterfaceProtocol      1 
      iInterface              0 
      ** UNRECOGNIZED:  11 21 10 01 01 25 81 14 03 03 03 04 13 02 08 03 03
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               4
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               8
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass     93 
      bInterfaceProtocol      3 
      iInterface              0 
      ** UNRECOGNIZED:  1b 21 00 01 01 01 83 40 01 04 20 16 85 00 00 00 00 00 00 16 05 00 00 00 00 00 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               2
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               4
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval              64
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval              16
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass     93 
      bInterfaceProtocol      2 
      iInterface              0 
      ** UNRECOGNIZED:  09 21 00 01 01 22 86 07 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval              16
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    253 
      bInterfaceProtocol     19 
      iInterface              4 
      ** UNRECOGNIZED:  06 41 00 01 01 03
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 003: ID 04d9:0499 Holtek Semiconductor, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x04d9 Holtek Semiconductor, Inc.
  idProduct          0x0499 
  bcdDevice            2.90
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      52
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
cannot read device status, Operation not permitted (1)

Bus 001 Device 002: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x04b8 Seiko Epson Corp.
  idProduct          0x0005 Stylus Printer
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
cannot read device status, Operation not permitted (1)

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

``` 

I have tried a ton of different tut's but none seem to have worked..

I will check out that link now, thanks

---

### Post by Grumbel on 2009-04-11
> **thelastunavail said:**
> here is the output for lsusb -v
Just checked, your gamepad isn't supported by the driver. So a little patch is required. You now have three option, any single one of them should work:

1) For the [userspace driver xboxdrv](http://pingus.seul.org/~grumbel/xboxdrv/) I created the patch and commited it. So all you need to do is get the latest version from git and compile that (see README):

```

apt-get install \
     libboost1.35-dev \
     scons \
     libusb-dev \
     git-core \
     libx11-dev \
     x11proto-core-dev \
     python-dbus
git clone git://github.com/Grumbel/xboxdrv.git
cd xboxdrv.git
scons

```

2) If you already have compiled an earlier xboxdrv release yourself without the patch, just start the driver with:

```
xboxdrv --device-by-id 0e6f:0201 --type xbox360
```

Which should work too, even without the patch.

3) If you want to use the kernels native xpad driver instead of xboxdrv, you have to recompile the kernel and patch the xpad.c file, you can find it in:

/usr/src/linux-source-2.6.27/drivers/input/joystick/xpad.c

It contains a simple list of devices into which you need to enter 0e6f:0201, its not a hard fix, but requires that you are familiar with kernel compilation.

---

### Post by thelastunavail on 2009-04-12
> **Grumbel said:**
> Just checked, your gamepad isn't supported by the driver. So a little patch is required. You now have three option, any single one of them should work:

1) For the [userspace driver xboxdrv](http://pingus.seul.org/~grumbel/xboxdrv/) I created the patch and commited it. So all you need to do is get the latest version from git and compile that (see README):

```

apt-get install \
     libboost1.35-dev \
     scons \
     libusb-dev \
     git-core \
     libx11-dev \
     x11proto-core-dev \
     python-dbus
git clone git://github.com/Grumbel/xboxdrv.git
cd xboxdrv.git
scons

```




I got all of the required things downloaded for the scons compile except for libboost1.35-dev, when i do sudo apt-get install libboost1.35-dev, i receive this error

```
desktop:~/xboxdrv$ sudo apt-get install libboost1.35-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libboost1.35-dev

```

and i get an error trying to scons it without that package

any ideas? Im useing Ubuntu hardy heron.. thanks! :-)

---

### Post by Grumbel on 2009-04-12
> **thelastunavail said:**
> any ideas? Im useing Ubuntu hardy heron.. thanks! :-)
Try libboost-dev instead.

---

### Post by thelastunavail on 2009-04-12
That did it! Thanks to the infinite power :)

---

### Post by ninfomane on 2009-04-27
> **po0f said:**
> Hunkadoodledoo,

If you would be so kind, maybe try the attached sources instead.  I have no way of testing if they work or not, so don't be surprised if they don't.  ;)

It test twice to install this module. But at each compile process, I get these errors :
```

xpad360/xpad.c: In function ‘xpad_open’:
xpad360/xpad.c:340: error: ‘struct input_dev’ has no member named ‘private’
xpad360/xpad.c: In function ‘xpad_close’:
xpad360/xpad.c:351: error: ‘struct input_dev’ has no member named ‘private’
xpad360/xpad.c: In function ‘xpad_probe’:
xpad360/xpad.c:441: error: ‘struct input_dev’ has no member named ‘cdev’
xpad360/xpad.c:442: error: ‘struct input_dev’ has no member named ‘private’

```

---

### Post by Grumbel on 2009-04-27
> **ninfomane said:**
> It test twice to install this module. But at each compile process, I get these errors :
If you are using a recent enough kernel there shouldn't be a need to compile it manually, as the kernel comes with the module. If you are using an older kernel you must patch the xpad.[ch], use on that works with your kernel or use the xboxdrv userspace driver instead:

[http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)

---

### Post by ninfomane on 2009-04-27
Well... I find a solution to my issue. Here is some information about my system :
Ubuntu 8.10 linux-2.6.27-11 (upgrade from previsous Ubuntu version).
I installed linux-headers with apt-get. But there wasn't any xpad.c.
I downloaded kernel source from kernel.org (2.26.27.11) and looked for xpad.c
I use it instead of the archive one and it compile. I've not tried yet to use the guitar.

---

### Post by ninfomane on 2009-04-27
OK. I tested it. Unfortunately, It still do not work. I did :
```

$> sudo rmmod xpad
$> sudo modprobe xpad

```
I ran Joystick Calibrator. It recognize the guitar, but nothing happen when I push buttons.

---

### Post by wily202 on 2009-05-07
i used to play frets on fire

---

### Post by Bln on 2009-06-19
xbox-linux driver from xbox-linux.sourceforge.net won't work for now ('til I send my contribution). (un)Fortunately, you will always get this error now (according to [http://kerneltrap.org/mailarchive/git-commits-head/2008/2/7/770834](http://kerneltrap.org/mailarchive/git-commits-head/2008/2/7/770834)) instead of ```
input_dev->private
``` (which was dirty), you will now have to use ```
dev_get_drvdata(&input_struct)
``` and ```
dev_set_drvdata(&input_struct, &dev_struct)
``` (& means to get an adress of an element, but since references are used everywhere, you'll more probably get something like input_get_drvdata(dev) and input_set_drvdata(input_dev, xpad)). In addition, according to [http://kerneltrap.org/index.php?q=mailarchive/git-commits-head/2008/2/7/770914](http://kerneltrap.org/index.php?q=mailarchive/git-commits-head/2008/2/7/770914), ```
input_dev->cdev
``` is obsolete and should be removed. if you're unsure, you can comment lines where cdev appears. Doing this, if anything comes bad, you can uncomment them. ;)

I hope it'll help. See [my blog]("http://blog.binarykatana.com/post/xbox-gamepad-driver-for-linux/") for further information.

[I]Edit: it seems that this driver freezes at boot when modprobed. I will look into my logs in order to resolve this. 
Also, I saw that my Xbox controller was supported by ubuntu 9.04 live disk (which I used to rescue my "non-booting" linux), but it wasn't supported by my Ubuntu. If someone has a clue 'bout this, I'd be glad to have some informations (I have to go to work, I can't test anything for now).[/I]

---

### Post by Gek12345 on 2009-08-19
Hi I get this error, even when I edit the scons config file, and pont to anotheir drectory Im getting a syntax error on  LIBS=['boost_signals', 'usb', 'pthread'])


::::
scons: Reading SConscript files ...
Checking for C++ library X11... yes
Checking for C++ library usb... yes
Checking for C++ header file boost/thread/thread.hpp... yes
Checking for C++ library boost_thread-mt... yes
scons: done reading SConscript files.
scons: Building targets ...
o src/arg_parser.o -c -g -O2 -Wall -ansi -pedantic src/arg_parser.cpp
sh: o: command not found
o src/command_line_options.o -c -g -O2 -Wall -ansi -pedantic src/command_line_options.cpp
sh: o: command not found
o src/evdev_helper.o -c -g -O2 -Wall -ansi -pedantic src/evdev_helper.cpp
sh: o: command not found
o src/firestorm_dual_controller.o -c -g -O2 -Wall -ansi -pedantic src/firestorm_dual_controller.cpp
sh: o: command not found
o src/force_feedback_handler.o -c -g -O2 -Wall -ansi -pedantic src/force_feedback_handler.cpp
sh: o: command not found
o src/helper.o -c -g -O2 -Wall -ansi -pedantic src/helper.cpp
sh: o: command not found
o src/linux_uinput.o -c -g -O2 -Wall -ansi -pedantic src/linux_uinput.cpp
sh: o: command not found
o src/modifier.o -c -g -O2 -Wall -ansi -pedantic src/modifier.cpp
sh: o: command not found
o src/pretty_printer.o -c -g -O2 -Wall -ansi -pedantic src/pretty_printer.cpp
sh: o: command not found
o src/uinput.o -c -g -O2 -Wall -ansi -pedantic src/uinput.cpp
sh: o: command not found
o src/usb_read_thread.o -c -g -O2 -Wall -ansi -pedantic src/usb_read_thread.cpp
sh: o: command not found
o src/xbox360_controller.o -c -g -O2 -Wall -ansi -pedantic src/xbox360_controller.cpp
sh: o: command not found
o src/xbox360_wireless_controller.o -c -g -O2 -Wall -ansi -pedantic src/xbox360_wireless_controller.cpp
sh: o: command not found
o src/xbox_controller.o -c -g -O2 -Wall -ansi -pedantic src/xbox_controller.cpp
sh: o: command not found
o src/xboxdrv.o -c -g -O2 -Wall -ansi -pedantic src/xboxdrv.cpp
sh: o: command not found
o src/xboxmsg.o -c -g -O2 -Wall -ansi -pedantic src/xboxmsg.cpp
sh: o: command not found
o src/xpad_device.o -c -g -O2 -Wall -ansi -pedantic src/xpad_device.cpp
sh: o: command not found
o xboxdrv src/xboxdrv.o src/xboxmsg.o src/uinput.o src/arg_parser.o src/pretty_printer.o src/helper.o src/modifier.o src/command_line_options.o src/xbox_controller.o src/xpad_device.o src/xbox360_controller.o src/xbox360_wireless_controller.o src/firestorm_dual_controller.o src/evdev_helper.o src/linux_uinput.o src/usb_read_thread.o src/force_feedback_handler.o -lX11 -lX11 -lusb -lusb -lboost_thread-mt -lboost_thread-mt
sh: o: command not found
scons: done building targets.
>scons (9563) returned '116'

---

### Post by Gek12345 on 2009-08-19
I edit and I get this I delete the comma . off the ends and I get the syntax error on line 74 



>scons (12303)
scons: Reading SConscript files ...
Checking for C++ library X11... (cached) yes
Checking for C++ library usb... (cached) yes
Checking for C++ header file boost/thread/thread.hpp... (cached) yes
Checking for C++ library boost_thread-mt... (cached) yes
scons: done reading SConscript files.
scons: Building targets ...
scons: *** [arg_parser.o] Source `arg_parser.cpp' not found, needed by target `arg_parser.o'.
scons: building terminated because of errors.
>scons (12303) returned '0'

# -*- python -*-

env = Environment(CPPFLAGS=['-g', '-O2', '-Wall', '-ansi', '-pedantic'])
conf = Configure(env)

# X11 checks
if not conf.CheckLibWithHeader('X11', 'X11/Xlib.h', 'C++'):
    print 'libx11-dev must be installed!'
    Exit(1)
else:
    conf.env.Append(LIBS = 'X11')

# libusb Checks
if not conf.CheckLibWithHeader('usb', 'usb.h', 'C++'):
    print 'libusb must be installed!'
    Exit(1)
else:
    conf.env.Append(LIBS = 'usb')

# boost-thread checks
if not conf.CheckCXXHeader('boost/thread/thread.hpp'):
    print 'libboost-thread-dev must be installed!'
    Exit(1)

boost_thread = None
for lib in ['boost_thread-mt', 'boost_thread']:
    if conf.CheckLib(lib, language='C++'):
        boost_thread = lib
        break

if not boost_thread:
    print 'libboost-thread-dev must be installed!'
    Exit(1)
else:
    conf.env.Append(LIBS = boost_thread)

env = conf.Finish()

# env = Environment(CPPFLAGS=['-g', '-O2'], LIBS=['usb', 'X11'])
env.Program('xboxdrv', ['src/xboxdrv.cpp', 
                        '/root/joy/xboxdrv-linux-0.4.8/boxmsg.cpp',
                        '/root/joy/xboxdrv-linux-0.4.8/uinput.cpp',
                        '/root/joy/xboxdrv-linux-0.4.8/arg_parser.cpp',
                        '/root/joy/xboxdrv-linux-0.4.8/pretty_printer.cpp',
                        '/root/joy/xboxdrv-linux-0.4.8/helper.cpp',
                        '/root/joy/xboxdrv-linux-0.4.8/modifier.cpp',
                        '/root/joy/xboxdrv-linux-0.4.8/command_line_options.cpp',
                        '/root/joy/xboxdrv-linux-0.4.8/xbox_controller.cpp',
                        '/root/joy/xboxdrv-linux-0.4.8/xpad_device.cpp',
                        '/root/joy/xboxdrv-linux-0.4.8/xbox360_controller.cpp',
                        '/root/joy/xboxdrv-linux-0.4.8/xbox360_wireless_controller.cpp',
                        '/root/joy/xboxdrv-linux-0.4.8/firestorm_dual_controller.cpp',
                        '/root/joy/xboxdrv-linux-0.4.8/evdev_helper.cpp',
                        '/root/joy/xboxdrv-linux-0.4.8/linux_uinput.cpp',
                        '/root/joy/xboxdrv-linux-0.4.8/usb_read_thread.cpp',
                        '/root/joy/xboxdrv-linux-0.4.8/force_feedback_handler.cpp'                        
                        ])

if False:
    env.Program('inputdrv',
                ['/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv.cpp',
                 '/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv/xbox360_driver.cpp',
                 '/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv/evdev_driver.cpp',
                 '/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv/xbox360_usb_thread.cpp',
                 '/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv/control.cpp',
                 '/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv/abs_to_rel.cpp',
                 '/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv/abs_to_btn.cpp',
                 '/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv/btn_to_abs.cpp',
                 '/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv/autofire_button.cpp',
                 '/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv/uinput_driver.cpp',
                 '/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv/join_axis.cpp',
                 '/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv/throttle.cpp',
                 '/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv/toggle_button.cpp'],
                LIBS=['boost_signals', 'usb', 'pthread'])

# EOF #

::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::
>scons (12323)
scons: Reading SConscript files ...
  File "/root/joy/xboxdrv-linux-0.4.8/SConstruct", line 74

    LIBS=['boost_signals', 'usb', 'pthread'])

       ^

SyntaxError: invalid syntax

>scons (12323) returned '0'
>scons (12324)
scons: Reading SConscript files ...
  File "/root/joy/xboxdrv-linux-0.4.8/SConstruct", line 74

    LIBS=['boost_signals' 'usb' 'pthread'])

       ^

SyntaxError: invalid syntax

>scons (12324) returned '107'




I delete the comma ,,,, off the end and I get syntax erro 

# -*- python -*-

env = Environment(CPPFLAGS=['-g', '-O2', '-Wall', '-ansi', '-pedantic'])
conf = Configure(env)

# X11 checks
if not conf.CheckLibWithHeader('X11', 'X11/Xlib.h', 'C++'):
    print 'libx11-dev must be installed!'
    Exit(1)
else:
    conf.env.Append(LIBS = 'X11')

# libusb Checks
if not conf.CheckLibWithHeader('usb', 'usb.h', 'C++'):
    print 'libusb must be installed!'
    Exit(1)
else:
    conf.env.Append(LIBS = 'usb')

# boost-thread checks
if not conf.CheckCXXHeader('boost/thread/thread.hpp'):
    print 'libboost-thread-dev must be installed!'
    Exit(1)

boost_thread = None
for lib in ['boost_thread-mt', 'boost_thread']:
    if conf.CheckLib(lib, language='C++'):
        boost_thread = lib
        break

if not boost_thread:
    print 'libboost-thread-dev must be installed!'
    Exit(1)
else:
    conf.env.Append(LIBS = boost_thread)

env = conf.Finish()

# env = Environment(CPPFLAGS=['-g', '-O2'], LIBS=['usb', 'X11'])
env.Program('xboxdrv', ['src/xboxdrv.cpp', 
                        '/root/joy/xboxdrv-linux-0.4.8/boxmsg.cpp'
                        '/root/joy/xboxdrv-linux-0.4.8/uinput.cpp'
                        '/root/joy/xboxdrv-linux-0.4.8/arg_parser.cpp'
                        '/root/joy/xboxdrv-linux-0.4.8/pretty_printer.cpp'
                        '/root/joy/xboxdrv-linux-0.4.8/helper.cpp'
                        '/root/joy/xboxdrv-linux-0.4.8/modifier.cpp'
                        '/root/joy/xboxdrv-linux-0.4.8/command_line_options.cpp'
                        '/root/joy/xboxdrv-linux-0.4.8/xbox_controller.cpp'
                        '/root/joy/xboxdrv-linux-0.4.8/xpad_device.cpp'
                        '/root/joy/xboxdrv-linux-0.4.8/xbox360_controller.cpp'
                        '/root/joy/xboxdrv-linux-0.4.8/xbox360_wireless_controller.cpp'
                        '/root/joy/xboxdrv-linux-0.4.8/firestorm_dual_controller.cpp'
                        '/root/joy/xboxdrv-linux-0.4.8/evdev_helper.cpp'
                        '/root/joy/xboxdrv-linux-0.4.8/linux_uinput.cpp'
                        '/root/joy/xboxdrv-linux-0.4.8/usb_read_thread.cpp'
                        '/root/joy/xboxdrv-linux-0.4.8/force_feedback_handler.cpp'                        
                        ])

if False:
    env.Program('inputdrv',
                ['/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv.cpp'
                 '/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv/xbox360_driver.cpp'
                 '/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv/evdev_driver.cpp'
                 '/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv/xbox360_usb_thread.cpp'
                 '/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv/control.cpp'
                 '/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv/abs_to_rel.cpp'
                 '/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv/abs_to_btn.cpp'
                 '/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv/btn_to_abs.cpp'
                 '/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv/autofire_button.cpp'
                 '/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv/uinput_driver.cpp'
                 '/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv/join_axis.cpp'
                 '/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv/throttle.cpp'
                 '/root/joy/xboxdrv-linux-0.4.8/src/inputdrv/inputdrv/toggle_button.cpp']
                LIBS=['boost_signals', 'usb', 'pthread'])

# EOF #

---

### Post by insanecrazy4 on 2009-08-19
can someone help me with this problem with makefile

```
devon@devon-laptop:~/xpad$ make
make modules -C /lib/modules/2.6.28-15-generic/build SUBDIRS=/home/devon/xpad
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/devon/xpad/xpad.o
/home/devon/xpad/xpad.c: In function ‘xpad_open’:
/home/devon/xpad/xpad.c:337: error: ‘struct input_dev’ has no member named ‘private’
/home/devon/xpad/xpad.c: In function ‘xpad_close’:
/home/devon/xpad/xpad.c:348: error: ‘struct input_dev’ has no member named ‘private’
/home/devon/xpad/xpad.c: In function ‘xpad_probe’:
/home/devon/xpad/xpad.c:438: error: ‘struct input_dev’ has no member named ‘cdev’
/home/devon/xpad/xpad.c:439: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/devon/xpad/xpad.o] Error 1
make[1]: *** [_module_/home/devon/xpad] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [all] Error 2
devon@devon-laptop:~/xpad$ 

```

---

### Post by Grumbel on 2009-08-20
> **Gek12345 said:**
> Hi I get this error
I think those obscure errors are the result of not having a g++ installed.

Also reextract the whole thing from the tarball again as your modification to the SConstruct file seem to have broken it.

---

### Post by Grumbel on 2009-08-20
> **insanecrazy4 said:**
> can someone help me with this problem with makefile
Thats not a problem with the makefile but with the source of the module. Just use the xpad module supplied by your kernel instead of trying to compile the module separately.

---

### Post by SerraAvenger on 2009-11-06
oookay.

I was having the same problems like BigSilly (?) on the first few pages, with the same gamepad. 

xpad is blacklisted, endpoints had been tested hardcoded as both 1 and 2, but it still wouldn't allow the driver to claim that interface.
So I did a little bit of treachery,  stealing the interface from the kernel (not my code, stolen from here [http://www.c-plusplus.de/forum/viewtopic-var-t-is-243643.html](http://www.c-plusplus.de/forum/viewtopic-var-t-is-243643.html))
```

void forceClaimInterface( usb_dev_handle *targetDevice, int interfaceNumber ){
    int nRet = -1;
    for( int i = 0; i < nRetries; i++)
    {
        if(1)
        {
            nRet = usb_claim_interface( targetDevice, interfaceNumber);
            if( nRet < 0)
            {
                std::cerr << "openUSBDevice: try to claim interface again..." << std::endl;
                if( usb_detach_kernel_driver_np( targetDevice, interfaceNumber ) < 0)
                {
                    printf( "failed to detach kernel driver from USB device...");
                    return;
                }
            }
            else
            {
                std::cerr << "openUSBDevice: claimed interface successfully" << std::endl;
                break;
            }
        }
    }
}
```and then it told me this:
```
openUSBDevice: try to claim interface again...
openUSBDevice: claimed interface successfully

Starting with uinput... done

Your Xbox/Xbox360 controller should now be available as:
  /dev/input/js0
  /dev/input/event5

Press Ctrl-c to quit

```Well. When using jstest, js0 and event5 are removed again, and jstest tells me those files do not exist (they are removed when using jstest, not before).

When disconnecting and reconnecting the gamepad to the usb-port, a new js0 is created.
Both jscalibrator and jstest  then think to know my device, but don't react to any buttons/pads whatsoever.

any idea on what to do?
EDIT: Wrong thread. Actually should have landed in [here]("http://ubuntuforums.org/showthread.php?t=825464").

---

### Post by Grumbel on 2009-11-06
> Well. When using jstest, js0 and event5 are removed again,
xboxdrv only guesses the names of js0 and event5, it does not actually know if the devices where created or what their exact names are, so its more likely that xboxdrv is wrong neither ever got created in the first place instead of them disappearing later on.

> When disconnecting and reconnecting the gamepad to the usb-port, a new js0 is created.
That (along with the claiming issue) indicates that there is something else grabbing control of the pads instead of xboxdrv and that might be causing trouble. So I would try to find what it is. Plug in the joystick and see what dependencies 'lsmod' list for the joydev module, a look at 'dmesg' might also help.

One issue might be that xpad simply isn't blacklisted. On the latest Ubuntu the naming seems to have changed and files in modprobe.d now require a .conf ending. So try blacklisting xpad in /etc/modprobe.d/blacklist.conf instead of /etc/modprobe.d/blacklist. Also verify with 'lsmod' that its really gone and doesn't come back when you plug in the pad.

If all that doesn't help: What controller are you using (Xbox1, Xbox360, first party, third party, etc.)?

---

### Post by frenchn00b on 2009-11-14
Is there a tar.gz, to do :

```
./configure
make 
make install
```

play with insmod and rmmod, and see the gamepad working on a 2.6.18 kernel?


alternatively to run to see it working:
> rmmod XX
modprobe XXXX
insmod XX.ko


---

### Post by Grumbel on 2009-11-14
> **frenchn00b said:**
> Is there a tar.gz, to do
Thats what xboxdrv is for, see README for details:

[http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)

You could also just try "modprobe xpad", however in 2.6.18 the driver might still be broken.

---

### Post by frenchn00b on 2009-11-14
> **po0f said:**
> Uranium235,

Sure thing:

```
$ tar xvzf /path/to/xpad360.tar.gz
$ cd xpad360
$ make
$ sudo make install
```

If you want to back up the original xpad driver (run **before** `sudo make install` above):

```
$ cp /lib/modules/`uname -r`/kernel/drivers/usb/input/xpad.ko xpad.ko.orig
```

before crashing the pc changing the filesystem, you can test it with :

```
make 
rmmod the running pad driver (which one is it?)
insmod xpad.ko
```

---

### Post by frenchn00b on 2009-11-14
> **Grumbel said:**
> Thats what xboxdrv is for, see README for details:

[http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)

You could also just try "modprobe xpad", however in 2.6.18 the driver might still be broken.

thanks Grumbel! I am testing / trying now ...

---

### Post by frenchn00b on 2009-11-14
xbox 360 you gave is too difficult to be installed :( 

here a xpad.ko working for the gamepad xbox
but i cannot get it for 2.6.18 working

insmod xpad.ko 
 
dmesg said on a 2.6.30 kernel:  
```
387.375566] usbcore: registered new interface driver xpad
[ 1387.375586] xpad: X-Box pad driver
[ 1654.328173] usb 2-1: USB disconnect, address 4
[ 1654.329465] xpad: xpad_irq_in - usb_submit_urb failed with result -19
[ 1654.329485] xpad: xpad_irq_in - usb_submit_urb failed with result -19
[ 1654.329500] xpad: xpad_irq_in - usb_submit_urb failed with result -19
[ 1656.056113] usb 2-1: new full speed USB device using uhci_hcd and address 5
[ 1656.291485] usb 2-1: New USB device found, idVendor=045e, idProduct=0719
[ 1656.291502] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1656.291515] usb 2-1: Product: Xbox 360 Wireless Receiver for Windows
[ 1656.291526] usb 2-1: Manufacturer: ©Microsoft
[ 1656.291535] usb 2-1: SerialNumber: FDE5EEB0
[ 1656.291828] usb 2-1: configuration #1 chosen from 1 choice
[ 1656.294134] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input26
[ 1656.295983] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.2/input/input27
[ 1656.298148] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.4/input/input28
[ 1656.300298] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.6/input/input29
[ 1910.264241] usb 2-1: USB disconnect, address 5
[ 1910.266466] xpad: xpad_irq_in - usb_submit_urb failed with result -19
[ 2238.680111] usb 2-2: new full speed USB device using uhci_hcd and address 6
[ 2238.971205] usb 2-2: New USB device found, idVendor=045e, idProduct=0719
[ 2238.971221] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2238.971234] usb 2-2: Product: Xbox 360 Wireless Receiver for Windows
[ 2238.971245] usb 2-2: Manufacturer: ©Microsoft
[ 2238.971254] usb 2-2: SerialNumber: FDE5EEB0
[ 2238.971550] usb 2-2: configuration #1 chosen from 1 choice
[ 2238.974674] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input30
[ 2238.976520] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.2/input/input31
[ 2238.978500] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.4/input/input32
[ 2238.980449] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.6/input/input33
```


 the given xpad.tar.gz isnt working :( 

**not working :( still for the 2.6.18 kernel :( **

---

### Post by frenchn00b on 2009-11-14
> **insanecrazy4 said:**
> can someone help me with this problem with makefile

```
devon@devon-laptop:~/xpad$ make
make modules -C /lib/modules/2.6.28-15-generic/build SUBDIRS=/home/devon/xpad
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/devon/xpad/xpad.o
/home/devon/xpad/xpad.c: In function ‘xpad_open’:
/home/devon/xpad/xpad.c:337: error: ‘struct input_dev’ has no member named ‘private’
/home/devon/xpad/xpad.c: In function ‘xpad_close’:
/home/devon/xpad/xpad.c:348: error: ‘struct input_dev’ has no member named ‘private’
/home/devon/xpad/xpad.c: In function ‘xpad_probe’:
/home/devon/xpad/xpad.c:438: error: ‘struct input_dev’ has no member named ‘cdev’
/home/devon/xpad/xpad.c:439: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/devon/xpad/xpad.o] Error 1
make[1]: *** [_module_/home/devon/xpad] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [all] Error 2
devon@devon-laptop:~/xpad$ 

```

you need to be capable to compile. ./configure ; make ; make install will not be a secret for you.
Try this code once and you'll be able to compile with QT, GCC, ... :

```
#!/bin/sh
echo " ==========   "
echo "QTDIR is :  $QTDIR"
echo "---Listing /usr/share/qt-----------"
ls /usr/share/qt* 
ls /usr/bin/gcc* -lha



echo "--------------"
printf "Type which QT3 or QT4 to use, but plz type qt3: "
read qtversion
export QTDIR="/usr/share/$qtversion"
echo "Configuring to: /usr/share/$qtversion"
echo " "
echo " "
echo " "
echo "---Listing /usr/bin/gcc-----------"
ls /usr/bin/gcc* 
echo "--------------"
printf "Type which 3.4 or 4.3 to use, but plz type 4.3: "
read ccversion
 
export CC="/usr/bin/gcc-$ccversion" 
rm /usr/bin/gcc
ln -s /usr/bin/gcc-$ccversion /usr/bin/gcc
ls -la /usr/bin/gcc

echo "--------------"
echo "--------------"
echo " Installing ... "

apt-get -f -y --allow-unauthenticated      install 
apt-get -f -y --allow-unauthenticated      install


apt-get -f -y --allow-unauthenticated      install gcc 
apt-get -f -y --allow-unauthenticated      install build-essential imlib11-dev esound-clients
#rm /usr/bin/gcc
#ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
apt-get -f -y --allow-unauthenticated      install linux-headers-$(uname -r)
apt-get -f -y --allow-unauthenticated      install build-essential 
apt-get -f -y --allow-unauthenticated      install 
apt-get -f -y --allow-unauthenticated      install cvs
apt-get -f -y --allow-unauthenticated      install 
apt-get -f -y --allow-unauthenticated      install bison
apt-get -f -y --allow-unauthenticated      install flex
apt-get -f -y --allow-unauthenticated      install 
## voor vmware
apt-get -f -y --allow-unauthenticated      install make
apt-get -f -y --allow-unauthenticated      install build-essential
apt-get -f -y --allow-unauthenticated      install gcc 
apt-get -f -y --allow-unauthenticated      install build-essential 
apt-get -f -y --allow-unauthenticated      install zenity

apt-get -f -y --allow-unauthenticated      install g++

cat /proc/version

apt-get -f -y --allow-unauthenticated      install
apt-get -f -y --allow-unauthenticated      install
######## installing qt3
apt-get -f -y --allow-unauthenticated      install qt3-dev-tools
apt-get -f -y --allow-unauthenticated      install qt3-apps-dev
apt-get -f -y --allow-unauthenticated      install libqt3-headers
apt-get -f -y --allow-unauthenticated      install qca-dev
apt-get -f -y --allow-unauthenticated      install libqt3c102-mt 
```

---

### Post by frenchn00b on 2010-01-03
hey guys, 

**[COLOR="Red"]this driver is not working for 2 players.[/COLOR]**
so sad

Look here the output of zsnes and dgen:

```
 
**mednafen (working for 2players)**
Using Microsoft Xbox 360 Wireless Controller (PC) (#0) as pad1 and Microsoft Xbox 360 Wireless Controller (PC) (#1) as pad2 
42 frames per second (optimal 60)
Starting Mednafen 0.8.5
 Loading settings from "/home/frenchn00b/.mednafen/mednafen.cfg"...
 Compiled against SDL 1.2.11, running with SDL 1.2.12


**ZSNES (non working for 2players, to set the input of the player #2 ie. buttons)**
non working :(

**dgen (non working, pad #2 not seen)**
 Initializing joysticks...
  Joystick 0 - Microsoft Xbox 360 Wireless Controller (PC) - Unique ID: e462ea11338354e1
  Joystick 1 - Microsoft Xbox 360 Wireless Controller (PC) - Unique ID: e462ea11338354e2
  Joystick 2 - Microsoft Xbox 360 Wireless Controller (PC) - Unique ID: e462ea11338354e2
  Joystick 3 - Microsoft Xbox 360 Wireless Controller (PC) - Unique ID: e462ea11338354e2
  Joystick 4 - Logitech Logitech Dual Action - Unique ID: ce96ea6b9d7ca56a
 Loading rom-test.bin...


**SNES-9x (non working, pad #2 not seen)**
Unrecognized file format.  Sorry.
Controller Port 1: Pad 1
Controller Port 2: <none>
Rate: 22050, Buffer size: 2048, 16-bit: yes, Stereo: yes, Encoded: no
No ROM file header found.
"B??.??r&N?" [bad checksum] LoROM, Corrupt, Type: ROM+ST-018, Mode: 40, TV: PAL, S-RAM: 4KB, ROMId:  Company: FF CRC32: 9BDC230C
Unrecognized input device name 'K00:grave'
Could not map 'Superscope ToggleTurbo' to 'K00:grave'
Unrecognized input device name 'K00:grave'
Could not map 'Superscope ToggleTurbo' to 'K00:grave'



  
```

---

### Post by Grumbel on 2010-01-03
> **frenchn00b said:**
> this driver is not working for 2 players.
If we are talking about xboxdrv, you have to start the driver twice, once for each controller and give the proper "--wid" on startup. This hasn't been tested much, but should work and if not its not hard to fix.

---

### Post by frenchn00b on 2010-01-03
> **Grumbel said:**
> If we are talking about xboxdrv, you have to start the driver twice, once for each controller and give the proper "--wid" on startup. This hasn't been tested much, but should work and if not its not hard to fix.


it is written this. It is a bit complicated. Is there a script that does the installation for us? 
here the src from the xbosdrv site:  [url]("http://pingus.seul.org/~grumbel/xboxdrv/xboxdrv-linux-0.4.9.tar.bz2")
```
  
Plug in your Xbox360 gamepad and then unload the xpad driver via:

 % rmmod xpad

If you want to permanently unload it add the following line to
/etc/modprobe.d/blacklist:

blacklist xpad

Next you have to load the uinput kernel module which allows userspace
programms to create input devices and the joydev module which gives
you the /dev/input/jsX device:

 % modprobe uinput
 % modprobe joydev

You also have to make sure that you have access rights to
/dev/input/uinput, either add yourself to the appropriate group,
adjust the permissions or run xboxdrv as root.

Once ensured that xpad is out of the way and everything is in place
start the userspace driver with:

 % ./xboxdrv

Or in case you don't have the neccesary rights (being in group root
should often be enough) start the driver as root via:

 % sudo ./xboxdrv

This will create /dev/input/js0 and allow you to access the gamepad
from any game. To exit the driver press Ctrl-c. 
If you have multiple wired controllers you need to start multiple instances
of the xboxdrv driver and append the -i argument like this:

 % ./xboxdrv -i 1

If you have multiple wireless controller you need to start multiple
instances of the xboxdrv driver and append the --wid argument like
this:

 % ./xboxdrv --wid 1

You have to sync the wireless controller as usual.

This will then use the second detected controller, see to see which id
your controller has:

 % ./xboxdrv --list-controller

When everything works as expected it is recomment that you run xboxdrv
with the silent option:

 % ./xboxdrv --silent
:


```

I found this example
> sudo /home/kdb424/xboxdrv-linux-0.4.9/xboxdrv --device-by-id 0x1bad:0xf016 --type xbox360 --silent


scons 
gives this error:

>   
scons: Reading SConscript files ...
Checking for C++ library X11... yes
Checking for C++ library usb... yes
Checking for C++ header file boost/thread/thread.hpp... yes
Checking for C++ library boost_thread-mt... yes
scons: done reading SConscript files.
scons: Building targets ...
g++ -o src/arg_parser.o -c -g -O2 -Wall -ansi -pedantic src/arg_parser.cpp
g++ -o src/command_line_options.o -c -g -O2 -Wall -ansi -pedantic src/command_line_options.cpp
g++ -o src/evdev_helper.o -c -g -O2 -Wall -ansi -pedantic src/evdev_helper.cpp
g++ -o src/firestorm_dual_controller.o -c -g -O2 -Wall -ansi -pedantic src/firestorm_dual_controller.cpp
g++ -o src/force_feedback_handler.o -c -g -O2 -Wall -ansi -pedantic src/force_feedback_handler.cpp
g++ -o src/helper.o -c -g -O2 -Wall -ansi -pedantic src/helper.cpp
g++ -o src/linux_uinput.o -c -g -O2 -Wall -ansi -pedantic src/linux_uinput.cpp
g++ -o src/modifier.o -c -g -O2 -Wall -ansi -pedantic src/modifier.cpp
g++ -o src/pretty_printer.o -c -g -O2 -Wall -ansi -pedantic src/pretty_printer.cpp
g++ -o src/saitek_p2500_controller.o -c -g -O2 -Wall -ansi -pedantic src/saitek_p2500_controller.cpp
g++ -o src/uinput.o -c -g -O2 -Wall -ansi -pedantic src/uinput.cpp
g++ -o src/usb_read_thread.o -c -g -O2 -Wall -ansi -pedantic src/usb_read_thread.cpp
src/usb_read_thread.cpp: In member function 'int USBReadThread::read(uint8_t*, int, int)':
src/usb_read_thread.cpp:61: error: 'boost::posix_time' has not been declared
scons: *** [src/usb_read_thread.o] Error 1
scons: building terminated because of errors.




I ran this
>   
apt-get update



apt-get install -f -y  install   beep
apt-get install -f -y 
apt-get install -f -y    install  g++ 

apt-get install -f -y      install     libboost1.37-dev 
     apt-get install -f -y    install  libboost-thread1.37-dev 
     apt-get install -f -y   install    scons 
     apt-get install -f -y    install  libusb-dev 
     apt-get install -f -y   install   git-core 
     apt-get install -f -y   install   libx11-dev 
     apt-get install -f -y   install    x11proto-core-dev  
     apt-get install -f -y   install   python-dbus

apt-get install  -f -y  install   libboost-thread-dev  
apt-get install -f -y install  libboost1.35-dev  
apt-get install -f -y install  libboost1.35-dev  ; beep

apt-get install  -f -y install   libboost-thread-dev


apt-get install  -f -y install   scons
 
scons





 and got




>  scons: *** No SConstruct file found.
File "/usr/lib/scons/SCons/Script/Main.py", line 817, in _main
scons: Reading SConscript files ...
Checking for C++ library X11... (cached) yes
Checking for C++ library usb... (cached) yes
Checking for C++ header file boost/thread/thread.hpp... (cached) yes
Checking for C++ library boost_thread-mt... (cached) yes
scons: done reading SConscript files.
scons: Building targets ...
g++ -o src/usb_read_thread.o -c -g -O2 -Wall -ansi -pedantic src/usb_read_thread.cpp
g++ -o src/xbox360_controller.o -c -g -O2 -Wall -ansi -pedantic src/xbox360_controller.cpp
g++ -o src/xbox360_wireless_controller.o -c -g -O2 -Wall -ansi -pedantic src/xbox360_wireless_controller.cpp
g++ -o src/xbox_controller.o -c -g -O2 -Wall -ansi -pedantic src/xbox_controller.cpp
g++ -o src/xboxdrv.o -c -g -O2 -Wall -ansi -pedantic src/xboxdrv.cpp
g++ -o src/xboxmsg.o -c -g -O2 -Wall -ansi -pedantic src/xboxmsg.cpp
g++ -o src/xpad_device.o -c -g -O2 -Wall -ansi -pedantic src/xpad_device.cpp
g++ -o xboxdrv src/xboxdrv.o src/xboxmsg.o src/uinput.o src/arg_parser.o src/pretty_printer.o src/helper.o src/modifier.o src/command_line_options.o s
rc/xbox_controller.o src/xpad_device.o src/xbox360_controller.o src/xbox360_wireless_controller.o src/firestorm_dual_controller.o src/saitek_p2500_con
troller.o src/evdev_helper.o src/linux_uinput.o src/usb_read_thread.o src/force_feedback_handler.o -lX11 -lusb -lboost_thread-mt
src/xboxdrv.o: In function `Xboxdrv::run_main(CommandLineOptions const&)':
/home/xboxdrv-linux-0.4.9/src/xboxdrv.cpp:535: undefined reference to `uInput::set_ff_callback(boost::f
unction<void ()(unsigned char, unsigned char), std::allocator<void> > const&)'
collect2: ld returned 1 exit status
scons: *** [xboxdrv] Error 1
scons: building terminated because of errors.
 


>  ./xboxdrv 
./xboxdrv: error while loading shared libraries: libboost_thread-mt.so.1.35.0: cannot open shared object file: No such file or directory

---

### Post by frenchn00b on 2010-01-03
```
# apt-get install libboost1.35-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libboost1.35-dev: Depends: libicu36 but it is not installable
                    Recommends: libboost-iostreams1.35-dev but it is not going to be installed
                    Recommends: libboost-regex1.35-dev but it is not going to be installed
E: Broken packages
```


whatever is tried, I get always this error :(
> 

xboxdrv-linux-0.4.9# scons
scons: Reading SConscript files ...
Checking for C++ library X11... yes
Checking for C++ library usb... yes
Checking for C++ header file boost/thread/thread.hpp... yes
Checking for C++ library boost_thread-mt... yes
scons: done reading SConscript files.
scons: Building targets ...
g++ -o src/arg_parser.o -c -g -O2 -Wall -ansi -pedantic src/arg_parser.cpp
g++ -o src/command_line_options.o -c -g -O2 -Wall -ansi -pedantic src/command_line_options.cpp
g++ -o src/evdev_helper.o -c -g -O2 -Wall -ansi -pedantic src/evdev_helper.cpp
g++ -o src/firestorm_dual_controller.o -c -g -O2 -Wall -ansi -pedantic src/firestorm_dual_controller.cpp
g++ -o src/force_feedback_handler.o -c -g -O2 -Wall -ansi -pedantic src/force_feedback_handler.cpp
g++ -o src/helper.o -c -g -O2 -Wall -ansi -pedantic src/helper.cpp
g++ -o src/linux_uinput.o -c -g -O2 -Wall -ansi -pedantic src/linux_uinput.cpp
g++ -o src/modifier.o -c -g -O2 -Wall -ansi -pedantic src/modifier.cpp
g++ -o src/pretty_printer.o -c -g -O2 -Wall -ansi -pedantic src/pretty_printer.cpp
g++ -o src/saitek_p2500_controller.o -c -g -O2 -Wall -ansi -pedantic src/saitek_p2500_controller.cpp
g++ -o src/uinput.o -c -g -O2 -Wall -ansi -pedantic src/uinput.cpp
g++ -o src/usb_read_thread.o -c -g -O2 -Wall -ansi -pedantic src/usb_read_thread.cpp
src/usb_read_thread.cpp: In member function 'int USBReadThread::read(uint8_t*, int, int)':
src/usb_read_thread.cpp:70: error: 'memcpy' was not declared in this scope
scons: *** [src/usb_read_thread.o] Error 1
scons: building terminated because of errors.


---

### Post by Jtheletter on 2010-01-19
Hello all, I am currently using an xpad.ko module v0.1.7 compiled for kernel 2.6.20.21 and I have written code to successfully read controller values for a standard WIRED Microsoft XBox360 controller (official MS hardware, recently purchased).

Everything works fine unless the controller is connected to the USB port prior to booting, this causes the system to hang when it reaches the "insmod /<directory_path>/xpad.ko" in my init. If I unplug the controller the system will recover and boot properly and the controller will work fine when it is plugged in again.

I am also loading the following modules during init:

insmod /lib/modules/2.6.20.21/kernel/drivers/usb/serial/usbserial.ko
insmod /lib/modules/2.6.20.21/kernel/drivers/usb/serial/pl2303.ko
insmod /lib/modules/2.6.20.21/kernel/drivers/usb/serial/ftdi_sio.ko
insmod /lib/modules/2.6.20.21/kernel/drivers/usb/input/xpad.ko

Ordering the xpad.ko before or after these other calls has no effect, it will hang on the xpad call. 

I see that others have raised this issue in this thread before but I have read all 22 pages and I could not find a post that resolved this problem specifically. Simply unplugging the controller before booting is not an acceptable workaround for my needs, sorry. 
Has anyone been able to fix this?

Thank you for your help,
S.

---

### Post by frenchn00b on 2010-01-19
> **Jtheletter said:**
> Hello all, I am currently using an xpad.ko module v0.1.7 compiled for kernel 2.6.20.21 and I have written code to successfully read controller values for a standard WIRED Microsoft XBox360 controller (official MS hardware, recently purchased).

Everything works fine unless the controller is connected to the USB port prior to booting, this causes the system to hang when it reaches the "insmod /<directory_path>/xpad.ko" in my init. If I unplug the controller the system will recover and boot properly and the controller will work fine when it is plugged in again.

I am also loading the following modules during init:

insmod /lib/modules/2.6.20.21/kernel/drivers/usb/serial/usbserial.ko
insmod /lib/modules/2.6.20.21/kernel/drivers/usb/serial/pl2303.ko
insmod /lib/modules/2.6.20.21/kernel/drivers/usb/serial/ftdi_sio.ko
insmod /lib/modules/2.6.20.21/kernel/drivers/usb/input/xpad.ko

Ordering the xpad.ko before or after these other calls has no effect, it will hang on the xpad call. 

I see that others have raised this issue in this thread before but I have read alland I could not find a post that resolved this problem specifically. Simply unplugging the controller before booting is not an acceptable workaround for my needs, sorry. 
Has anyone been able to fix this?

Thank you for your help,
S.

It seems that the drivers or the developments of xpad 360 driver has low activity, although the website still lives. Not much replies & results indeed as you wrote :  > 22 pages 

---

### Post by Grumbel on 2010-01-20
> **Jtheletter said:**
> Hello all, I am currently using an xpad.ko module v0.1.7 compiled for kernel 2.6.20.21 and I have written code to successfully read controller values for a standard WIRED Microsoft XBox360 controller (official MS hardware, recently purchased).
Have you made sure that the old xpad driver that came with the kernel is out of the way? If not it will be automatically loaded. So either delete the old xpad.ko, overwrite it with the new driver or blacklist the module so that it is not automatically loaded by creating a file /etc/modprobe.d/xpad.conf with a line:

blacklist xpad

---

### Post by frenchn00b on 2010-01-20
> **Grumbel said:**
> Have you made sure that the old xpad driver that came with the kernel is out of the way? If not it will be automatically loaded. So either delete the old xpad.ko, overwrite it with the new driver or blacklist the module so that it is not automatically loaded by creating a file /etc/modprobe.d/xpad.conf with a line:

blacklist xpad

if he does rmmod xpad when trying after compilation, it shall work. 

dgen -j   is interesting. It gives 4 xbox gamepad instead of one. It is an interestign debugger.

---

### Post by Jtheletter on 2010-01-20
> **Grumbel said:**
> Have you made sure that the old xpad driver that came with the kernel is out of the way? If not it will be automatically loaded. So either delete the old xpad.ko, overwrite it with the new driver or blacklist the module so that it is not automatically loaded by creating a file /etc/modprobe.d/xpad.conf with a line: blacklist xpad

First, thank you to both frenchn00b and Grumbel for your quick responses. Unfortunately the kernel I am working with is a custom build of 2.6.20.21 for a single board computer that originally had less than 40MB of HDD space, so many of the kernel tools and unused modules were removed by the original creator to save space. I am trying to avoid rebuilding a new kernel for this SBC because that will cause other problems for me down the line. Thankfully it has been upgraded to a 2GB HDD so I have some more room to work, but the preferred upgrade process is to add modules after init rather than build a new kernel.

There is no preexisting xpad.ko for this custom kernel, so there is no conflict with two xpad.ko modules being loaded. There seems to be a problem with xpad.ko partially loading but not being able to finish/exit when the 360 controller is already plugged in.

Here is a snippet of dmesg that shows what happens if I boot with the 360 controller attached but do not load xpad at boot, then later manually modprobe it. Dmesg output is in **bold**, my comments are in *//italic*.


[B]usb 1-2: new full speed USB device using ohci_hcd and address 2
usb 1-2: configuration #1 chosen from 1 choice[/B]
*//the xbox controller has been detected and connects as a generic device, next I call 'modprobe xpad'*
[B]input: Microsoft Xbox 360 Controller as /class/input/input0
input: Microsoft Xbox 360 Controller as /class/input/input1[/B]
*//xpad loads enough to recognize the controller as the 360, this is where loading xpad will hang until I disconnect the controller. I should note I can run jstest and my own code to read the controller even though modprobe is hanging*
**usb 1-2: USB disconnect, address 2**
*//this disconnect is from me manually unplugging the controller*
[B]usbcore: registered new interface driver xpad
drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.7[/B]
*//after the controller is unplugged  the modprobe finishes and exits, if controller is reconnected it is recognized and works*

I have found that if I run "insmod /<dir_path>/xpad.ko &" in my rc0.d I can use the controller but the insmod process will stick around in the background. I don't see any memory leak or processor hogging for this process if I check with "top" but it seems like a very bad idea to let insmod hang in an open process.

Anyway, this sequence of events leads me to believe that xpad.ko is 99% loaded but there is an error in xpad.c and/or usbcore such that it is waiting on some event that cannot occur while the controller is connected. Thoughts on this?  

My other planned approach was to disable ohci_hcd during boot using a blacklist, then insmod xpad, then re-enable ohci afterwards. The problem is that my custom kernel is missing all of the sbin programs needed to build an initramfs image to utilize the blacklist at boot. grrr. Any other ideas on how to disable USB until xpad is loaded?

Thanks for any help you can give,
J.S.

---

### Post by Realnot on 2010-02-18
Hi, I found problems installing the headset Microsoft LifeChat ZX-6000 on Ubuntu 9.10. I followed the manual step by step, but nothing to do ... sorry for my bad English:

[B]Error:
[/B]
[EMAIL="mauro@workstation:%7E/.xpad"]mauro@workstation:~/.xpad[/EMAIL]360$ cd /home/mauro/.xpad360
[EMAIL="mauro@workstation:%7E/.xpad"]mauro@workstation:~/.xpad[/EMAIL]360$ sudo make
make modules -C /lib/modules/2.6.31-19-generic/build SUBDIRS=/home/mauro/.xpad360
make[1]: ingresso nella directory «/usr/src/linux-headers-2.6.31-19-generic»
  CC [M]  /home/mauro/.xpad360/xpad.o
/home/mauro/.xpad360/xpad.c: In function ‘xpad_open’:
/home/mauro/.xpad360/xpad.c:339: error: ‘struct input_dev’ has no member named ‘private’
/home/mauro/.xpad360/xpad.c: In function ‘xpad_close’:
/home/mauro/.xpad360/xpad.c:350: error: ‘struct input_dev’ has no member named ‘private’
/home/mauro/.xpad360/xpad.c: In function ‘xpad_probe’:
/home/mauro/.xpad360/xpad.c:440: error: ‘struct input_dev’ has no member named ‘cdev’
/home/mauro/.xpad360/xpad.c:441: error: ‘struct input_dev’ has no member named ‘private’
/home/mauro/.xpad360/xpad.c: In function ‘usb_xpad_init’:
/home/mauro/.xpad360/xpad.c:519: error: implicit declaration of function ‘info’
make[2]: *** [/home/mauro/.xpad360/xpad.o] Errore 1
make[1]: *** [_module_/home/mauro/.xpad360] Errore 2
make[1]: uscita dalla directory «/usr/src/linux-headers-2.6.31-19-generic»
make: *** [all] Errore 2

**lsusb:**

[EMAIL="mauro@workstation:%7E/.xpad"]mauro@workstation:~/.xpad[/EMAIL]360$ lsusb
Bus 002 Device 007: ID 045e:0719 Microsoft Corp. 
Bus 002 Device 005: ID 045e:0714 Microsoft Corp. 
Bus 002 Device 004: ID 045e:0717 Microsoft Corp. 
Bus 002 Device 003: ID 045e:0707 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 045e:075d Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**dmesg | tail -n20**

[EMAIL="mauro@workstation:%7E/.xpad"]mauro@workstation:~/.xpad[/EMAIL]360$ dmesg | tail -n20
[ 7501.533367] 8:3:1: usb_set_interface failed
[ 7501.837047] usb 1-1: new high speed USB device using ehci_hcd and address 9
[ 7501.985340] usb 1-1: configuration #1 chosen from 1 choice
[ 7501.988133] uvcvideo: Found UVC 1.00 device Microsoft® LifeCam Cinema(TM) (045e:075d)
[ 7501.996870] input: Microsoft® LifeCam Cinema(TM) as /devices/pci0000:00/0000:00:02.1/usb1/1-1/1-1:1.0/input/input17
[ 7503.117114] 9:3:1: cannot get freq at ep 0x82
[ 7504.241805] usb 2-2: USB disconnect, address 6
[ 7504.244080] xpad: xpad_irq_in - usb_submit_urb failed with result -19
[ 7504.316121] 9:3:1: cannot get freq at ep 0x82
[ 7505.449116] 9:3:1: cannot get freq at ep 0x82
[ 7507.469032] usb 2-2: new full speed USB device using ohci_hcd and address 7
[ 7507.694216] usb 2-2: configuration #1 chosen from 1 choice
[ 7507.697664] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input18
[ 7507.697921] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.2/input/input19
[ 7507.698139] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.4/input/input20
[ 7507.698340] input: Xbox 360 Wireless Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.6/input/input21
[ 8837.311908] padlock: VIA PadLock not detected.
[ 8837.411250] alg: No test for xts(twofish) (xts(twofish-generic))
[ 8837.472897] alg: No test for xts(serpent) (xts(serpent-generic))
[ 8837.503701] EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended.

Thank's for support!

---

