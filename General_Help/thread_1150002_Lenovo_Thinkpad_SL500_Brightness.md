---
title: "Lenovo Thinkpad SL500 Brightness"
date: 2009-05-05
forum: General Help
---

### Post by johnjust on 2009-05-05
In my search to fix my brightness buttons on my new Ubuntu 9.04 Laptop, I found this driver:

[http://github.com/tetromino/lenovo-sl-laptop/tree/master](http://github.com/tetromino/lenovo-sl-laptop/tree/master)

It's a C file, and there are different ways to load it with different modules, but I've never had to install a driver through a C file before.

Can anyone lend a hand with this?  Here is the info from the README file:

> 
lenoso-sl-laptop

This is an experimental driver for the Lenovo ThinkPad SL
series, since those laptops are currently not supported by
the thinkpad_acpi driver.

Works: hotkeys, bluetooth, the Lenovo Care LED, the fan
Experimental: backlight brightness
Not implemented: hdaps accelerometer

NB: to make the Lenovo Care LED blink, make sure the LED timer
trigger is enabled (CONFIG_LEDS_TRIGGERS_TIMER) and do
echo "timer" > /sys/class/leds/lensl::lenovocare/trigger


The backlight brightness control is useful because the SL
series use the ACPI brightness API in a non-standard manner,
causing buggy behavior with the standard ACPI video module
backlight control.

To enable the brightness control, load the module with the 
"control_backlight=1" module parameter (i.e.
insmod lenovo-sl-laptop.ko control_backlight=1 )

Note that the brightness control will likely conflict with
the ACPI video driver brightness control. So, if you have
the ACPI video driver loaded (and you probably do):

echo 0 > /sys/module/video/parameters/brightness_switch_enabled
insmod lenovo-sl-laptop.ko control_backlight=1
and then restart X.

Alternatively, you can try to use the "acpi_backlight=vendor"
kernel boot parameter (recognized by kernel versions 2.6.28
and higher).

Alternatively alternatively, simply unload the ACPI video
driver (rmmod video).


To build the module for your current kernel, run make.
Note that you will need to have the sources or headers for 
your kernel in the correct location (depends on the distro).



Also, I'm not sure how it all works, but is this something that is done once then never needed again, or is this like a script in that I would have to set it up to run at boot?

Thanks for any assistance!

---

### Post by Wangberg on 2009-05-25
i'm looking for help on this one also.  i've tried to make this file, but keep running into this error:

```

wangberg@dino:~/Desktop/tetromino-lenovo-sl-laptop-c594820b5ca36b73b311ee4cbace54f223be2377$ sudo make
make -C /lib/modules/2.6.28-11-generic/build M= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [all] Error 2

```

i've tried the solution from this thread [http://ubuntuforums.org/showthread.php?t=1047374](http://ubuntuforums.org/showthread.php?t=1047374) to no avail.  My kernel-header and full sources are unpacked and in /usr/src/ so i'm not quite sure how to get around this problem.  

any suggestions would go greatly appreciated!

thanks,
wangberg

---

### Post by Wangberg on 2009-05-26
> **Wangberg said:**
> i'm looking for help on this one also.  i've tried to make this file, but keep running into this error:

```

wangberg@dino:~/Desktop/tetromino-lenovo-sl-laptop-c594820b5ca36b73b311ee4cbace54f223be2377$ sudo make
make -C /lib/modules/2.6.28-11-generic/build M= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [all] Error 2

```

i've tried the solution from this thread [http://ubuntuforums.org/showthread.php?t=1047374](http://ubuntuforums.org/showthread.php?t=1047374) to no avail.  My kernel-header and full sources are unpacked and in /usr/src/ so i'm not quite sure how to get around this problem.  

any suggestions would go greatly appreciated!

thanks,
wangberg

i just comitted the cardinal sin in asking for help on message forums by being too hasty in my search.  my apologies! 

getting this module installed is outlined in a how-to and greater discussion on this laptop's acpi support is discussed in this thread:

[http://ubuntuforums.org/showthread.php?t=1137682&highlight=sl500+brightness](http://ubuntuforums.org/showthread.php?t=1137682&highlight=sl500+brightness)

---

### Post by ignasigarcia on 2009-06-19
I use Jaunty with some changes and I my thinkpad sl500 works great now:

First, I use kernel 2.6.30 available from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Since I use 64bits ubuntu I installed:

linux-headers-2.6.30-020630-generic_2.6.30-020630_amd64.deb
linux-headers-2.6.30-020630_2.6.30-020630_all.deb
linux-image-2.6.30-020630-generic_2.6.30-020630_amd64.deb

This kernel supports partially the sl500 and fixes all brightness problems. However, some other things still do not work, such as volume hotkeys. Si I aldo did this:

I compiled and installed the Tetromino Kernel module available here: [http://github.com/tetromino/lenovo-sl-laptop/tree/master](http://github.com/tetromino/lenovo-sl-laptop/tree/master)

Unzip/untar the compressed file, compile and install running these commands:

make all
sudo cp lenovo-sl-laptop.ko /lib/modules/`uname -r`/kernel/drivers/misc
sudo depmod

Blacklist the thinkpad-acpi module (not sure this is necessary though), by editing /etc/modprobe.d/blacklist.conf (in prior versions of ubuntu the file does not have the .conf extension) and adding:

blacklist thinkpad-acpi

Run this to create a new file in /etc/modprobe.d

echo options lenovo-sl-laptop control_backlight=1 > /etc/modprobe.d/lenovo-sl-laptop.modprobe.conf


Finally, edit /etc/rc.local and add these 2 lines before the "exit 0" statement:

echo 0 > /sys/module/video/parameters/brightness_switch_enabled
modprobe lenovo-sl-laptop


Hope it works for you

Ignacio

---

### Post by nickhaw on 2009-08-18
> **ignasigarcia said:**
> I use Jaunty with some changes and I my thinkpad sl500 works great now:

First, I use kernel 2.6.30 available from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Since I use 64bits ubuntu I installed:

linux-headers-2.6.30-020630-generic_2.6.30-020630_amd64.deb
linux-headers-2.6.30-020630_2.6.30-020630_all.deb
linux-image-2.6.30-020630-generic_2.6.30-020630_amd64.deb

This kernel supports partially the sl500 and fixes all brightness problems. However, some other things still do not work, such as volume hotkeys. Si I aldo did this:

I compiled and installed the Tetromino Kernel module available here: [http://github.com/tetromino/lenovo-sl-laptop/tree/master](http://github.com/tetromino/lenovo-sl-laptop/tree/master)

Unzip/untar the compressed file, compile and install running these commands:

make all
sudo cp lenovo-sl-laptop.ko /lib/modules/`uname -r`/kernel/drivers/misc
sudo depmod

Blacklist the thinkpad-acpi module (not sure this is necessary though), by editing /etc/modprobe.d/blacklist.conf (in prior versions of ubuntu the file does not have the .conf extension) and adding:

blacklist thinkpad-acpi

Run this to create a new file in /etc/modprobe.d

echo options lenovo-sl-laptop control_backlight=1 > /etc/modprobe.d/lenovo-sl-laptop.modprobe.conf


Finally, edit /etc/rc.local and add these 2 lines before the "exit 0" statement:

echo 0 > /sys/module/video/parameters/brightness_switch_enabled
modprobe lenovo-sl-laptop


Hope it works for you

Ignacio

Thanks for that, worked a treat on my SL500. Had to su rather than sudo on the 

echo options lenovo-sl-laptop control_backlight=1 > /etc/modprobe.d/lenovo-sl-laptop.modprobe.conf

command.

Cheers

---

