---
title: "Ubuntu/Windows XP duel boot problem"
date: 2009-01-24
forum: General Help
---

### Post by ForMar on 2009-01-24
Firstly sorry if this is wrong sub but I had no idea where this topic goes

I recently formatted my hard drive and installed ubuntu (first time) and windows xp. It took me about 5 tries to get it right so formatting again is not an option. 

My problem is that after selecting windows xp from grub my usb mouse and keyboard go dead lights and all. But it only happens when I select windows so linux and grub work fine when it comes to my keyboard and mouse. I did get into windows once but right after I installed one (irreverent) driver and restarted it just stopped working. 

Plz note that I am very new to linux and grub. I also dont know how to start windows in safe mode or in last good config while using grub. 

Thank you for you time

---

### Post by Moop on 2009-01-24
Make sure that you have usb keyboard and mouse enabled in your bios. 

You can access safe mode in XP by choosing windows from grub and then immediately hitting the f8 key.

---

### Post by mikewhatever on 2009-01-24
Correct me if I am wrong, but if you can use the keyboard to select Windows, then there is no grub related usb problem, also, if you can use both the keyboard and the mouth in Ubuntu, it looks like the problem is on the Windows side. Hence, it doesn't matter how new you are to Linux, and hopefully, you'll figure out what's wrong with Windows in no time.

---

### Post by ForMar on 2009-01-24
Alrgiht I cked the bios config and everything for usb was either enable or on auto so I everything to just enabled and then booted windows in last known.

About it being entirely windows I actually have no idea but I think that grub controls some of the kernels (but I could be out of my mind). Either way I felt it important to note seeing as it could be a factor.

Thanks for you time

---

### Post by mikewhatever on 2009-01-24
> **ForMar said:**
> Alrgiht I cked the bios config and everything for usb was either enable or on auto so I everything to just enabled and then booted windows in last known.

About it being entirely windows I actually have no idea but I think that grub controls some of the kernels (but I could be out of my mind). Either way I felt it important to note seeing as it could be a factor.

Thanks for you time

Grub lets you choose the kernel version and the boot options, but all that applies to Linux. Obviously, it doesn't control any part of the Windows kernel in any possible way.

---

