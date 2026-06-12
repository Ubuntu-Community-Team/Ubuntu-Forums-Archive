---
title: "New User question"
date: 2009-05-11
forum: General Help
---

### Post by maflynn on 2009-05-11
Hey,
I'm a new user of ubuntu/kubuntu and I'm still getting my feel for the OS and to that end, I have some basic questions. I've been reading and searching these forums (and google) but I've not really found anything that specifically answers them. I hope this is in the right forum.

1.  Installation of ubuntu (and/or kubuntu).  I have a MacBook Pro, with 4 gigs of ram. I provided about 40 gigs space for the main partition and 8 for the swap partition. Looking at the system monitor, I can see that I'm not doing any swapping (yet).  What's the rule of thumb on creating a swap partition.  How large should it be sized.

2. What applications are available for me to run windows programs. I've heard about wine, but I'm not sure if that's the best solution, or if something else is out there.

---

### Post by Paul41 on 2009-05-11
> 2. What applications are available for me to run windows programs. I've heard about wine, but I'm not sure if that's the best solution, or if something else is out there.

In my opinion the best option would be to find a Linux option that is equivalent to the Windows program. It is usually not hard to do. If you need to run a windows program you will have to use WINE or install Windows on a virtual machine and run the program there. My experience with WINE hasn't been all that great so I personally stay away from it.

---

### Post by kanikilu on 2009-05-11
> **maflynn said:**
> 1.  Installation of ubuntu (and/or kubuntu).  I have a MacBook Pro, with 4 gigs of ram. I provided about 40 gigs space for the main partition and 8 for the swap partition. Looking at the system monitor, I can see that I'm not doing any swapping (yet).  What's the rule of thumb on creating a swap partition.  How large should it be sized.

I don't think there's any "hard and fast" rule about a swap partition. Back in the day when I was using 512MB (or less) of RAM, the general consensus was to use a swap partition that was around 1.5-2.0 times more than the system memory.

Now that I have 4GB of RAM, my swap is only 2GB, and I've yet to need to use it, even while running a VM that I'm giving 768MB of RAM.

It kind of depends on what you are doing, but if you need disk space more than swap, just resize it. If you are running a lot of memory hogs at the same time and can spare the disk space, having a larger swap partition isn't necessarily a problem...

> 2. What applications are available for me to run windows programs. I've heard about wine, but I'm not sure if that's the best solution, or if something else is out there.

What programs are you wanting to use?

The main options available are:

- Wine, either installed from the repositories, or downloaded from WineHQ if you need the bleeding-edge version.

- CrossOver, a commercial product built on wine (there is a free trial though) that has some nice features, but ultimately it's up to you to decide if it's worth the price.

- Virtualization. Depending on what applications you want to run, virtualization (VirtualBox or VMWare) may be an option. It won't work for things like games, but if you have the disk space and RAM (which it seems you do) and Windows, this may be something to look into.

- If all else fails, dual-boot.

I personally use VirtualBox at work for a few applications or tasks that can only be done on Windows (not Wine). At home I dual-boot to be able to play games (not very often these days), and use iTunes (although Amazon MP3 and eMusic have nearly eliminated my need for iTunes).

---

### Post by maflynn on 2009-05-11
> **Paul41 said:**
> In my opinion the best option would be to find a Linux option that is equivalent to the Windows program. It is usually not hard to do. If you need to run a windows program you will have to use WINE or install Windows on a virtual machine and run the program there. My experience with WINE hasn't been all that great so I personally stay away from it.
I would love to but so far there's nothing on par for the program called Qimage.  Its a handly utility to print images, in variety of output sizes and its sizing ability is such that you don't lose too much quality in printing.  That's probably the only windows application I'd really not want to do without.

---

### Post by maflynn on 2009-05-11
> **kanikilu said:**
> 
- Virtualization. Depending on what applications you want to run, virtualization (VirtualBox or VMWare) may be an option. It won't work for things like games, but if you have the disk space and RAM (which it seems you do) and Windows, this may be something to look into.

- If all else fails, dual-boot.

I personally use VirtualBox at work for a few applications or tasks that can only be done on Windows (not Wine). At home I dual-boot to be able to play games (not very often these days), and use iTunes (although Amazon MP3 and eMusic have nearly eliminated my need for iTunes).

I forgot about virtualbox.  I should look into that for programs like Qimage (see my other post). 

I don't see any replacing my OSX software, I just don't think there's applications out there on Linux that could replace the functionality.  No slam or slight on Ubuntu just that I don't think they exist.

I'm still probably going to stick with my OSX software but I can easily see this replacing windows.

---

### Post by DeMus on 2009-05-11
> **maflynn said:**
> Hey,
I'm a new user of ubuntu/kubuntu and I'm still getting my feel for the OS and to that end, I have some basic questions. I've been reading and searching these forums (and google) but I've not really found anything that specifically answers them. I hope this is in the right forum.

1.  Installation of ubuntu (and/or kubuntu).  I have a MacBook Pro, with 4 gigs of ram. I provided about 40 gigs space for the main partition and 8 for the swap partition. Looking at the system monitor, I can see that I'm not doing any swapping (yet).  What's the rule of thumb on creating a swap partition.  How large should it be sized.

2. What applications are available for me to run windows programs. I've heard about wine, but I'm not sure if that's the best solution, or if something else is out there.

1)
I also have 4 GB and do not have a swap partition. I also set a variable called vm.swappiness=0 in a file called /etc/sysctl.conf
This way the system will never use swap. With 4 GB you don't need that. Just check your system monitor for a while, especially when using a lot of (heavy) programs and see how much ram you are using.
Linux has a tendency to use as much ram as needed because that's why you have ram: when it's there - use it.
When using swap the whole machine will become slower.

---

