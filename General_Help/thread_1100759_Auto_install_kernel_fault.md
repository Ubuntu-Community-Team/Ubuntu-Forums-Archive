---
title: "Auto install kernel fault"
date: 2009-03-19
forum: General Help
---

### Post by MisterMark on 2009-03-19
I bought recently 4GB memory for my laptop running Ubuntu 8.10 Linux. As 32bits can't cooperate with that amount of memory i searched the web and found out that the server kernels had HIGHMEM_64G enabled. So my 32bit would be able to run with the whole 4GB of memory. I installed a server kernel for my desktop Linux it all worked fine except from some applications, there four i decided to go for the other option on running 4GB of memory on a 32bits, compile your own kernel with HIGHMEM_64G enabled. I configured this kernel and created the .deb files. After that i didn't had enough time to install that kernel and shut down my system.

Now the real problem comes up:
When i booted my system next morning at booting the systems tells me dkms is auto installing the kernel. (i couldn't write down the exact message) The kernel i booted was a regular kernel (2.6.27-14) which i run for about 4 days without any trouble. But after that auto install of the kernel the system is acting strange, per example: Firefox, hellanzb, amsn and other programs can't seem to find there config files and the firefox profile is also missing for firefox. When i browse to my personal folder it all seems oke and all maps seemed unchanged, also my desktop icons and panels are present.

Can someone please help me restoring this back to normal. I'am not that experienced in Linux, although i run Linux on my machine for about a half a year.

---

### Post by fieroboom on 2009-03-19
> **MisterMark said:**
> I bought recently 4GB memory for my laptop running Ubuntu 8.10 Linux. As 32bits can't cooperate with that amount of memory i searched the web and found out that the server kernels had HIGHMEM_64G enabled. So my 32bit would be able to run with the whole 4GB of memory. I installed a server kernel for my desktop Linux it all worked fine except from some applications, there four i decided to go for the other option on running 4GB of memory on a 32bits, compile your own kernel with HIGHMEM_64G enabled. I configured this kernel and created the .deb files. After that i didn't had enough time to install that kernel and shut down my system.

Now the real problem comes up:
When i booted my system next morning at booting the systems tells me dkms is auto installing the kernel. (i couldn't write down the exact message) The kernel i booted was a regular kernel (2.6.27-14) which i run for about 4 days without any trouble. But after that auto install of the kernel the system is acting strange, per example: Firefox, hellanzb, amsn and other programs can't seem to find there config files and the firefox profile is also missing for firefox. When i browse to my personal folder it all seems oke and all maps seemed unchanged, also my desktop icons and panels are present.

Can someone please help me restoring this back to normal. I'am not that experienced in Linux, although i run Linux on my machine for about a half a year.

Actually, 4GB *is* the 32 bit OS system limitation, so there's no need for you to have the HIGHMEM_64G enabled. Plus, being a laptop, all of your video memory is going to be mapped from that 4GB, so your OS will actually see less than 4GB. I would recommend reinstalling vanilla Ubuntu 32 bit, and call it a day.
:D
-Paul

---

### Post by joey-elijah on 2009-03-19
> **fieroboom said:**
> I would recommend reinstalling vanilla Ubuntu 32 bit, and call it a day.
:D
-Paul

Surely if they're going to do a clean install they should opt for 64bit instead of 32bit? The whole issues have stemmed from not wanting to install 64bit when that is the only way to best use a x64 compatible processor and more than 4GB memory (including video). 

I've been using x64 bit ubuntu for the last year and i've not had a single problem or incompatiblity that wasn't easily solved.

---

### Post by MisterMark on 2009-03-19
> **fieroboom said:**
> Actually, 4GB *is* the 32 bit OS system limitation, so there's no need for you to have the HIGHMEM_64G enabled. Plus, being a laptop, all of your video memory is going to be mapped from that 4GB, so your OS will actually see less than 4GB. I would recommend reinstalling vanilla Ubuntu 32 bit, and call it a day.
:D
-Paul

By enable PAE ([WIKI]("http://en.wikipedia.org/wiki/Physical_Address_Extension")) it is possible to use more memory, up to 64GB. The system recognized my 4GB (and worked with it and addressed it) when running the server kernel and also running the custom kernel with HIGHMEM_64G enabled. I know it is possible as i saw it with my own eyes running that server kernel.

But that isn't my question. The system seems to get lost of my personal directory after that auto install of the kernel at boot, but actually it is physical available and also there seems nothing wrong with it. But a lot of programs loosed there configurations and profiles etc. that are normally stored in the personal directory.

---

