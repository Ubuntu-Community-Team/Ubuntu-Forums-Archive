---
title: "Did I break GRUB?"
date: 2008-12-26
forum: General Help
---

### Post by Me_Rock on 2008-12-26
Hey there, I have a small problem.

The other day, I was installing xubuntu on to an external hard drive. The install went great and everything worked. Now for the bad news...my laptop gets a GRUB error 21 when I try to boot up now.

Then I figured maybe it was just a problem with the GRUB that was on the laptop. I configured the laptop to boot from the external hard drive, but when it got to the OS selection screen, I chose the install that was on the laptop's hard drive. It worked with no problem.

So, I guess the problem is just with GRUB on the laptop, because it works when I select the laptop's hard drive from the GRUB on the external hard drive.

I couldn't figure what was up by myself, so I could use some help.

Thanks

---

### Post by logos34 on 2008-12-26
You need to disconnect the extenral usb and reinstall grub on the MBR of the internal HDD (see link in my signature), so that it points to the menu.lst on the laptop drive.  Then when you want to boot xubuntuon the external drive toggle the boot drive in the Bios like you did

---

### Post by kindlinux on 2008-12-26
> Then I figured maybe it was just a problem with the GRUB that was on the laptop. I configured the laptop to boot from the external hard drive, but when it got to the OS selection screen, I chose the install that was on the laptop's hard drive. It worked with no problem.

So, I guess the problem is just with GRUB on the laptop, because it works when I select the laptop's hard drive from the GRUB on the external hard drive.


That´s strange
I think you have install ubuntu on the extrenal without grub,also I think you would have to burn a Super Grub Disk CD.

---

### Post by Me_Rock on 2008-12-28
Thanks, logos34! Using the 'Restore Grub from Live CD' guide worked like a charm!

---

### Post by logos34 on 2008-12-28
glad to hear.  Mark as 'solved' (>thread tools)

enjoy ubuntu

---

