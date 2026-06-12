---
title: "Burning TWO distro's on the same disk?"
date: 2012-08-11
forum: Development CD/DVD Image Testing
---

### Post by listerdl on 2012-08-11
Not sure if this is the best place to post but I would like to burn two live distro's on a since disk - 

So basically that would mean burning grub2 as well right?

Any pointers here would be really appreciated thanks

---

### Post by drs305 on 2012-08-11
I have not tried it but if you already have Grub 2 installed and bootable you would most likely be able to mount and run either ISO. Of course, the ISO's have to be written in a bootable format for Grub 2. Not all linux flavors do so, but all the Ubuntu ISOs can be booted from a drive.

Here is the link to the Community Documentation on booting and installing an ISO from Grub 2.
[https://help.ubuntu.com/community/Grub2/ISOBoot]("https://help.ubuntu.com/community/Grub2/ISOBoot")

There are still threads on these forums which I wrote that may have comments you find useful, but the bulk of the information was migrated to the site above (and its parent) a few months ago.

Let us know how it works out.

---

### Post by listerdl on 2012-08-11
thank you my friend

- also, I wonder about the size of the disk - that will be an issue......i.e. depends on the size of the distros being able to fit on the CD/ DVD

Is it better to burn on a CD or DVD - I'm sure this info is elsewhere but if anyone can chime in that would be helpful

---

### Post by drs305 on 2012-08-11
A DVD would be better only because it could hold more - most of the normal Ubuntu releases are 700GB+. The medium really doesn't matter much (other than storage capacity) as Grub just considers it a file to mount. So whether the ISO files are on a CD, DVD, USB drive or the main drive, GRUB will be happy as long as it can find the file and mount it.

There are many ISOs that are smaller and could be included on the CD. For instance, I just booted a SystemRescueCD ISO an hour ago for backing up something. The Boot Repair ISO (at least the Secure Remix one that I have) and SystemRescue disk are both less than 400MB.

Just to clarify, I am not talking about installing multiple ISOs on a single CD - just having the files stored on it.

Added: Also when burning the first ISO that the software burning software leaves the disc open for additional writing.

---

### Post by anderson123 on 2012-10-18
Hi everyone,

Thanks for sharing our view here.
:P:P:P

---

