---
title: "Dell Inspiron 530 - Gutsy"
date: 2008-01-17
forum: Dell  Ubuntu Support
---

### Post by ikkepjo on 2008-01-17
Hi all,

I recently acquired one of those, with an E6550 Core2Duo processor. I have made a clean install of Gutsy (7.10) from the LiveCD . I choose the i386 because I have no interest in spending any time in figuring out how to get various flash and etc apps working under 64bit.

I experience a very worrisome problem: sometimes, about 1 in 4, the OS doesn't start up, it just hangs. After a while it reboots automagically, and then it may or may not start up. This can happen several consecutive times. 

I investigated, and after restarting in recovery mode (which has the nicety to display all /var/log/messages on the screen so you can follow) I saw that it does not manage to set up ata.1, my hard disk. The exact message I did not get a chance to write down, but it was something about time out.

Now, this is weird, because starting up Gutsy happens after grub, and that resides on the same disk so obviously it must have been available. So why do I loose it afterwards?
Also, very early in the process, I see that ata.1 is correctly identified, with seemingly the right parameters.

I checked the disk with the Dell diagnostic tools, everything is fine.

I configured a dual boot with Vista, booting in Vista never fails (but then, I hardly do that, so that may not be statistically relevant)

I cannot give the /var/log/messages messages exactly as they are not written in a file at failed startup because he then thinks there is no disk to write to.

Ideas anyone? This gives me the willies ...

Peter

---

### Post by MJN on 2008-01-17
It might be worth changing the the boot options to enable you see the boot process/progress (as per recovery) by hitting 'e' when the Grub screen appears, highlighting kernel line and modiyfing the options to read 'noquiet nosplash'. If you then hit 'b' to boot you will see the boot process in all its glory.
 
Keep doing this until you experience the hanging and try and ascertain at what stage this happened. It could well be something as innocent as fsck checking the partitions every x mounts and hence giving the appearance of a hung machine when it is in fact doing something.
 
Mathew

---

### Post by ikkepjo on 2008-01-22
> **MJN said:**
> It might be worth changing the the boot options to enable you see the boot process/progress (as per recovery) by hitting 'e' when the Grub screen appears, highlighting kernel line and modiyfing the options to read 'noquiet nosplash'. If you then hit 'b' to boot you will see the boot process in all its glory.
 
Keep doing this until you experience the hanging and try and ascertain at what stage this happened. It could well be something as innocent as fsck checking the partitions every x mounts and hence giving the appearance of a hung machine when it is in fact doing something.
 
Mathew

Thanks Matthew, I have done that and have come up with a more or less consistent pattern (had to do it several times, and whaddayaknow, it fails hardly ever when you're looking at it)

Nevertheless, the sequence of events:

when all goes well: 
ata1: SATA max UDMA/133 cmd 0x0001f700 ctl 0x0001f602 bmdma 0x0001f300 irq 20
ata2: SATA max UDMA/133 cmd 0x0001f500 ctl 0x0001f402 bmdma 0x0001f308 irq 20
usb 3-5: new high speed USB device using ehci_hcd and address 2
ata1.00: ATA-7: ST3320620AS, 3.ADG, max UDMA/133
ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
ata1.00: configured for UDMA/133

Note the USB stuff, it is interspersed between the ata stuff

when it doesn't go:
I get the last line of the USB config:
attached scsi generic sg3

then a long pause (about a minute)

then 
ata.1: qc timeout (cmd 0x27)
ata.1: hpa sectors (0) is smaller than sectors [a big number]
ata.1: failed to set xfermode (errmask=0x40)
ata.1: limiting speed to UDMA/133: PIO3

and then it reboots.

An idea, anyone?

Peter

---

### Post by MJN on 2008-01-22
Ignore the USB aspects - they will indeed pop in an out of an otherwise ordered boot log due the nature of how the USB bus operates - it is heavily hotplug-biased and so there are plenty of pauses and general 'relaxed' behaviours of devices.

I take it the machine is configured (hardware/BIOS-wise) as per the default shipped build? I would normally put these sorts of errors (of this type as opposed to these very errors) a result of incompatible hardware, IRQ settings, cable configurations etc - all stuff that a pre-built (and certified) machine is meant to be free of.

Do you have anything connected to the USB bus? Are there any mentions of IRQ settings/problems in the logs? (Post the whole lot if you're not sure) Have you adjusted the IRQs in the BIOS?

Am I to infer from the 'LiveCD' mention that you haven't used the Dell-specific 7.10 release? I'm not saying this is the problem, but it's something to bear in mind either way.

Mathew

---

### Post by ikkepjo on 2008-01-24
> **MJN said:**
> Ignore the USB aspects - they will indeed pop in an out of an otherwise ordered boot log due the nature of how the USB bus operates - it is heavily hotplug-biased and so there are plenty of pauses and general 'relaxed' behaviours of devices.

I just mentionned the USB stuff because, when it fails, the last screenfull is just a sequence of USB stuff, neatly together. Whereas when it works, there is lots of stuff interspersed. So the non-USB part somehow stops, I guess, and times out

> **MJN said:**
> I take it the machine is configured (hardware/BIOS-wise) as per the default shipped build? I would normally put these sorts of errors (of this type as opposed to these very errors) a result of incompatible hardware, IRQ settings, cable configurations etc - all stuff that a pre-built (and certified) machine is meant to be free of.
As come out of the box. It was not a linux box, Dell doesn't do that in Belgium, but I have not opened it ...

> **MJN said:**
> Do you have anything connected to the USB bus? Are there any mentions of IRQ settings/problems in the logs? (Post the whole lot if you're not sure) Have you adjusted the IRQs in the BIOS?
Yes, a scanner (Canon Lide30), the bluetooth dongle for mouse and keyboard. I have not touched IRQ setting in the BIOS

> **MJN said:**
> Am I to infer from the 'LiveCD' mention that you haven't used the Dell-specific 7.10 release? I'm not saying this is the problem, but it's something to bear in mind either way.

Mathew
I don't know where to get the Dell release for this machine, as it is not delivered with Ubuntu around here.

I made a small mistake in reporting the output of the fails: the line starts with ata1.00 rather than ata1

Also, when it fails, I seem to get a similar line 
ata1: SATA max UDMA/133 cmd 0x0001f700 ctl 0x0001f602 bmdma 0x0001f300 irq 20
ata2: SATA max UDMA/133 cmd 0x0001f500 ctl 0x0001f402 bmdma 0x0001f308 irq 20

early on in the process. I am not sure why there are 2, I have only one disk, and I have 2 CD/DVD readers, so there should be 1 or 3? I thought it could be partitions, but then I have even more: dell recovery, vista, / and /home?

Is there a way to control the scrolling so that you cab actually look at it? Normally it gets into /var/log/messages, but when it has no disk it doesn't put it there, of course ...

I have the impression there is something flaky with the Gutsy install, I also have issues with X (minor one, it doesn't read .Xmodmap on login), gdm (sound config is not stable) and a few other (dbus?) items ...

Grrr

Peter
It is very difficult to see what is happening because it scrolls rather fast.

---

### Post by MJN on 2008-01-24
I'd be inclined to try and reach out for someone who has got the 'official' Linux version of the 530N and to see how there IRQ maps compare to yours (if they are customisable).

My gut feeling is that it's an IRQ conflict - possibly between USB and the SATA controllers.

You can download the Dell-tweaked 7.10 ISO [here](http://linux.dell.com/wiki/index.php/Ubuntu_7.10) although I wouldn't necessarilly hold my breath expecting that to solve it if it's a hardware configuration issue.

Mathew

---

### Post by jerrykenny on 2008-01-24
/var/log/dmesg  should let you view your startup logs at leisure, . . . . there will also be gzipped versions of previous boot messages.

Is it possibly rebooting due to a fsck problem ? whate fs are you using ? 

Not sure how rigourous the Dell diagnostic facikity (i've never owned a Dell) but the Hard drive manufacturer will will probably be able to supply a comprehensive facility fir checking you hdd, and cable.

---

### Post by ikkepjo on 2008-01-24
> **jerrykenny said:**
> /var/log/dmesg  should let you view your startup logs at leisure, . . . . there will also be gzipped versions of previous boot messages.

Is it possibly rebooting due to a fsck problem ? whate fs are you using ? 

Not sure how rigourous the Dell diagnostic facikity (i've never owned a Dell) but the Hard drive manufacturer will will probably be able to supply a comprehensive facility fir checking you hdd, and cable.

Yes, when it has found ata1.00 and decided to mount it ... however it doesn't find it, hence doesn't write to it

Diagnostics are good, I used them before (on other pcs) to find real problems, comes thru 100% clean ...

And I am not sure it is a disk problem, early in the process it is correctly detected, and then lost 

I am using ext3 

Peter

---

### Post by ikkepjo on 2008-01-24
> **MJN said:**
> I'd be inclined to try and reach out for someone who has got the 'official' Linux version of the 530N and to see how there IRQ maps compare to yours (if they are customisable).
Mathew


How does one find the mappings? In the BIOS or is it elsewhere? 

Peter

---

### Post by ikkepjo on 2008-01-24
One thing I forgot to mention, I actually run Xubuntu, aout of habit (and also because I quite like it), but I would not expect that to cause any issue?

Peter

---

### Post by MJN on 2008-01-24
The IRQ settings will indeed be in the BIOS (if at all - with the prevalence of PNP OS's the feature requirements of the BIOS are dwindling).
 
Regarding Xubuntu that's not really an issue as the stage we're looking at here is very early on in the boot process - way before we get to window managers and other userland processes.
 
Mathew

---

### Post by MJN on 2008-01-24
Stab in the dark time - I see from the Dell user guide at [http://support.euro.dell.com/support/edocs/systems/inspd530/EN/OM/appendix.htm#wp1057460](http://support.euro.dell.com/support/edocs/systems/inspd530/EN/OM/appendix.htm#wp1057460) that you can set the SATA mode for the controllers - IDE or RAID.
 
If yours is on IDE (the default) try setting it to RAID - this should enable the AHCI featureset which may prove a more stable method of detecting and configuring the disks.
 
I don't know how your Vista install will cope with this change but try it for Ubuntu and see if there's any change.
 
Mathew

---

### Post by boyofford on 2008-01-25
I think I've got a similar problem, sometimes when trying to boot into 7.10, screen switchs off and computer restarts, and this does not go away until I do a memory test, (Note: don't really understand why this happens or why this works).

Does seem to happen generally after i've been using vista (got dual boot setup) but not everytime.

Got a 530s..see signature

Like I said not sure if eaxctly same problem as you've got... or this is a genuine solution as only soves problem for a week or so at a time!

---

### Post by ikkepjo on 2008-01-28
> **MJN said:**
> Stab in the dark time - I see from the Dell user guide at [http://support.euro.dell.com/support/edocs/systems/inspd530/EN/OM/appendix.htm#wp1057460](http://support.euro.dell.com/support/edocs/systems/inspd530/EN/OM/appendix.htm#wp1057460) that you can set the SATA mode for the controllers - IDE or RAID.
 
If yours is on IDE (the default) try setting it to RAID - this should enable the AHCI featureset which may prove a more stable method of detecting and configuring the disks.

I tested this a few days ... not a single failure on boot anymore. It seems to do the trick, no idea why?



> **MJN said:**
>  
I don't know how your Vista install will cope with this change but try it for Ubuntu and see if there's any change.
 
Mathew
Never mind Vista :)

Thanks,

Peter

---

### Post by MJN on 2008-01-28
> **ikkepjo said:**
> It seems to do the trick, no idea why?

As mentioned it was just a hunch based on the fact that SATA running in RAID mode (with the ACHI featureset that this inherently brings) uses a significantly different architecture to access the drives.

Not only does this architecture suit your native setup (i.e. using SATA drives as SATA drives, not pseudo-IDE drives) but it also brings other features such as hotplugging (or at least the potential for) which in turn requires a degree of self-correcting operation and increased resilience to timing issues etc. I suspect that now you're using AHCI you may well be sidestepping the otherwise-volatile boot process issues.

In other words, I don't know for certain!

Mathew

---

