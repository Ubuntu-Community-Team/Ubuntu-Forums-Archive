---
title: "virtual box kernel driver not installed"
date: 2008-06-30
forum: Desktop Environments
---

### Post by chubbtech on 2008-06-30
I've tried with synaptic add/remove applications and still I get this error message when I try to launch vbox

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

I searched for vboxdrv and got a few results but only links and a shell script.

any takers?

---

### Post by rcdeacon on 2008-07-04
If you open up the Synaptic Package manager and do a search for "virtualbox" it will bring yoiu to all of the kernels for virtualbox. Finding the correct one may be a problem. I loaded the one I thought would work but for some reason it did not work correctly. It gave me problems with my cd/dvd drive. Some things would work others would not. Have not figured it out yet.

---

### Post by NetworkGuy on 2008-07-04
I'm assuming you loaded the OSE version:

From Synaptic - 

Load virtualbox-ose-modules-generic

Reboot and you will be in business.

---

### Post by rcdeacon on 2008-07-04
Thank you NetworkGuy. I definitely loaded the wrong kernel. I am in the process of doing a fesh install of 8.04.1 on my Acer Aspire Laptop and I will try this and hopefully all will be well. It is the last hurdle to becoming windows free.

---

### Post by NetworkGuy on 2008-07-04
Just remember that you have to keep the Linux kernel and the virtualbox-kernel-module in sync when you use the OSE version.   Don't install and use a newer kernel until you also see the module has been updated in Update Manager also.

---

### Post by rcdeacon on 2008-07-04
OK. Thanks again. Now I know that the ose version DOES NOT have usb support. Am I better off getting the deb from Sun and installing it instead? USB would be nice but it is not necessary.

---

### Post by flytripper on 2008-07-04
deffers a yes..

---

### Post by rcdeacon on 2008-07-04
flytripper, thanks for the info and help.

---

