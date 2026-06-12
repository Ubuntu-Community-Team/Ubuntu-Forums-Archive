---
title: "Dell studio 1558 high fan speed issue"
date: 2012-11-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bond17_007 on 2012-11-05
Hi, I have 2011 dell studio 1558 with core i3, 8 gb ram and 128gb ssd.i noticed that my CPU fan runs on high speed most of the time., I searched around and saw that it could be due to the bios or the video driver. In my case I have the latest bios.. a12 and my system only has the intel graphics card. I even opened up the machine cleaned the dust.. But it did not help.. My core temp shows around  55 degrees.. Any help would be appreciated

---

### Post by 2F4U on 2012-11-05
The 55 degree seems to be not too high, so my guess would be a faulty fan management due to a wrong ACPI implementation by Dell. You can try some additional tweaks not implemented in the Ubuntu default configuration:

[https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks](https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks)

---

### Post by bond17_007 on 2012-11-05
> **2F4U said:**
> The 55 degree seems to be not too high, so my guess would be a faulty fan management due to a wrong ACPI implementation by Dell. You can try some additional tweaks not implemented in the Ubuntu default configuration:

[https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks](https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks)

Thanks 2F4U,
   I will try that tonight hopefully it will work. 
On a site node, I used "Jupiter" to get my temperature readings etc. I will check it again after updating the ACPI impl.

---

### Post by 2F4U on 2012-11-05
What version of Ubuntu are you running? Ubuntu 12.10 now requires 3D capable graphics hardware and can place quite some burden on the graphics card and maybe also on the processor. Therefore, you should open Sytem Monitor and see if the there is a considerable CPU activity.

---

### Post by northrup on 2012-11-05
Interesting; I'm running Kubuntu 12.04 on the same model laptop (except mine's a bit differently-configured; i5, 500GB platter-stack HDD, Radeon HD graphics) and don't really see much fan use difference between Windows 7 and Kubuntu (if anything, Kubuntu seems to have less).

So, adding to the previous forum-goer's inquiry regarding the version of Ubuntu, are you using Unity or a different desktop manager (like KDE or Xfce)?  Also, if you're on 12.10, were you having the same issue on older versions?

---

### Post by bond17_007 on 2012-11-05
Thanks for the comment guys,
I am running Ubuntu 12.10. 

I tried by adding 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=1"
as mentioned in the link but it didnt do anything.

i have the default Intel graphics 3000 HD on this thing (not ATI radion or nVidia).

I have had this issue with both 12.04 and 12.10. Perhaps even tried mint13 and this issue persist, i guess since mint is based on ubuntu, it wouldnt have made any difference anyway.

Also, I had to make following entry on my grub file because w/o that entry, my screen would be on max brightness and i wasn't able to control it. After adding following line my brightness control worked.
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

any suggestions at this point? 

I checked the system monitor and CPU usage is less than 10% on each core but my CPU temp is 78 degrees according to "Jupiter".

---

### Post by 2F4U on 2012-11-06
You could try one or both kernel parameters acpi.power_nocheck=1 OR acpi_osi=linux:

[https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options](https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options)

---

### Post by bond17_007 on 2012-11-06
> **2F4U said:**
> You could try one or both kernel parameters acpi.power_nocheck=1 OR acpi_osi=linux:

[https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options](https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options)

Thanks 2F4U, I really appreciate your help on this. more I look online seems like a issue with acpi. Most people were referring to ATI or nVidia graphics card driver and no one talked about intel graphics card which is the case  for me. Hope this works.
I will test it tonight.

---

### Post by bond17_007 on 2012-11-06
> **bond17_007 said:**
> Thanks 2F4U, I really appreciate your help on this. more I look online seems like a issue with acpi. Most people were referring to ATI or nVidia graphics card driver and no one talked about intel graphics card which is the case  for me. Hope this works.
I will test it tonight.

Thanks again.. i tried acpi.power_nocheck=1, also acpi_osi=linux and even acpi=off, but did not help. I am still noticing the same fan issue :(

---

