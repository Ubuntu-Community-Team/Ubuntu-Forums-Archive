---
title: "Any IEEE 1394 keyboards for a dedicated-organ 'puter?"
date: 2020-12-09
forum: Gaming &amp; Leisure
---

### Post by bcschmerker on 2020-12-09
As of December 2020 I am assessing the available-hardware situation for a dedicated Aeolus station built on a Gateway®/ac*e*r® DX4822-01 (Acer G43T-AM planar; intel® Pentium Processor® E5300 (FCLGA 775); 6 GiB DDR2-533 main memory) with a Creative Laboratories® SB0350 PCI 2.0 audio adapter (Creative Technology CA0102 DSP/synth) and SB0250 I/O Drive.  I'm already aware of some of the Audigy2 hardware bugs (e.g., a 31- rather than 32-bit address for the CA0102 sample DMA) and Intel Corporation's decision to exclude the Wolfdale platform from a microcode upgrade to mitigate CVE-2017-5715 (see "[[ubuntu] Meltdown and Spectre Discussion Sticky](https://ubuntuforums.org/showthread.php?t=2381801)").  For the purpose of testing different Kernels via GRUB 2.04, I'm planning on the following /etc/default/grub:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT=10
GRUB_TIMEOUT_STYLE=hidden
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_EARLY_INITRD_LINUX_STOCK="microcode.cpio"
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="debug memmap=2048M\\$6144M"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=1024x768
#GRUB_GFXPAYLOAD_LINUX=keep

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
GRUB_INIT_TUNE="480 440 1"


```
The planar intel® GPU is already supported in X11 with the i915/i945 video drivers insofar as necessary for an operator monitor, which HAS to be DE-15 analog due to a known hardware bug in the HDMI installation.  However, Google® Search gave me no leads on an IEEE 1394 keyboard controller (which would send MIDI signals to the SB0350 via the onboard IEEE 1394, which Creative calls SB1394); and I anticipate needing three 61-note manuals (C2-C7) and a 30-note concave parallel or 32-note concave radiating pedalboard, plus an up to 32-drawknob input board.  Who has information on suitable hardware for the MIDI input via IEEE 1394 (including, if possible, a multi-channel MIDI adapter in case I have to fall back on MIDI manuals, pedalboard, and stop board from Classic Organ Works)?

---

