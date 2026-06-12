---
title: "[SOLVED] Hibernate and Suspend failures"
date: 2008-08-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by arijarot on 2008-08-01
Hello,

I have a Dell Vostro 200 Desktop. The suspend and hibernate both fail to resume or even work for that matter. What details are needed in order to figure this out?

Thank you.

---

### Post by funkydan2 on 2008-08-02
Working out why suspend/resume doesn't work isn't easy because the information you need to find out doesn't get stored in the kernel logs.

[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend) is some instructions on how you can start to workout what is going wrong.  If the log output doesn't make sense, post the relevant lines up here and see if someone can help you.

---

### Post by Paul S on 2008-08-02
> **arijarot said:**
> Hello,

I have a Dell Vostro 200 Desktop. The suspend and hibernate both fail to resume or even work for that matter. What details are needed in order to figure this out?

Thank you.

On hardy, suspend doesn't work here with a nvidia using nvidia binary driver or ati card using fglrx binary driver.  I don't think either can be fixed.  The ATI card will suspend with the open source driver "ati" or "radeonhd" using quirks of --quirk-vbestate-restore --quirk-vbemode-restore --quirk-vbe-post.  You can test it out in a terminal with:

sudo pm-suspend --quirk-vbestate-restore --quirk-vbemode-restore --quirk-vbe-post

I understand intel should suspend, but don't have one to test.

Regarding hibernate, it should work even with the nvidia binary driver or ATI with fglrx binary or "ati" or "radeonhd" (with the same quirks).  I believe intel will work too.

For hibernate to work, you have to have a swap partition or logical volume that is at lease the size of your RAM.  i.e., I have 2GB RAM, so my swap is just a bit more (2.1 GB).  Check it as follows:

paul :~$ cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/mapper/vgsda12-lvswapsda12         partition       2101240 659288  -1

If you didn't provide enough swap, you'll have to repartition and make it larger and/or reinstall and make it larger.

hth,

---

### Post by CloudFX on 2008-08-03
You should post a bug report on this using the instructions from [http://help.ubuntu.com/community/ReportingBugs](http://help.ubuntu.com/community/ReportingBugs), as well as adding the necessary debugging files from here: [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI).

---

### Post by arijarot on 2008-08-07
I'm going to close this thread... I've switched back to ubuntu 7.10 as suspend and hibernate works with it.

---

