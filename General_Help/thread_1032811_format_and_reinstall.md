---
title: "format and reinstall?"
date: 2009-01-06
forum: General Help
---

### Post by Indyviews on 2009-01-06
Hi everyone, I have just dumped Microsoft and am chopping at the bits to get started with Linux! I may not have done the change correctly though.

I changed from Windows 2000 and installed  8.10 on my hda and gave the whole disk to Ubuntu. Although it is working, I notice during the bootup that it mentions Windows 2000 as another operating os and that I have only 135gig of space left on my 160gig drive.

I was thinking that if I gave the whole drive to Ubuntu that the disk (sata) would be cleaned and I would have a fresh start. Even though Ubuntu is installed and working I would feel better knowing that Windows is gone for good.

My questions are how much room does 8.10 take on the disk and what is the best way to uninstall Ubuntu and format my drive, or should I bother to do so and reinstall 8.10?

Thanks for any help

---

### Post by Titan8990 on 2009-01-06
Open the terminal and report the output of the following:


```
sudo fdisk -l
```

---

