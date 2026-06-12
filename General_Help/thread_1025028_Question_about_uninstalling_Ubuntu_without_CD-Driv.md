---
title: "Question about uninstalling Ubuntu without CD-Drive"
date: 2008-12-29
forum: General Help
---

### Post by NC10 on 2008-12-29
Hello ! 

I am new to Ubuntu, I have a short question (i am sorry if this is the wrong place):

Before i am going to install Ubuntu on my netbook i want to know if its possible to uninstall Ubuntu without a Win CD ? I think formatting the partition is no problem with the live usb stick (which i will use to install), but how can I fix the MBR without any CD's. I used Google but couldn't find any informations about uninstalling. 

I hope somebody can help me.

Thank you. :popcorn:

---

### Post by Agent ME on 2008-12-29
What do you mean by uninstalling Ubuntu? That would just leave your computer operating system-less, unless you already have a dual-boot system.

---

### Post by NC10 on 2008-12-29
No, on the Netbook there is Windows XP pre-installed, i want Ubuntu for my 2nd OS, just in case, if i need to uninstall Ubuntu, i want to know if it works without a windows cd.

---

### Post by dcstar on 2008-12-29
> **NC10 said:**
> No, on the Netbook there is Windows XP pre-installed, i want Ubuntu for my 2nd OS, just in case, if i need to uninstall Ubuntu, i want to know if it works without a windows cd.

You can probably download the Windows fixmbr program from the 'net, or copy it off your Windows installation when you want to remove Grub (which is what you are talking about).

---

### Post by NC10 on 2008-12-29
Yes, i am talking about the grub.

I will search the net for the fixmbr program, tahnk you for the hint.

And formatting the partition where linux is installed is no problem too ?

---

### Post by caljohnsmith on 2008-12-29
You could write a Windows equivalent MBR to your drive while you are in Ubuntu by doing:
```
sudo lilo -M  /dev/sda mbr
```
Then the next time you boot, you should boot directly into Windows assuming the Windows partition still has the boot flag set on it. To check that you could do:
```
sudo fdisk -l
```
And look for the partition with the asterisk * under the "boot" category, and that is the partition with the boot flag. So once you run the above lilo command to install a Windows MBR, you could then delete your Ubuntu partitions or format them as NTFS for use in Windows. Let me know how it goes or if you run into problems.

---

