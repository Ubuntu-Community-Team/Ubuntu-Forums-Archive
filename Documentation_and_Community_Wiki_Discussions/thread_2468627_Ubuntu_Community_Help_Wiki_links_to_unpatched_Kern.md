---
title: "Ubuntu Community Help Wiki links to unpatched Kernel/BIOS corruption"
date: 2021-11-05
forum: Documentation and Community Wiki Discussions
---

### Post by delgonna on 2021-11-05
[https://help.ubuntu.com/community/Boot-Repair?](https://help.ubuntu.com/community/Boot-Repair?)

Links to 32bit iso which still contains Intel SPI bug in kernel causing BIOS corruption in a small number of machines.

[https://bugs.launchpad.net/boot-repair/+bug/1734147](https://bugs.launchpad.net/boot-repair/+bug/1734147)

The wiki page is immutable so I'm unable to add a warning. Is there anyone in the community able to add a cautionary note?

---

### Post by grahammechanical on 2021-11-05
I have tried several times and I cannot see where in the community wiki page on Boot Repair that there is a link to a 32 bit ISO image that has a Linux kernel with the Intel SPI bug. I used to have permission to edit community Wiki pages. I do not have that permission any more but to place a warning on that page or to remove a link to an ISO image download site a person would need to know specifically the line in the instructions that need to be edited. You do not give this information.

As regards the bug in the Linux kernel a fix has been in place since the second week of December 2017. The fix was made within days of the bug being reported. Besides which the only version of Ubuntu that may have the buggy kernel is Xenial = 16.04 and that would have had several Kernel updates since 2017.

This bug was reported yesterday against boot repair and I cannot understand why. The person who reported the bug failed to add any comments. As far as I know Boot Repair does not install Linux kernels. A typical Boot Repair repair would be to reinstall the Grub boot loader. There is an option to "Purge kernels then reinstall last kernel (beta)". I do not know how that works. It may download the kernel from a Ubuntu site. In which case the replacement kernel would have been patched with the bug fix.

Ubuntu developers have stopped providing 32 bit versions of Ubuntu. Any ISO image built after 22/12/2017 would have a patched kernel. Or a newer kernel that does not have the bug. Any ISO image with the 4.14 kernel would not have had this bug in the Linux kernel.

Regards

---

### Post by deadflowr on 2021-11-05
*Thread moved to **Documentation and Community Wiki Discussions***

---

### Post by guiverc on 2021-11-06
> **grahammechanical said:**
> I have tried several times and I cannot see where in the community wiki page on Boot Repair that there is a link to a 32 bit ISO image that has a Linux kernel with the Intel SPI bug.

I too had a look for it, and couldn't find it.  I looked using the normal readers view of the page, then entered edit mode looking for links to ISO or a direct download link and didn't find any.

You'll need to provide the text around the issue as I too didn't find it.

The Ubuntu ISOs that had the issue I believe we all re-spun & new not-impacted ISOs exist on Ubuntu's site for download.

---

### Post by delgonna on 2021-11-06
[https://help.ubuntu.com/community/Boot-Repair?](https://help.ubuntu.com/community/Boot-Repair?)

Has a link to "[Boot-Repair-Disk]("http://sourceforge.net/p/boot-repair-cd/home")" which goes to the sourceforge project.

From here if you click on "Files" 2 ISO images are available for download, the 32bit version of boot-repair-disk (last modified 2017-10-29) contains unpatched Kernel from Ubuntu 17.10. A Live session of this image with unpatched Kernel is able to corrupt the BIOS of certain computers.

[https://www.omgubuntu.co.uk/2018/01/ubuntu-17-10-lenovo-fix](https://www.omgubuntu.co.uk/2018/01/ubuntu-17-10-lenovo-fix)

As seen in article Ubuntu 17.10 was patched and re-released 2018-01-11.

Unfortunately this isn't just a theory I used 32bit  boot-repair-disk on Fujitsu Q584 tablet, it's no longer able to boot  from internal eMMC or USB. BIOS cannot save changes. "Fix" detailed at  [https://bugs.launchpad.net/boot-repair/+bug/1734147](https://bugs.launchpad.net/boot-repair/+bug/1734147) requires a working  OS to apply.

---

### Post by guiverc on 2021-11-06
As I see it, that's a problem that needs to be corrected on the sourceforge site; as no Ubuntu site refers to 17.10 (it was *faulty*) and quickly re-released & replaced as 17.10.1, but that reached [EOL back in mid-2018]("https://fridge.ubuntu.com/2018/07/19/ubuntu-17-10-artful-aardvark-end-of-life-reached-on-july-19-2018/") anyway & isn't listed on any download site either (*except for [old-releases.ubuntu.com]("http://old-releases.ubuntu.com/releases/17.10/")*[URL="http://old-releases.ubuntu.com/releases/17.10/"])

[/URL]

---

### Post by delgonna on 2021-11-06
I mostly agree but the Official Ubuntu Help: [https://help.ubuntu.com/community/Boot-Repair?](https://help.ubuntu.com/community/Boot-Repair?) could do with a warning, Obviously the problem is incredibly rare but it's concerning others could also brick their system following the Ubuntu Community Support Wiki.

---

### Post by guiverc on 2021-11-06
I've added a [warning]("https://help.ubuntu.com/community/Boot-Repair#A1st_option_:_get_a_disk_including_Boot-Repair") and provided a link to this thread.

You can have a look & see if you're happy. Sorry I didn't credit you in edit (*didn't think of it till too late*) including a link to here only..

**Thank you for reporting the issue**, and helping make our Ubuntu documentation better.

FYI: Later 32-bit ISO were produced by Ubuntu until at least [August-2020]("https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/"); as I'm involved in QA-testing and recall using my pentium 4/d/M devices for it; also in 18.10 & 19.04 (*alpha*) for two *flavors* (*though they were earlier*).

---

### Post by delgonna on 2021-11-06
> **guiverc said:**
> I've added a [warning]("https://help.ubuntu.com/community/Boot-Repair#A1st_option_:_get_a_disk_including_Boot-Repair") and provided a link to this thread.

You can have a look & see if you're happy. Sorry I didn't credit you in edit (*didn't think of it till too late*) including a link to here only..

**Thank you for reporting the issue**, and helping make our Ubuntu documentation better.

FYI: Later 32-bit ISO were produced by Ubuntu until at least [August-2020]("https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/"); as I'm involved in QA-testing and recall using my pentium 4/d/M devices for it; also in 18.10 & 19.04 (*alpha*) for two *flavors* (*though they were earlier*).

Thanks, that's better worded than I would have managed if I'd been able to edit wiki page. Hopefully boot-repair developer will patch kernel soon.

---

