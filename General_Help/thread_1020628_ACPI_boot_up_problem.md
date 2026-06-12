---
title: "ACPI boot up problem"
date: 2008-12-24
forum: General Help
---

### Post by husky55 on 2008-12-24
I have installed Ubuntu 8.10 to my test computer and it is working fabulously. So I installed Ubuntu on my gaming desktop.

A strange thing happened. At boot up, Ubuntu hung. So I inserted the CD, nothing doing. Shut down computer.

The next day, insert Ubuntu Cd, no problem. So I installed Ubuntu inside Windows and reboot. Hung up again. Tried 64 and 32 bit flavors. Nothing doing.

I then reboot and press "Escape" and chose the bootup with the workaround ACPI, this time Ubuntu boot up and installed.

My MB is an Abit IP35-E with an Intel Quadcore 6600 and 4 GB of DDR2 and 2 WD 640GB HDs, 1 Sata DVDR and 1 IDE DVDR, Razer sound card etc...Nvidea Gforce 8800GT

So everything is well, Ubuntu downloaded all the updates but I just wonder what happened with the ACPI problem and workaround which saves my installation.

I am really impressed with how Ubuntu 8.10 recognizes my hardware i.e. network connection and drivers (sound card specifically)

---

### Post by Nepherte on 2008-12-24
I believe it added a acpi=off option to the boot command. You can verify it in the file /boot/grub/menu.lst. You should see something like:
```
# (1) Arch Linux
title  Arch Linux, kernel 2.6.27.8-1 (Recovery)
root   (hd1,0)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/ea711929-1274-4ee8-80e4-fbb556156a72 ro edd=off vga=795 **acpi=off**
initrd /boot/kernel26-fallback.img
```
but with Ubuntu instead of arch linux of course.

---

### Post by 67GTA on 2008-12-24
Sounds like you have a buggy DSDT file. If you can get it booted, post the output of ```
dmesg
``` from a terminal. You can also do this from a live CD.

---

### Post by husky55 on 2008-12-24
Wow I am really impressed. Thank you again. Not sure how to get the DSDT file yet much less the code or what is required to read it. I do have a few Linux books to read. I did use MD5SUM and burned the CD a lower speed. During install, Ubuntu checked the files so I doubt if any file is corrupted (although it certainly is a possibility). Used both 32 and 64 bit Ubuntu CD and install and had the same problem.

---

### Post by 67GTA on 2008-12-24
If dmesg shows acpi errors, it is not hard to fix the DSDT file. Most of the time, your DSDT file has been compiled with Windows in mind:(. ACPI tries to read it (in your bios) during install. I can probably help you fix it, and load it into the kernel if your not afraid of using the command line. To get started:

```
sudo apt-get install iasl
``` (intel asl compiler)
```
sudo cat /proc/acpi/dsdt > dsdt.dat
``` (This makes a copy of your DSDT file in your /home folder)
```
iasl -d dstd.dat
``` (This will disassemble the DSDT and create a dsdt.dsl file among others. Our main focus is dsdt.dsl)
```
sudo iasl -tc dsdt.dsl
``` (This will compile the dsdt.dsl file, optimize for linux, and show any remaining errors to be fixed.) If you get that far, post the output of the last command, and we will see how bad it is.

---

### Post by husky55 on 2008-12-24
I will do this after the holiday. My wife is pretty unhappy with my lack of house cleaning and holiday shopping so far.

I know what I must do first!!!

:)

---

