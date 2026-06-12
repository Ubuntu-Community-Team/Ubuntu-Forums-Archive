---
title: "Not showing full 7GB of Memory"
date: 2009-03-14
forum: General Help
---

### Post by ilamythest on 2009-03-14
I just bought my husband a new computer. It's a HP with an AMD Phenom quad core processor, 640 GB hard drive, and 7 GB of DDR2 Ram. Running Ubuntu 8.10. System runs beautifully, except it's only showing 3.34 GB of ram. He checked the bios and it's showing the full 7GB. He's read through the forums trying to find the solution but can't seem to find anything. Can anyone with a little more computer savy than what we possess shed some light on this problem? Thanks in advance.

---

### Post by LegendofTom on 2009-03-14
If you are running a 32-bit OS, the cache size isn't big enough to show all of your 7 gigs.  If you want to utilize your 7 gigs of ram and that phenom quad, try the 64-bit version of 8.10.

---

### Post by jwbrase on 2009-03-14
> **ilamythest said:**
> I just bought my husband a new computer. It's a HP with an AMD Phenom quad core processor, 640 GB hard drive, and 7 GB of DDR2 Ram. Running Ubuntu 8.10. System runs beautifully, except it's only showing 3.34 GB of ram. He checked the bios and it's showing the full 7GB. He's read through the forums trying to find the solution but can't seem to find anything. Can anyone with a little more computer savy than what we possess shed some light on this problem? Thanks in advance.

Most likely you installed the 32 bit instead of the 64 bit version of Ubuntu.

---

### Post by unutbu on 2009-03-14
Open a terminal (Applications>Accessories>Terminal) and type
```
getconf LONG_BIT
```

If it returns 32 then you are running the 32-bit version of Ubuntu 8.10.
If it returns 64 then you are running the 64-bit version of Ubuntu 8.10.

The 32-bit version of Ubuntu (or any operating system, including Windows) will only recognize at most 4GB of RAM. Less than 4GB of RAM is available because other pieces of hardware, such as video and DMA also reserve memory space. (See
[http://fixunix.com/ubuntu/506776-32-bit-os-4-gb-limit.html](http://fixunix.com/ubuntu/506776-32-bit-os-4-gb-limit.html))

One way to utilize the full 7GB of memory would be to install the 64-bit version of Ubuntu. Go to [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and click the "64bit version" button near the bottom of the page.

---

### Post by sdennie on 2009-03-14
As others have said, it sounds like you are using a 32 bit OS.  However, it's not accurate that you'll need to use a 64-bit OS (though, you may still want to).  See: [ Ubuntu with 4GB+ of memory]("http://ubuntuforums.org/showthread.php?t=855511")

---

### Post by hyperdude111 on 2009-03-14
You are most likely using the 32 bit version just download the 64 bit one.

---

### Post by rlj1965 on 2009-03-14
A few people have suggested you install the 64bit version of Ubuntu to gain acess to the extra ram in your husband's system. I am currently running Ubuntu 8.10 32bit. I have 4gb of Ram and my Ubuntu only shows three and change ram being accessed. I could upgrade to the 64bit version to gain access to the extra ram. I have decided to stay with 32bit because basically... everything works well. Why possibly fuss up my system by trying to install a different version of my OS when everything is fine. I guess it really depends on what your husband plans to use the system for. You should read the following thread before proceeding to just install the 64bit version of Ubuntu. Many people have offered pros and cons. Many have no issues with 64bit and some do. I think the real decision is based on what your hub intends to use his machine for and if he would gain an advantage by installing the 64bit version. Here is a decent link that may help to alter his decision... [http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

Good Luck

rlj1965

---

### Post by 3rdalbum on 2009-03-14
Firstly, I'll just say that Ubuntu will run very nicely with 3 gigabytes of RAM addressable. For ordinary desktop use, I'm not even sure you'd be able to use more than about 2 gigabytes of RAM for cache, much less actively use it. Read the "permanent articles" on my blog for the ridiculous test I did :-)

I installed 4 giagbytes of RAM and switched to 64-bit Ubuntu, and I'm having no troubles at all. If I was intending to install 32-bit binary-only programs I might have to track down some 32-bit libraries, but there is a program called Getlibs that can automatically do most of that for me.

A lot of negative attitudes toward 64-bit operating systems come from Windows, and the rough transition that the Windows platform is having. I can assure you that 64-bit Ubuntu is 97% indistinguishable in operation from its 32-bit counterpart.

---

### Post by Yellow Pasque on 2009-03-14
Even if you're running 32-bit Ubuntu, you can access 7GB of RAM by installing/using the server kernel. It has PAE and can see up to 64GB of RAM.

---

### Post by dcstar on 2009-03-15
> **Temüjin said:**
> Even if you're running 32-bit Ubuntu, you can access 7GB of RAM by installing/using the server kernel. It has PAE and can see up to 64GB of RAM.

"Access" in 32 bit means that the 4GB RAM segments can only be used by individual processes, so while it is better than nothing only a full 64 bit system can use >4GB RAM to maximum efficiency.

I, along with many (many) other Ubuntu users, have been using 64 bit without any issues for quite a while now, there is little excuse not to run the OS that utilises your hardware to maximum capacity now days.

---

### Post by Yellow Pasque on 2009-03-15
dcstar, I agree with you 100% (I'm running 64-bit Ubuntu myself, even though I currently have only 2 GB of RAM :P )
I was simply throwing out the option of running the server kernel in case the OP didn't want to reinstall.

---

