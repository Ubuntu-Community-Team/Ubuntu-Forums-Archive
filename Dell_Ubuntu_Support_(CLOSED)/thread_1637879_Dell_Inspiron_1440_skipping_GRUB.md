---
title: "Dell Inspiron 1440 skipping GRUB"
date: 2010-12-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TheRaiderNation on 2010-12-05
Hi, I'm new to the forums and I'm here for some problems I'm having with my Dell Inspiron 1440.

So, just a quick summary of what I did, the first time I installed ubuntu 10.10 was with a flash drive, it installed correctly. I was able to use bootloader and boot into Ubuntu and Windows.

To make a long story short, after encountering some problems and doing some research I found that some dell software would override the MBR whenever I booted into Windows 7 and give me the "No Modules found" error. So I recovered Windows 7 using the repair disk that came with the laptop. After that finished I deleted the programs that were supposedly responsible for overriding the MBR. Then I [successfully] installed Ubuntu 10.10 again, this time using an installation disk that I burned.

My problem now is that instead of booting to grub then booting the selected OS. My laptop boots directly into grub. I've been searching the fourms, googling for a solution, but I can't seem to get anything going. Any one have any solutions for this problem?

idk if this is of any help, but grub-install -v returns:
1.98+20100804-5ubuntu3

Thanks in advanced.
----------EDIT---------------
Figured it out, got grub to  show up, I now have another problem with grub:
[http://ubuntuforums.org/showthread.php?p=10203890#post10203890](http://ubuntuforums.org/showthread.php?p=10203890#post10203890)

---

