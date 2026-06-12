---
title: "USB Key Not Being Read by Jaunty"
date: 2009-06-25
forum: General Help
---

### Post by Sef on 2009-06-25
I installed Jaunty on a friends Inspiron 6000; however, her 8 gb usb key is not being read. (It worked under XP just fine.)  It is detected under lsusb.  I tried two other usb keys, and they both work.  What can I try to get her usb key to work?

---

### Post by Divider on 2009-06-25
by key do you mean flash drive?

---

### Post by Sef on 2009-06-25
> by key do you mean flash drive?


Yes, it is another name for it.

---

### Post by Divider on 2009-06-25
Just wanted to make sure, It doesn't recognized it at all?'

 do a before and after:

```
sudo cat /proc/partitions
```

does a new /dev/XXX# show up?

If it does you might have the "windows remove bug" were you have to safely remove it from windows before it will show up.

---

### Post by mcduck on 2009-06-25
> **Sef said:**
> I installed Jaunty on a friends Inspiron 6000; however, her 8 gb usb key is not being read. (It worked under XP just fine.)  It is detected under lsusb.  I tried two other usb keys, and they both work.  What can I try to get her usb key to work?

Have you checked what file system the USB key has now? A 8GB drive could pretty well be formatted as exFAT, which as far as I know isn't yet supported by Linux..

If that's the case reformatting into some supported file system would of course solve the problem.

---

### Post by Sef on 2009-06-25
> Have you checked what file system the USB key has now? A 8GB drive could pretty well be formatted as exFAT, which as far as I know isn't yet supported by Linux..

No I have not.   I will check that.  What would be the best command to do that or should I just use GParted for that?

---

### Post by Divider on 2009-06-25
> **Sef said:**
> No I have not.   I will check that.  What would be the best command to do that or should I just use GParted for that?

I myself use fdisk, but i would use what you are familiar with.

---

### Post by mcduck on 2009-06-25
> **Sef said:**
> No I have not.   I will check that.  What would be the best command to do that or should I just use GParted for that?

I'm not sure how well any Linux tool detects exFAT at this point, and as I haven't got any device using it I can't even test. 

But I suppose if the drive is formatted with any supported file system GParted or fdisk should detect it, and if they aren't able to detect the filesystem it's most likely exFAT.. ;)

I'd try this first:
```
sudo fdisk -l
```

edit: Come to think of it, what I'd *really* do is first open a terminal and run "tail -f /var/log/kern.log", and then plug in the drive to see if the system detects the actual device itself. And after that, if the kern.log didn't give information about the filesystem, run "sudo fdisk -l" to see if that provides the information. If not, I'd assume it's exFAT and format it into FAT.

---

### Post by BambooClaw on 2009-07-04
I had trouble with USB flash drive and CF card reader not mounting. The problem was that the module usb_storage was not being loaded by the OS. So run
sudo modprobe -i usb_storage
before plugging in the drives and see if they are now recognised. 

If so then a more permanent solution is to add usb_storage to the end of your /etc/modules file.

For the record, USB flash drive reading was working fine before I upgraded  to Jaunty, during Jaunty I was having problems.

---

### Post by Onesimus on 2009-07-18
BambooClaw:  Many Thanks - this works now.

---

