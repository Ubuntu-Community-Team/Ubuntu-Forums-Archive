---
title: "Need to resetup GRUB"
date: 2006-06-20
forum: Desktop Environments
---

### Post by m_memmory on 2006-06-20
I dual-boot my PC and a couple of days ago had a problem where I had to reinstall Windows.  I've done this but it's destroyed the dual boot-up options.  I've searched around but I don't know how to re-install GRUB into the boot sector.

I've still got my Ubuntu live CD that I installed from but I don't know how to resetup GRUB from there.

Anyone able to give me instructions please?

Thanks.

---

### Post by Ramses de Norre on 2006-06-20
From live cd do ```
sudo grub-install /dev/hdX
```
With /dev/hdX the device node of the disc you boot from.

---

### Post by Ashish Meena on 2006-06-20
Well I am not sure if simply grub-install would work but you can do one more thing .

1. boot with live cd and open terminal 
2. type 

$ grub
$ grub> root (hd0,0)          (if you have /boot in hda1 else if in hda3 then use (hd0,2 ) and similarly  )
grub> setup (hd0)           (Install GRUB in the MBR)
grub> quit                  (Exit the GRUB shell)

Ok best of luck

---

### Post by m_memmory on 2006-06-20
[QUOTE=Ashish Meena]Well I am not sure if simply grub-install would work but you can do one more thing .

1. boot with live cd and open terminal 
2. type 

$ grub
$ grub> root (hd0,0)          (if you have /boot in hda1 else if in hda3 then use (hd0,2 ) and similarly  )
grub> setup (hd0)           (Install GRUB in the MBR)
grub> quit                  (Exit the GRUB shell)

Ok best of luck[/QUOTE]

I tried root (hd0,1) as the /boot is stored in hda2 however I get the following message:

> Error 21: Selected disk does not exist.

However if I try to mount /dev/hda2 then I'm able to mount it and am able to access the files/folders on that drive.
Am I going to have to re-install Ubuntu again?

---

### Post by Ashish Meena on 2006-06-20
NO there is one more way . U can do one more thing .
Boot with ubuntu cd and type 
" Secure " in booting options then and then type "grub-install /dev/hda" 

anyway follow this link 
[http://ubuntuguide.org/wiki/Ubuntu#How_to_restore_GRUB_menu_after_Windows_installation](http://ubuntuguide.org/wiki/Ubuntu#How_to_restore_GRUB_menu_after_Windows_installation)

---

### Post by m4rqz on 2006-06-21
[QUOTE=m_memmory] Error 21: Selected disk does not exist.[/QUOTE]

I get that error too.. This is the last time I'm considering using windows.. When I get it to boot again it's ubuntu only..

---

### Post by frodon on 2006-06-21
**m_memmory**, you will find there a good documentation about re-installing GRUB : 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by m_memmory on 2006-06-21
Thank you to all for the advice/links.  I've now got my Ubuntu installation back up and running again without any headaches or any re-installs :D

I just needed to enter into the GRUB command and resetup where GRUB was actually all setup and installed to.  However to be able to do that properly via the LiveCD I needed to enter into the superuser mode first.

---

