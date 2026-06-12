---
title: "ubuntu 11.04 blank ttys/virtual console"
date: 2011-10-01
forum: Desktop Environments
---

### Post by mzycdth on 2011-10-01
Hi all,

just installed and fully updated natty narwhal (2.6.38-11-generic kernel, GNOME 2.32.1) on acer 5930g (3.0gb RAM, Intel p7350, Nvidia 9600M GT) onto a replacement HDD while my SSD is away for repair.

I want to install the Nvidia driver from their site as it significantly improves my laptop performance but my virtual consoles (ctrl+alt+fn 1-) are all blank.

I've spent the morning wading through a variety of forums and tutorials and haven't fixed the problem. Is there a full overview of how to sort this common problem somewhere? I've included some information below (you can see I've changed some of the defaults).

> **modprobe.d/blacklist.conf]
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves said:**
> 

[quote=/etc/defaults/grub]
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
#GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=800"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

GRUB_GFXPAYLOAD_LINUX=text


[quote=/etc/modprobe.d/nvidia-graphics-drivers.conf]
blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-current
blacklist nvidia-96
[/quote]

---

### Post by mzycdth on 2011-10-01
hi guys,

sorry to bump so quickly but the performance is so bad that my backtrack 5 flash drive OS (with the NVIDIA driver installed) works better/faster.

I'm aware this is a common problem but it seems to have a multitude of causes/solutions.

I'm not able to run inkscape effectively which I need for work :(

---

### Post by mzycdth on 2011-10-01
Many hours later I decided to try and fix the problem myself manually (i.e. terminally!). The following worked for me, please back up all your data before you attempt to do the same. I think the ubuntu team have attempted to improve their NVIDIA support with the latest updates, but it still doesn't match using the proprietary drivers from NVIDIA themselves!

1. identify and download the correct driver at [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

2. open terminal in your X environment and type the following:
> sudo apt-get remove --purge nvidia*3. Then type: (you SHOULD get an error here, nouveau shouldn't be properly installed anyway but may be if you've attempted other methods)
> sudo apt-get remove --purge nouveau*4. Then:
> sudo nano /etc/modprobe.d/blacklist.confThis will open a terminal text editor, scroll to the bottom and type:
> blacklist nouveau*
ctrl+x
y
enter5. reboot then hit: (this takes you to a virtual console)
> ctrl+alt+f1 (or f2, or f3 etc)6. Login then navigate to the folder you downloaded the NVIDIA file to:
> cd /Downloads
sudo sh NVIDIA <tab><tab>
enter7. Follow the installation through then reboot - DONE!

---

