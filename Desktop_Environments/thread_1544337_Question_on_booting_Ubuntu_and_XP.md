---
title: "Question on booting Ubuntu and XP"
date: 2010-08-02
forum: Desktop Environments
---

### Post by semmtexx on 2010-08-02
I have a desktop running one hard drive with XP as the OS and another seperate hard drive with Ubuntu (latest edition) as the OS.  I was wondering if there was a way to boot into the Ubuntu without restarting the pc.  Also, as I am typing this question I am sorting thinking there is no way to do this but I figured I would ask.  Maybe some kind of application that could do this?

---

### Post by kio_http on 2010-08-02
No, you cannot run multiple physical OS'S on normal computers. Some server equipment can though. The OS needs to start its own initialization and since the Windows platform is different from the linux platform this is not possible.

However you can run both OS's simultaneously. See visualization. The OS you boot + the secondary OS that runs within a Window.
[Virtualbox]("http://www.virtualbox.org/")
[Virtual PC]("http://www.microsoft.com/windows/virtual-pc/")

If you just want to share files between the two OS's Ubuntu can access Windows's NTFS file system. But this does not work vice-versa.

---

### Post by Mi11z on 2010-08-02
> **semmtexx said:**
> I have a desktop running one hard drive with XP as the OS and another seperate hard drive with Ubuntu (latest edition) as the OS.  I was wondering if there was a way to boot into the Ubuntu without restarting the pc.  Also, as I am typing this question I am sorting thinking there is no way to do this but I figured I would ask.  Maybe some kind of application that could do this?

I think what your after is a virtualization tool, in other words it's basically a program which run's as a guest os inside a host os. 

seen here VMware:

[IMG]http://pcwin.com/media/images/screen/VMware_Workstation_Windows_120537.jpg[/IMG]

and for gnu/linux VirtualBox:

[IMG]http://www.g4g.it/g4g/wp-content/uploads/2008/01/virtual_box_02.jpg[/IMG]

That's the only real way i know of for running two OS's together at the same time without restarting/rebooting the fact that you have two different OS's on two different hard drives makes no difference unless you have two computers.

---

### Post by semmtexx on 2010-08-08
Awsome!  Thanks for the tips!

---

