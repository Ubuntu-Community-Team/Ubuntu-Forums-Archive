---
title: "[SOLVED] How to apply patch"
date: 2008-10-17
forum: Desktop Environments
---

### Post by techie_india on 2008-10-17
Hi,

I m a newbie for driver installation.

I have to install the driver for the IC TI USB 3410/5052 

In that release note say that this file should be there **"drivers/usb/serial/usb-serial.h"**

But I was not able to find it.

There is a regarding for not founding it :

**_[https://lists.ubuntu.com/archives/kernel-bugs/2008-January/031282.html](https://lists.ubuntu.com/archives/kernel-bugs/2008-January/031282.html)_**

I m not able to apply the patch which is given.

Can anybody help me how to apply that patch.

PS: I was not able to find the serial.h in the directory /usr/include/linux/usb instead it was in the /usr/include/linux

Thanks and Regards
Anshuman Srivastava

---

### Post by lisati on 2008-10-17
> **techie_india said:**
> Hi,

I m a newbie for driver installation.

I have to install the driver for the IC TI USB 3410/5052 

In that release note say that this file should be there **"drivers/usb/serial/usb-serial.h"**

But I was not able to find it.

There is a regarding for not founding it :

**_[https://lists.ubuntu.com/archives/kernel-bugs/2008-January/031282.html](https://lists.ubuntu.com/archives/kernel-bugs/2008-January/031282.html)_**

I m not able to apply the patch which is given.

Can anybody help me how to apply that patch.

PS: I was not able to find the serial.h in the directory /usr/include/linux/usb instead it was in the /usr/include/linux

Thanks and Regards
Anshuman Srivastava
From the terminal (it's on the Applications->Accessories menu) type in ```
locate usb-serial.h
```

If there's a copy on your system, it should show up in the output from the locate command.
Feel free to let us know how you get on.

---

### Post by techie_india on 2008-10-17
Hi,
I m not able to find the usb-serial.h.

When I run the command as given in the link below:

[https://lists.ubuntu.com/archives/kernel-bugs/2008-January/031282.html]("https://lists.ubuntu.com/archives/kernel-bugs/2008-January/031282.html")

The command is this :
**git log -p a969888ce91673c7f4b86520d851a6f0d5a5fa7d commit a969888ce91673c7f4b86520d851a6f0d5a5fa7d**

It give the following error :
**fatal: Not a git repository**

Can anybody tell how to add the repository


Thanks and regards
Anshuman Srivastava

---

### Post by techie_india on 2008-10-18
Is there not any way to solve this problem , of having the usb-serial.h
in the ubuntu system.

Anshuman

---

### Post by cicatrix1 on 2008-10-18
You do not want to run that git command.  I checked your link.  That command was provided for reference to show it's output.  git is a version control system, and the author was just using it as a shorthand way to say "I commited this code with these comments."


> **techie_india said:**
> Hi,
I m not able to find the usb-serial.h.

When I run the command as given in the link below:

[https://lists.ubuntu.com/archives/kernel-bugs/2008-January/031282.html]("https://lists.ubuntu.com/archives/kernel-bugs/2008-January/031282.html")

The command is this :
**git log -p a969888ce91673c7f4b86520d851a6f0d5a5fa7d commit a969888ce91673c7f4b86520d851a6f0d5a5fa7d**

It give the following error :
**fatal: Not a git repository**

Can anybody tell how to add the repository


Thanks and regards
Anshuman Srivastava

---

### Post by techie_india on 2008-10-20
Thanks for clarifying the doubt about patch.

Can anybody help me to get the file usb-serial.h

Thanks and regards
Anshuman Srivastava

---

### Post by techie_india on 2008-11-15
Hi all,

The usb problem is solved 
Upgrading the Ubuntu from 8.04 to 8.1 
and using the link
[https://answers.launchpad.net/ubuntu/+question/51120](https://answers.launchpad.net/ubuntu/+question/51120)
Thanks and regards

---

