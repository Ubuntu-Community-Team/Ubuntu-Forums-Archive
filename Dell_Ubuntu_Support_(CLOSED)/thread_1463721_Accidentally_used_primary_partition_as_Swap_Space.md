---
title: "Accidentally used primary partition as Swap Space"
date: 2010-04-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Farmzybaby on 2010-04-27
Hi there,

I'm near enough brand new to the Linux scene, and after reading how 'easy' Ubuntu was to install, I thought I'd give it a go.

I'd set up a small 10gig partition to try it on and installed it, and during the install it asked me to allocate a swap space with a very rough description, which I took to mean it would allow me to literally 'swap' files between windows and linux.

As such, I chose my primary 400gig partition which has now because completely inaccessible. I cannot use my Windows 7 disc to retrieve the partition, nor can I reinstall Windows 7 at all. How can I remove this swap space thing, and finally be able to use Windows 7 and my full harddrive again?

Please help! I'm tearing my hair out :(

Thanks in advance.

Ok, so I found the Disk Utility application, which I assume is Ubuntu's equivalent of a partition manager, yet when I change the Swap Space to NTFS, it just says "Modifying Partition" for an age, without any real signs that it's changing ANYTHING.

---

### Post by viralmeme on 2010-04-27
> **Farmzybaby said:**
> during the install it asked me to allocate a swap space .. I chose my primary 400gig partition

You're kidding, right ?

[http://news.softpedia.com/news/Installing-Ubuntu-8-10-97417.shtml](http://news.softpedia.com/news/Installing-Ubuntu-8-10-97417.shtml)

[http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot](http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot)

---

### Post by Farmzybaby on 2010-04-27
> **ymitchell said:**
> You're kidding, right ?

[http://news.softpedia.com/news/Installing-Ubuntu-8-10-97417.shtml](http://news.softpedia.com/news/Installing-Ubuntu-8-10-97417.shtml)

[http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot](http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot)

Obviously I've done it wrong. At this point I want the harddrive back, I don't even care about the files now.

---

### Post by warri0r on 2010-04-28
seems u messed up things totally. Try using the gparted by booting into the live cd. delete the swap partition, format the unallocated space into ntfs and try reinstalling windows 7 into tat if needed.

---

### Post by leonhook on 2010-04-28
you could use the live cd to reinstall ubuntu over writing the current windows 7 and ubuntu installations and then follow the instructions here 
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) 
to install a windows 7 dual boot. or you can install windows 7 and add ubuntu after . the instructions are all listed on the above page. i hope that helps.

---

