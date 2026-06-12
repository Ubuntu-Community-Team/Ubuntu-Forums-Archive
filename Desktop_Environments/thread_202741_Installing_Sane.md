---
title: "Installing Sane"
date: 2006-06-24
forum: Desktop Environments
---

### Post by canadianwriterman on 2006-06-24
I've installed Sane through Synaptic with no problem. However, I need the Pixma back end. I downloaded the file from the Sane site, but when I ren "make" in the terminal, it doesn't work. What files do I need to install to get make to work? Thanks.

---

### Post by aysiu on 2006-06-24
Can you be more specific than "it doesn't work"? What error do you get?

I suspect it's something like ```
bash: make command not found
``` If so, try ```
sudo aptitude update
sudo aptitude install build-essential
``` and try again to compile the Pixma backend.

---

### Post by canadianwriterman on 2006-06-24
Actually, build-essential was what I was missing. The pixma backend installed, however, I get an error that no device was found. When I run the command to check for devices, the USB-connected Pixma MP500 is detected as shown below:

root@linux-o9y4:/home/stephen# scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
root@linux-o9y4:/home/stephen# sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

[COLOR="RoyalBlue"]found USB scanner (vendor=0x04a9 [Canon], product=0x170c [MP500]) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported[/COLOR]
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

However, I can't figure out where to go from there.

---

### Post by aysiu on 2006-06-24
I'm sorry. I don't have a scanner, so it's all Greek to me.

---

### Post by canadianwriterman on 2006-06-24
Okay, I finally got Sane working and it scans. But, only in the root terminal. I've added a desktop icon, with the command xscanimage (which works in the terminal). Nothing happens. I've added myself as a user in the "scanner" group and the permissions show up the the icon's properties okay, but it doesn't run.

---

### Post by penvzila on 2007-02-23
Did you run 'make' or 'sudo make'?

---

