---
title: "Kernel update 2.6.15.25 changelog??"
date: 2006-06-15
forum: Desktop Environments
---

### Post by derk.d on 2006-06-15
Where can you find the changelog of the new 2.6.15.25 kernel?? in synaptic isn't the list of changes available...

---

### Post by FredB on 2006-06-15
Erh... Here ?

[https://lists.ubuntu.com/archives/dapper-changes/2006-June/thread.html]("https://lists.ubuntu.com/archives/dapper-changes/2006-June/thread.html")

---

### Post by derk.d on 2006-06-15
[QUOTE=FredB]Erh... Here ?

[https://lists.ubuntu.com/archives/dapper-changes/2006-June/thread.html]("https://lists.ubuntu.com/archives/dapper-changes/2006-June/thread.html")[/QUOTE]

The new kernel update isn't in the list (yet)?!?!?!?

---

### Post by FredB on 2006-06-15
yes, it looks like it is the case :(

---

### Post by FredB on 2006-06-15
Found on a french support forums for Ubuntu :

```
linux-source-2.6.15 (2.6.15-25.43) dapper-security; urgency=low

  Changes by Ben Collins

  * bcm43xx dma mask handling (> 1GB memory)
  - Add powerpc IOMMU handlers for dma masks
  - Sync updates to amd64 IOMMU to handle dma masks

  * Sync ide changes for better flash driver handling (flash isn't removable).

  Changes by David S. Miller

  * [SPARC64]: Temporary workaround for memory corruption on Niagara.

 -- Fabio M. Di Nitto <fabbione@ubuntu.com>  Wed, 14 Jun 2006 11:05:57 +0200

linux-source-2.6.15 (2.6.15-24.42) dapper-security; urgency=low

  Changed by Daniel T Chen

  * Fix cs4266 build failure.

 -- Ben Collins <bcollins@ubuntu.com>  Mon, 12 Jun 2006 22:26:24 -0400

linux-source-2.6.15 (2.6.15-24.41) dapper-security; urgency=low

  Changes by Ben Collins

  * usb: Enable CONFIG_USB_EHCI_SPLIT_ISO and CONFIG_USB_EHCI_ROOT_HUB_TT
    - Malone #28840
    - Malone #49367
  * usb: Enable CONFIG_USB_SUSPEND
  * powerpc: Fix for smp clock timer
    - Malone #29420
    - Git cherry pick: 0c2aca88bdac4254a13466fb108733d243a118b6
  * powerpc: Enable zilog as a module, and serial core/8250 as modules as
    well.
    - Malone #36499
  * btsco: Patch to get headset working.
    - Maline #48910

  Changes by Chuck Short

  * speedstep-smi: Allow speedstep-smi to load Thinkpad T20.
    - Malone #35044

  Changes by Daniel T Chen

  * sound/pci/cs46xx: Fix PM support for snd_cs46xx
    - Malone #11149

  Changes by David S Miller

  * [SPARC64]: Avoid JBUS errors on some Niagara systems.

 -- Ben Collins <bcollins@ubuntu.com>  Mon, 12 Jun 2006 12:27:42 -0400

linux-source-2.6.15 (2.6.15-24.40) dapper-security; urgency=low

  Changes by Ben Collins

  * psmouse: Total reset for intellimouse.
    - Malone #30224
  * powerpc: Add one-liner to fix physical memory mapping on some G3's.
    - Malone #34508
  * nsc-ircc: Update to latest code to fix crashes.
    - Malone #46947
  * nsc-ircc: Add some IBM thinkpads
  * ahci: Add support for JMicron ahci controller.
    - Malone #45839
  * acx: Make all TI ACX111's use 1.2.1.34 firmware.
    - Malone #30766
  * sky2: Update to latest version, 1.4.
    - Malone #38865 (and others)
  * rt2500: Update to CVS code, which the maintainer says will fix our SMP
    related bugs with this driver.
  * PCI: reverse pci config space restore order. Stolen from upstream patch.
    This should fix a few resume bugs for hardware that stricly needs to
    adhere to PCI specs. MacTel is one of the biggest examples.
  * Disable davicom usage in tulip driver to let dmfe module takeover.
    - Malone #48287
  * powerpc: Enable MESH and MAC_FLOPPY drivers.
  * acpi/ec: Use semaphore instead of spinlock to get rid of missed interrupts
    - Malone #39315
  * i386/amd64: Change HZ=1000 to HZ=250. The high frequency was causing high
    power consumption on some laptops, and also some latency under certain I/O
    loads.
  * irda/sir: Fix wait operations in kernel thread. Use proper
    wait_event_interruptible_timeout().
    - Malone #45542
  * hid-powerbook: Enable on i386 for MacTels.
  * i386: Add Averatec 3200 to list of acpi=noirq dmi matches.
    - Malone #48263

  Changes by David S Miller

  * [SPARC64]: Fix missing fold at end of checksums.
  * [SPARC64]: Fix D-cache corruption in mremap.
  * [TG3]: Handle Sun onboard tg3 chips more correctly.

  Changes by Fabio M. Di Nitto

  * [debian/config] Enable HUGE_TLB & Co. on sparc64.

  Changes by Daniel T Chen

  * sound/{drivers/opl3,synth/emux}/: Fix port type bits
  * sound/pci/ac97/: Add workaround for ASUS A6KM
  * sound/pci/hda/: Fix handling of capture controls on ALC882 3/6-stack models
  * sound/core/: Fix pcm-draining of capture stream in PCM middle layer
  * sound/pci/hda/: Fix init verbs for ALC260 hp model
  * sound/usb/: Add workaround for CSR Bluetooth Headphones
  * sound/synth/emux/: Fix NULL pointer dereference
  * sound/pci/hda/: Fix codec model for HP dc7600
  * sound/pci/ice1712/: Don't use Consumer AC97 for Terratec DMX6fire
  * sound/pci/hda/: Add support for more Sony Vaio models
  * sound/pci/hda/: Add support for Sigmatel 922[7-9] HDA codecs
  * sound/pci/ac97/: Add ThinkPad T41p to Jack Sense blacklist
  * sound/pci/: Fix incorrect mixer element name for cmipci
  * sound/pci/{cs46xx,hda}/: Fix race in removing device
  * sound/pci/hda/: Add HP nx6320 to supported list
  * sound/pci: Fix additional races in the irq handler and ioremap()

  Changes by Ryan Lortie

  * snd-hda-intel: fix routing on macbook
  * usb-hid: enable Fn key on Macbook keyboard (Intel)
  * libata: delay resume to wait for harddrives to spin up
  * ich7-sci-en-quirk: poke the SCI_EN bit on Macbook resume

  Security updates

  * CVE-2006-1052: Cherry picked
  * CVE-2006-1066: Cherry picked
  * CVE-2006-1368: Cherry picked
  * CVE-2006-1525: Cherry picked
  * CVE-2006-1055: Cherry picked
  * CVE-2006-0744: Cherry picked
  * CVE-2006-0038: Cherry picked and merged
  * CVE-2006-1522: Cherry picked
  * CVE-2006-1527: Cherry picked
  * CVE-2006-1056: Cherry picked and merged
  * CVE-2006-1863: Cherry picked
  * CVE-2006-1864: Copied patch and applied
  * CVE-2006-1859: Cherry picked
  * CVE-2006-1860: Cherry picked
  * CVE-2006-2271: Cherry picked
  * CVE-2006-2272: Cherry picked
  * CVE-2006-2274: Cherry picked
  * CVE-2006-2275: Cherry picked
  * CVE-2006-1857: Cherry picked
  * CVE-2006-1858: Cherry picked
  * CVE-2006-2444: Cherry picked

 -- Ben Collins <bcollins@ubuntu.com>  Fri,  9 Jun 2006 12:15:10 -0400
```

---

