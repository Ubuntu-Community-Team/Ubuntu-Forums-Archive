---
title: "Compiling New Kernel for ndiswrapper use"
date: 2005-04-20
forum: Desktop Environments
---

### Post by Mat10 on 2005-04-20
Hi folks,
Seem to be having trouble placing a newer kernel source so that I may use nidiswrapper 1.1  and wireless WMP11 V4 InProComm chipset.

At this point I have a stack of printed HOWTOs for compiling a new kernel from source.  The problem is after following all the instuctions I get to the point of using a make mrproper command and get back errors.  I think the problem is the default install of the Ubuntu 2.6.10.5-386 does not install the necessary compile tools needed.  Am I wrong here.

If anyone has the correct source of information to upgrade the kernel to 2.6.11.7 I would appreciate the info.  No reason to install a new kernel other than the fact the WMP11 V4 does not work without nidiswrapper.

This Ubuntu has a very nice and beautiful desktop, not overbearing to old eyes.

Thanks

Tom

---

### Post by accuser on 2005-04-20
Do you need to compile a new kernel to use this ndis driver with the ndiswrapper tool? ndiswrapper support is available with Ubuntu 5.04 (Hoary), or do you just want to bleed on the edge? :-)

---

### Post by Mat10 on 2005-04-20
It looks like I have to use it or else do without Internet.  Other distros are the same and use the same 0.6 ndiswrapper which has limited drivers included.  I'm not really interested in bleeding edge, I do care to learn once and for all to make a new kernel config.  If you use Linux you need to know these things and the infomation out there for building and compiling kernels is a little misleading if you take into consideration the different tools each distro installs.  It's very hard for noobs like myself to sort out the right info and use the right one for the distro I'm using.  I know I need to put my new source into the /usr/src folder and know how to extract the new kernel and all that, after that things just don't seem to follow the written howto's at least not for me.

Tom

---

