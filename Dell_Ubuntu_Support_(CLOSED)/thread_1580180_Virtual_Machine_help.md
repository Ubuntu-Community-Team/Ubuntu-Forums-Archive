---
title: "Virtual Machine help?"
date: 2010-09-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bamim2 on 2010-09-23
I have a Dell Latitude D610 running Windoze XP Pro SP3. I'm using Virtual PC 2007 with Ubuntu 10.04 installed as a Virtual Machine. 

* Does anyone know where I can get the VMAdditions for Linux? 
* Does anyone know how I can get the Intel 945GM graphics driver for Ubuntu?

What I really need to know is how to get any better resolution than 800x600, my screen in the VM is REALLY small. Any help would be most appreciated.

---

### Post by psavva on 2010-09-23
> **bamim2 said:**
> I have a Dell Latitude D610 running Windoze XP Pro SP3. I'm using Virtual PC 2007 with Ubuntu 10.04 installed as a Virtual Machine. 

* Does anyone know where I can get the VMAdditions for Linux? 
* Does anyone know how I can get the Intel 945GM graphics driver for Ubuntu?

What I really need to know is how to get any better resolution than 800x600, my screen in the VM is REALLY small. Any help would be most appreciated.

Hi, 

You mentioned that you are using "Virtual PC 2007" which is Microsoft's Virtualization Solution. Hence, VMAdditions do not exist for Virtual PC 2007.
VMAdditions belongs to VMWARE. [www.vmware.com](www.vmware.com)

Secondly about the graphics driver. A virtual machine does not recognise and utilise the graphics driver that is installed on your PC. Instead, it has it's own build in graphics driver, hence, you'll never find the graphics driver specifically for the 945GM in a Virtual Machine.  
Instead, you will need to install the software on the Virtual Machine that comes with the Virtualization Solution you choose. 

I highly suggest you try VirtualBox.  It has easy to install "Guest Additions" (like VMAdditions) which installs graphics drivers, and will give you as high resolution as you need.

[www.virtualbox.org](www.virtualbox.org)

Good Luck.

---

### Post by bamim2 on 2010-09-23
Thank you. That's exactly what I needed to know. I'll check out VirtualBox.

---

### Post by bamim2 on 2010-09-23
I just thought I'd mention for anyone looking at this later that VirtualBox is not dot com, it's dot org. It's here:

http://www.virtualbox.org/

---

### Post by yerayenrique on 2010-09-23
VirtualBox is, certainly, the best Virtual PC tool I've ever tried, and it's free :).

---

### Post by psavva on 2010-09-24
> **yerayenrique said:**
> VirtualBox is, certainly, the best Virtual PC tool I've ever tried, and it's free :).

Happy to help :D

Btw, I fixed the URL, thanks for that :D

---

