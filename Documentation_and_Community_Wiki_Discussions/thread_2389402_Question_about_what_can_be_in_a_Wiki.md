---
title: "Question about what can be in a Wiki"
date: 2018-04-16
forum: Documentation and Community Wiki Discussions
---

### Post by Cavsfan on 2018-04-16
I'm currently maintaining the  [[COLOR=green]MaintenanceFreeCustomGrub2Screen[/COLOR]]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen") Community Wiki.

It currently contains legacy disk drive technology, meaning non SSD/UEFI and it has been pretty popular I believe. Now, I have a new computer and it will have everything UEFI plus I still have my old computer to support legacy Grub.
I have not gotten to the point where I can add a custom EFI grub to my computer or to the Wiki. Since this method of customizing the grub menu can readily be used on any Debian distro including Ubuntu.

I was wondering if I could add Arch Linux to the Wiki. I am not meaning adding a separate part for just Arch Linux, just including it.
Where users who multi-boot several Linux systems: Arch and/or Ubuntu and/or other Debian distros and/or Windows.

Arch uses only 2 files to customize the Grub: **/etc/default/grub** and **/etc/grub.d/06_custom**.
It does not have a **/etc/grub.d/05_debian_theme** file, so the menu colors and background picture are in **/etc/default/grub**.
It also does not have a **/etc/grub.d/30_os-prober** file either unless you explicitly install it for other operating systems.

I just thought I'd ask if this was doable or not in the [[COLOR=blue]https://ubuntuforums.org[/COLOR]]("https://ubuntuforums.org").

Thank you.
Cavsfan

---

### Post by Cavsfan on 2018-04-19
I installed Xenial Xerus 16.04.4 UEFI yesterday and the default grub would not boot, after installation into any OS including 16.04.

The only thing that saved me was in my BIOS, I could select the Arch boot loader or the Windows 10 boot loader.

I'll be working on fixing that and of course when I do I'll add the Ubuntu UEFI boot customization. Not able to go too fast right now and it seems to be pretty complicated but, I'm sure like anything else it is indeed doable.

Regards,
Cavsfan

---

### Post by slickymaster on 2018-04-19
> **Cavsfan said:**
> I'm currently maintaining the  [[COLOR=green]MaintenanceFreeCustomGrub2Screen[/COLOR]]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen") Community Wiki.

It currently contains legacy disk drive technology, meaning non SSD/UEFI and it has been pretty popular I believe. Now, I have a new computer and it will have everything UEFI plus I still have my old computer to support legacy Grub.
I have not gotten to the point where I can add a custom EFI grub to my computer or to the Wiki. Since this method of customizing the grub menu can readily be used on any Debian distro including Ubuntu.

I was wondering if I could add Arch Linux to the Wiki. I am not meaning adding a separate part for just Arch Linux, just including it.
Where users who multi-boot several Linux systems: Arch and/or Ubuntu and/or other Debian distros and/or Windows.

Arch uses only 2 files to customize the Grub: **/etc/default/grub** and **/etc/grub.d/06_custom**.
It does not have a **/etc/grub.d/05_debian_theme** file, so the menu colors and background picture are in **/etc/default/grub**.
It also does not have a **/etc/grub.d/30_os-prober** file either unless you explicitly install it for other operating systems.

I just thought I'd ask if this was doable or not in the [[COLOR=blue]https://ubuntuforums.org[/COLOR]]("https://ubuntuforums.org").

Thank you.
Cavsfan
IMO, the proper venue for your query would the ubuntu-doc mailing list: [email]ubuntu-doc@lists.ubuntu.com[/email]

---

### Post by Cavsfan on 2018-04-20
> **Cavsfan said:**
> I'm currently maintaining the  [[COLOR=green]MaintenanceFreeCustomGrub2Screen[/COLOR]]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen") Community Wiki.

It currently contains legacy disk drive technology, meaning non SSD/UEFI and it has been pretty popular I believe. Now, I have a new computer and it will have everything UEFI plus I still have my old computer to support legacy Grub.
I have not gotten to the point where I can add a custom EFI grub to my computer or to the Wiki. Since this method of customizing the grub menu can readily be used on any Debian distro including Ubuntu.

I was wondering if I could add Arch Linux to the Wiki. I am not meaning adding a separate part for just Arch Linux, just including it.
Where users who multi-boot several Linux systems: Arch and/or Ubuntu and/or other Debian distros and/or Windows.

Arch uses only 2 files to customize the Grub: **/etc/default/grub** and **/etc/grub.d/06_custom**.
It does not have a **/etc/grub.d/05_debian_theme** file, so the menu colors and background picture are in **/etc/default/grub**.
It also does not have a **/etc/grub.d/30_os-prober** file either unless you explicitly install it for other operating systems.

I just thought I'd ask if this was doable or not in the [[COLOR=blue]https://ubuntuforums.org[/COLOR]]("https://ubuntuforums.org").

Thank you.
Cavsfan

> **slickymaster said:**
> IMO, the proper venue for your query would the ubuntu-doc mailing list: [EMAIL="ubuntu-doc@lists.ubuntu.com"]ubuntu-doc@lists.ubuntu.com[/EMAIL]

Thanks slickymaster! 
I'll do that when I get some more of this sorted out. UEFI is new to me, very different from Legacy MBR partitioning and I'm still trying to figure it out.

---

