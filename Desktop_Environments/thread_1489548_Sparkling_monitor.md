---
title: "Sparkling monitor"
date: 2010-05-21
forum: Desktop Environments
---

### Post by manolomanolo on 2010-05-21
Hi to all.

My monitor is sparkling in Ubuntu 10.04. I suppose it is a driver problem and not a defect of the monitor itself since it is not sparkling on windows.

It happens when both upgrading from 9.10 as when installing 10.04 from scratch.

Any suggestion, please?
Thanks.

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

Kernel 2.6.32-22-generic #33-Ubuntu SMP x86_64 GNU/Linux

---

### Post by manolomanolo on 2010-05-25
It happens with both 3d effects activated or deactivated.

---

### Post by tom4everitt on 2010-05-25
I get that too with some kernels (especially if I install one that is several points ahead of the default one). So perhaps you're just having a problem with that particular kernel build. 

Try installing some older ones (if not already installed)
```

sudo apt-get install linux-image-2.6.32-21-generic linux-image-2.6.32-19-generic

```
and see how they work. 

If it doesn't work you have a greater choice of ubuntu kernels here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)


PS. If you want to include a log, it is generally better to attach a plain text file (.txt), rather than an OpenOffice/Word document. gedit is an excellent text editor, if you want to edit/save a plain text file.

---

### Post by manolomanolo on 2010-05-26
tom4everitt, thanks for your reply.

Thanks for your suggestions. It could be a good choice to install older kernels and see what happens but I am not going to make mess with my system so hope to see what will happen with newer versions.

Actually I already experienced that everything was good with previous kernels since I did not have this kind of problem when I was on Karmic. So it could be good for developers to take a look at this issue and try to fix it, just in case.

As for the attachment, at the beginning I have been trying to attach it in .txt format but the size of the .txt exceded the maximum uploadable for that file type. On the other hand, this forum allows larger uploads for .doc files so I was obliged to choose that format. :(

Any other experiencing the same issues with monitor?

Thank you.

---

### Post by tom4everitt on 2010-05-27
Okay, I see. I wouldn't say installing an older kernel is messing with your system. It will just coexist with your current kernel, being chooseable at boot. If you don't want it anymore, you can just remove it again with

sudo apt-get remove --purge linux-image-2.6.32-xx-generic


Funny about the the attachments limits :P

---

