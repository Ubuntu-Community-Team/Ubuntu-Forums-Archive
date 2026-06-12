---
title: "External Hard Drive help??"
date: 2009-05-27
forum: General Help
---

### Post by Zaba5 on 2009-05-27
Ok so i just installed ubuntu 8.10 and everything is working fine. I can use my 4gig usb, but when i try to plug in my External hard drive nothing happens. I tried updating everything i could, but to no avail. It doesnt even show anything in the Computer section. How can i get my external to work??

---

### Post by Munschy_00 on 2009-05-27
system>>administration>>SynapticPackageManager

look for usbmount


did that do the trick?

---

### Post by fballem on 2009-05-27
> **Zaba5 said:**
> Ok so i just installed ubuntu 8.10 and everything is working fine. I can use my 4gig usb, but when i try to plug in my External hard drive nothing happens. I tried updating everything i could, but to no avail. It doesnt even show anything in the Computer section. How can i get my external to work??

Is your external drive NTFS format. In other words, was it formatted under Windows. If so, you may want to try installing ntfsprogs from the repository.

Just a thought,

---

### Post by Zaba5 on 2009-05-27
how do i do that?

also it doesnt even mount the hard drive.

---

### Post by fballem on 2009-05-28
> **Zaba5 said:**
> how do i do that?

also it doesnt even mount the hard drive.

System > Administration > Synaptic Package Manager

Once Synaptic is open:

[LIST=1]
[*]search for ntfsprogs.
[*]Once the program is listed, right-click on the program listing and select Mark for installation from the menu.
[*]It will open a window indicating that other items need to be installed - select the Mark button. These are the dependencies.
[*]Select the Apply button. This will install ntfsprogs and the dependencies.
[*]Select the Close button.
[*]Reboot and then try connecting your USB drive.
[/LIST]

Hope this helps,

---

