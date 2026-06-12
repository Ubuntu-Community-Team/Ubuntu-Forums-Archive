---
title: "running ubuntu under xp"
date: 2005-10-22
forum: Desktop Environments
---

### Post by iant on 2005-10-22
i have xp and ubuntu partitions on my laptop which is set up for dual boot. 
i use xp for work but find myself needing to switch to linux occasionally which requires a reboot each time.  i was wondering if anyone knows of a windows application that allows booting of the linux partition so both are running at the same time on the same machine (not sure if that makes sense, hopefully you'll get what i mean).  i've looked at colinux but that seems to require a reinstallation of ubuntu - not really what i want to do. 

any help would be much appreciated.

thanks!

---

### Post by gw90se on 2005-10-22
Are you actually needing to switch to Linux? Or just access something in your home directory? If it is just get into the home directory, there is a program that will allow you to see the partition like a separate drive. I don't remeber the name of it, as it is installed on my laptop at work for the same reason, but you can find it through a search here.

---

### Post by iant on 2005-10-23
[QUOTE=gw90se]Are you actually needing to switch to Linux? Or just access something in your home directory? If it is just get into the home directory, there is a program that will allow you to see the partition like a separate drive. I don't remeber the name of it, as it is installed on my laptop at work for the same reason, but you can find it through a search here.[/QUOTE]

thanks for the reply.  i'm able to mount ext2 and ext3 on xp and access files okay. 
it's actually that i need to run some scripts/executables that are on the linux partition that i'm unable to use on windows.  it's no problem rebooting the machine but just a bit of an inconvenience. so i was looking for something similar to [maconlinux]("http://www.maconlinux.org/") - but where linux runs on top of windows...  any ideas if it's possible?

---

### Post by afonic on 2005-10-23
Hi,

the only thing you can use is a virtual machine like VMWare, I don't think there is another way of running linux on top of windows.

---

### Post by jamyskis on 2005-10-23
If you don't want to fork out the hundreds of dollars associated with VMWare, another choice might be Xen ([http://www.xensource.com)](http://www.xensource.com)). You do pay for what you get though - VMWare is by far the easier to use.

---

### Post by brickbat on 2005-10-23
try colinux. google it.

---

### Post by iant on 2005-11-02
thanks for the replies.

[QUOTE=brickbat]try colinux. google it.[/QUOTE]
perfect. i see now that coLinux *is* able to use a linux [partition]("http://wiki.colinux.org/cgi-bin/ConvertingDistributions"). does anyone know if there is a howto, specific to ubuntu, for using coLinux?

---

