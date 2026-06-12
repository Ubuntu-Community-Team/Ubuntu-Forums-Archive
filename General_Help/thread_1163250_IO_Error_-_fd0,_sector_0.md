---
title: "I/O Error - fd0, sector 0"
date: 2009-05-18
forum: General Help
---

### Post by Roasted on 2009-05-18
I use FOG, a Linux based cloning solution on top of Ubuntu 9.04. Now, this is working with Linux kernels and all so I assume I can be helped here.

Despite me getting these errors with 1 particular computer, the computer still images just fine. I'm just wondering what this particular error (seen in the subject) means, and how it works, etc.

Can anybody offer any info in this department?

---

### Post by Roasted on 2009-05-25
Any idea? I'm pretty sure this is a Linux thing since FOG is linux based, so I was just curious what the nature of that error was, because even when I get the error the imaging process still works fine.

---

### Post by thedohman on 2009-05-28
Hi

I have the same error.  I get:
```

[22.813835] end_request: I/O error, dev fd0, sector 0
[35.877830] end_request: I/O error, dev fd0, sector 0
[35.877869] Buffer I/O error on device fd0, logical block 0

```

the end_request line is every 13 seconds, and every other one is followed by the Buffer I/O line until the last one at 404.570280.  the boot continues at 422 with "udev: starting version 141", and everything seems to be fine after that 6-7 minute delay.

Xubuntu 9.04, Live USB created with PORTABLELNX.  

I know it's trying to read the floppy drive, only it's a laptop and doesn't have a floppy drive.

I found a reference to the same error on the redhat bugtracker (here: [Bug ID 491230]("https://bugzilla.redhat.com/show_bug.cgi?id=491230")), but it turns out to be a kernal with compiled in floppy driver (not a module, as is norm), or 
> could be caused by lvm or by specifying root (in the kernel cmdline, through grub.conf) as UUID= or LABEL=, lvm will scan all block devices (although it may skip floppies) for physical volumes and specifying root as UUID= / LABEL= will cause nash to scan all block devices to find the UUID / LABEL.

You could try working around this by specifying your root= as /dev/.... in grub.conf


My grub.conf uses (hd0,0) so that shouldn't be an issue.  Since it's a live install, I can't use /dev/... anyway as it may show up different on other computers. (Someone correct me if I'm wrong! ;))

Live CD boots fine without the issue (but the CD drive has dust issues, so it really only boots half the time in this computer, hence the use of the USB drive.)

I'll reboot now to see if there is an option in BIOS to disable the (nonexistant) floppy.

---

### Post by cariboo on 2009-05-28
/dev/fd0 is a floppy drive, if you are getting the error and you don't have a floppy drive, disable it in the bios and you shouldn't have any more problems.

---

### Post by Roasted on 2009-05-28
> **cariboo907 said:**
> /dev/fd0 is a floppy drive, if you are getting the error and you don't have a floppy drive, disable it in the bios and you shouldn't have any more problems.

Ahhhh! Makes perfect sense. Thank you! I knew it wasn't anything too important if the imaging process was still working fine but I was still curious to know exactly what it was...

Thanks again.

---

### Post by Roasted on 2009-06-30
Just to bump for the sake of me understanding this, if I wanted to get the floppy drive working, how could I get it working? I'm not running Linux on these systems but what would be the protocol to get a floppy drive running with a computer having this error?

---

