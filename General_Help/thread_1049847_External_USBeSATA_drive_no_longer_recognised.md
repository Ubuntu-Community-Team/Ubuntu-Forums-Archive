---
title: "External USB/eSATA drive no longer recognised"
date: 2009-01-25
forum: General Help
---

### Post by Bucky Ball on 2009-01-25
Hi all.

I have a WD GreenPower 500Gb hard drive in a Coolermaster external case which is eSATA and USB. The eSATA I haven't had a look at setting up, but the USB connection has always worked fine. 

Today, when I really need to use it for uni, plug it in and thought I might try the eSATA cable. Gives me an error message about 'can't mount' and so bah, I'll look at that some other time and boot with USB as per normal. Wrong.

Now the machine doesn't recognise the external drive anywhere and it is not showing up anywhere so I don't have much chance of even manually mounting it. I have looked in:

```
dmesg | tail
sudo fdisk -l
df -h
```Nothing. I doubt this is caused by trying the eSATA, but you never know. I did just have an update which installed kernel 2.6.24-23-rt (the realtime kernel for Ubuntu Studio) from 2.6.24-22-rt. I tried the .22 kernel in which it was working though, and no different.

I have tried the drive in XP and it works fine. I can get around this for now but when uni hots up, this will be a nightmare, so any suggestions greatly appreciated.

* Add to that list GParted; the drive is nowhere to be seen.

---

### Post by Bucky Ball on 2009-01-25
I seem to be getting the same error message for eSATA and USB connection types:

> org.freedesktop.hal.storage.mount-fixed no <--(action, result).I open Authorisations and find the location (or something similar) but can't change any of the settings. What I did find was this, under 'Mount File Systems From Removable Drives':

> Anyone: no
Console: no
Active Console: Active Administrator (keep indefinitely)Figure I should become root so drop to terminal and type:

```
gksudo policykit
```... and nothing. 

I might add that I am using Xubuntu with Ubuntu Studio packages except the artwork. This includes the realtime kernel. But as I say, the drive was working fine before so doubt this is it. Starting to wonder about the kernel update. 

Anyone?

---

### Post by Bucky Ball on 2009-01-25
Okay, this is where I am up to. When I switch on the drive then enter:

```
dmesg | tail
```I get this:

```
[ 1708.676682]  sde: sde1 < sde5 sde6 sde7 >
[ 1709.081854] sd 6:0:0:0: [sde] Attached SCSI disk
[ 1709.081935] sd 6:0:0:0: Attached scsi generic sg5 type 0
[ 2689.433772] FAT: Unrecognized mount option "force" or missing value
[ 2719.390596] usb 5-1: USB disconnect, address 2
[ 2719.390604] usb 5-1.4: USB disconnect, address 3
[ 2739.637306] usb 5-1: new high speed USB device using ehci_hcd and address 4
[ 2739.751784] usb 5-1: configuration #1 chosen from 1 choice
[ 2739.752248] hub 5-1:1.0: USB hub found
[ 2739.752484] hub 5-1:1.0: 4 ports detected
```So it is there. But that is all I get. Can't mount anything manually and not showing up anywhere else. Locked out of Authorizations so can't change them and they seem to be wrong, and also can't unlock anything in Users and Groups. Things seem to have changed with that last kernel update. My permissions seem to have changed somewhat!

When I enter lsusb, I get this:

```
bucky@studiobox:~$ lsusb
Bus 005 Device 004: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```The drive comes to life and I get an error message for each logical drive (partition) on the disk as it tries to connect:

> org.freedesktop.hal.storage.mount-fixed no <--(action, result).But can't change Authorisations. Oh, joy. Just when I really need to use this hard drive. Help! (please - if you have any clues at all) ...

---

### Post by Bucky Ball on 2009-01-28
Adding to this ...

Just tried the external drive on my Xfce laptop and shows up no problem. All fine. Points to the recent kernel upgrade. Any help on this would be greatly appreciated.

---

### Post by Gizenshya on 2009-01-28
even though you didn't mention it, did you happen to change a setting on the external drive?  Jumper setting on the drive itself, jumper settings on the enclosure, or a switch on/in the enclosure *might* cause something like that.

have you tried plugging it into another USB controller (not just another usb slot.. needs to be a different controller)?

have you tried a different sata drive in the enclosure?

do you have another sata enclusure to put the drive in?  (could eliminate the enclosure)

do you have another sata drive to try in that enclosure? (even your internal one, just boot from the live CD)  (this could eliminate the drive).

hmm.. live CD... Just disable (remove) your main boot drive and boot from a Live CD.  This could eliminate the drive and enclosure as well as a few other things.

If you have sata connectors on your mobo (directly, or even via an sata controller), try hooking it up in there and see what happens.

have you made sure you've disconnected it properly from your computer? if not, plug it into a windows comp, and "safely remove" it, then try it again.  you might just want to try this anyway.

Try disabling the esata on your computer (try by OS, and also by BIOS) and try again.

You can try disabling USB (controllers) on your comp in the same fashion, and then re-enable them.

do you have any other USB drives you can check with?

Have you tried clearing the logfiles (assuming NTFS.. I have no idea about other FS's)?

Have you tried sharing the drive while its hooked up to another computer and mounting it like NATS? (dunno if this is possible in ubuntu... but its something I'd eventually try on win).

thats all I can think of off the top of my head.  Nothing really jumps out as probable causes.  just possible... some more so than others.  But, thats all I got :(  Worse case scenario, if you have the equipment to do all that, you'll have it narrowed down a bit.

---

### Post by Bucky Ball on 2009-01-29
> **Gizenshya said:**
> even though you didn't mention it, did you happen to change a setting on the external drive?  Jumper setting on the drive itself, jumper settings on the enclosure, or a switch on/in the enclosure *might* cause something like that.

Nope. The drive is in its enclosure. Haven't taken it out or tampered with the hardware in any way.

> have you tried plugging it into another USB controller (not just another usb slot.. needs to be a different controller)?Yes, no different.

> have you tried a different sata drive in the enclosure?Nope, no point. As mentioned, this drive and enclosure work flawlessly in Windoze XP on this desktop box (which also has the Linux install) and in Vista and Linux on my laptop.

> do you have another sata enclusure to put the drive in?  (could eliminate the enclosure)As per previous, they are pretty well eliminated. Both seem to be in perfect working order except on this install.

> If you have sata connectors on your mobo (directly, or even via an sata controller), try hooking it up in there and see what happens.Done. Nothing.

> have you made sure you've disconnected it properly from your computer? if not, plug it into a windows comp, and "safely remove" it, then try it again.  you might just want to try this anyway.Yes, this is mentioned in my first post from memory.

> thats all I can think of off the top of my head.  Nothing really jumps out as probable causes.  just possible... some more so than others.  But, thats all I got :(  Worse case scenario, if you have the equipment to do all that, you'll have it narrowed down a bit.I have it narrowed down to the fact that this has nought to do with hardware and everything to do with software. I am thinking it was a kernel update that has changed the permission and now I can't change things in 'Authorizations', among other things. You might like to check this thread for a description of that:

[http://ubuntuforums.org/showthread.php?t=1050613](http://ubuntuforums.org/showthread.php?t=1050613)

Thanks for giving it a go.

---

### Post by Bucky Ball on 2009-01-29
The bad news is, try as I might, I couldn't get the USB connection happening.

The good news is, I thought after doing so much screwing around, wonder if something has changed that may allow the eSATA connection? Plugged in the SATA cable, switched on the drive and bang, there she blows! \\:D/

Better transfer rate than USB anyhow and have never been able to get the damn thing working stable in Windoze through eSATA (I bought the drive and enclosure for the higher transfer rate).

That's solved one problem. Now, if I could only work out how to get the permissions to change the 'Authorizations'.

Hold on, just checked and that's fixed too!!!

The major things I did are outlined on this page:

[http://www.freebsd.org/gnome/docs/halfaq.html#q3](http://www.freebsd.org/gnome/docs/halfaq.html#q3)

Particularly the stuff from Step2 on.

Not sure how I fixed my problems but I seem to have. As I say, the USB connection still shows no signs of life. I'll try my dongle, see if that works. I'm predicting it won't.

Hope all this helps someone! :)

---

