---
title: "Possible to ALT+TAB between XP and Ubuntu?"
date: 2006-01-11
forum: General Help
---

### Post by inigmatus on 2006-01-11
Anyone know how to have both XP and Ubuntu running at the same time on the same computer, and easy switching between the two OSes without requiring them to reboot every time?

I used to have a Macintosh Cross Platform machine that I could switch between MacOS and Windows 98 with a hot key. Of course, it required a seperate "PC" card on the machine to run it, but I was curious to know if anything has been developed to facilitate hotswapping between multiple OSes on the same machine without requiring additional hardware or faking it out with an emulator.

or is this an invention for another day?

---

### Post by hillbilly on 2006-01-11
I guess you are looking for something like vmware ! I dont have much idea on this. you can google around or wait for someone else to reply to  your post !!

---

### Post by invalid on 2006-01-11
You could run one with some software like vmware, or I have seen hardware that will actually allow this.

---

### Post by probe45 on 2006-01-11
Windows and Linux are Os-es and not programs. Since they both use there own architecture its impossible to do that. (dont count VMware since thats a programm running on the main OS (linux or windows) and uses lots of resources).

---

### Post by soulestream on 2006-01-11
You dont have full functionality with qemu/vmware but its pretty good

[Ubuntu Howto]("http://ubuntuforums.org/showthread.php?t=84275&highlight=qemu")

[Screenshot]("http://soule.homelinux.com/images/212d.png")

its not ubuntu, but you get the idea.

It can be a resource hog, most newer machines can handle it with no problem

soule

---

### Post by inigmatus on 2006-01-11
Maybe I don't know enough about computer science to figure out why it's impossible, but do OSes reside only in RAM? If so then couldn't an OS be written specicially to split the ram and "guide" additional OSes that would load into that RAM, freezing in a session all the data to restore a previously active OS?

---

### Post by soulestream on 2006-01-11
> Maybe I don't know enough about computer science to figure out why it's impossible, but do OSes reside only in RAM? 

No they dont. If you would like a really destructive demo, boot up XP then reach down and unplug the harddrive. ;) 

The issue is that they really cant share the hardware. Hardware addressing becomes the issue(this includes RAM).Im sure it would be possible, but most OS's have enough trouble keeping up with the system themselves, much less fighting for resources with another. 

The way Xen, Vmware, and Qemu work is they have a base OS, then the create a simulated computer. It has a fake hardrive, fake network, Processor, RAM, everything. Then the program handles requests for real hardware. So in my case for instance when W2K sends image out a video card it goes to qemu as device A, then qemu moves the information to my real video card B. 

soule

---

### Post by inigmatus on 2006-01-11
Makes sense. I completely forgot about hardware addressing.  I guess software emulation is the only way to do it. :(

Thanks for all the responses tho!

---

