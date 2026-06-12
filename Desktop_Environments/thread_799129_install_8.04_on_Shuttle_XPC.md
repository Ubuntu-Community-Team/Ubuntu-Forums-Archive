---
title: "install 8.04 on Shuttle XPC"
date: 2008-05-18
forum: Desktop Environments
---

### Post by pablolie on 2008-05-18
i had tried to install ubuntu 8.04 on a shuttle xpc
[http://us.shuttle.com/barebone/Models/sg33g5_pro.html](http://us.shuttle.com/barebone/Models/sg33g5_pro.html)
that was running 7.10, which i had successfully installed of the Live CD after a few attempts.

it is a very cool little system that acts as my home server for music (it runs squeezecenter) and several other central tasks, and i also admit to use it instead of my other desktop simply because i love ubuntu!

the specs are simple, other than the plain vanilla stuff included above, it has
- an intel core duo 2GHz
- 2GB memory
- 160GB hard drive

i was not able to ever get the 64bit or the 8.04 Live CD to install. the system would hang during or after the installation when going for the first restart.

using the Alternate 32bit 8.04 CD, though, brought success by adding
irqpoll 
into the boot options (as the first item), it became clear that the installation process was thus able to circumvent several issues that had affected proceeding before.
just keep also in mind that you need to change the hard drive option on the BIOS away from IDE, 8.04 doesn't seem to like that at all.

the 64 bit version probably should run on this system, but i am happy enough with this version that will enjoy LTS, it's runnig strong.

this is just to document this for other XPC users.

---

