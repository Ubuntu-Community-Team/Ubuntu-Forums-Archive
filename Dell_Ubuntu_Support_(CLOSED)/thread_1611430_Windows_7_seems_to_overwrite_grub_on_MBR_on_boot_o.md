---
title: "Windows 7 seems to overwrite grub on MBR on boot on Inspiron 1012"
date: 2010-11-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by otakuj462 on 2010-11-01
Hi,

I just set Ubuntu up on my Dell Mini Inspiron 1012. I did so in what I think is the normal way: I shrank the Windows 7 partition from within Windows 7, and installed Ubuntu on the 150GB new free space. As usual, grub was installed to the MBR, and I was able to boot into Ubuntu and Windows 7 normally. Unfortunately, however, it seems that every time I boot into Windows 7, the MBR is overwritten with something stupid, so that I can no longer boot from the hard disk the next time I reboot the computer. Each time, I need to restore grub to the MBR by booting off of an Ubuntu installation USB, and running grub-setup. 

If anyone has any idea as to what might be causing this behaviour, and how I could fix it, I'd greatly appreciate it if you could let me know. Thanks!

---

### Post by wilee-nilee on 2010-11-01
This may be of interest to you, it sounds like you understand how to reload the mbr, but feel free to ask.
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

It appears this is probably the culprit here.

---

### Post by otakuj462 on 2010-11-02
Thanks for the quick reply. From the article you linked to, it sounds like uninstalling Dell DataSafe is the correct solution.

---

### Post by ktoepke on 2010-11-06
I had the same problem for a while...after I uninstalled all of the Dell utilities in Win7, it stopped happening.

---

### Post by mpsz on 2010-11-10
Hi, I had the same problem.

Just uninstall Dell Datasafe software.
That's what causes the problem.
Regards.

---

### Post by Swashbunglar on 2010-12-04
I'm in this unfortunate situation with Windows 7 Ultimate overwriting and killing my mbr and grub. If I run windows once, I have to run Ubuntu live and fix grub at reboot.
Now the very unfortunate part is, I don't have Dell nor do I have Datasafe anywhere on my pc.
I've even tried the trick of rebuilding the mbr, and then rebuilding grub. But alas this also fails.
I have absolutely no clue as to what is making windows overwrite the mbr.

note: I can load safe mode windows without an overwrite.

Thanks in advance for any tips, tricks, or advice.

---

### Post by matt_symes on 2010-12-04
Hi

One thing you could do is to use msconfig and disable all the start up applications and services. You can then fix grub.

You can then enable them one by one, rebooting after each until grub is overwritten. Then the last one you enabled is the one causing the problem. Time consuming but it should find the problem application or service.

Failing that you could post a list of all your start up applications and services on here. Some one might be able to identify the application causing the problem.

Kind regards

---

### Post by Swashbunglar on 2010-12-04
You know.. I have no idea why that wasn't the first thing I did. I think the holidays have my head full of mush! lol
Once I read that I had an ADUH moment. lol

Thanks for the quick reply, I'll try that and report back if I find the culprit.

---

### Post by oldfred on 2010-12-04
It is not just Datasafe but a variety of win7 (and just some win) software.

Writes to MBR-----------------------------------
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
[http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable](http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable)
In Windows 7, I had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

---

### Post by Swashbunglar on 2010-12-04
Well I found one more to add to the list.

IORAIDManager (service)

It's added when you install software for the IO Crest SATA II Raid Controller PCI-E Card.
I think you only need it if you boot from a drive attached to that card. Which I don't, so I disabled it and I have windows and ubuntu playing nicely now.

Thanks for the input!

---

