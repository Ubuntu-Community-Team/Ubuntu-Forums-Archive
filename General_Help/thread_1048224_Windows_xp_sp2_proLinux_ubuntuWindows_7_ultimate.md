---
title: "Windows xp sp2 pro//Linux ubuntu//Windows 7 ultimate"
date: 2009-01-23
forum: General Help
---

### Post by PC_Head on 2009-01-23
Hi all. Im new to all this so please go easy. Ha. I have a Q? But first the desciption. My main HDD is split into 3 partions. Lets call them A, B and C. Ok. Partion 'A' has Windows xp sp2 on it. Partion 'B' has ubuntu on it and partion 'C' has Windows 7 on it. Until i installed Windows 7 on partion 'C', Grub was working fine. Now no Grub. I tried to reinstall Grub from the ubuntu cd i have with no luck. When i reboot my PC, all i get now is a screen that Windows 7 has installed (its like Grub but for Windows) that says i can boot from Windows 7 or an earlier windows install, i.e xp. How do i get back Grub?? Oh and if it helps, i installed them in that order. Fisrt xp then ubuntu then Windows 7. Can anyone help please!!! I have just reed some forums on this problem im having and to be honest, in the words of W. Axl Rose, 'its all Greek to me'. I do know how to load and install Grub from the ubuntu disk, but it wont work! HELP!!! I want ubuntu back!

---

### Post by ubu_dynamite on 2009-01-23
Have you tried this
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by PC_Head on 2009-01-23
> **ubu_dynamite said:**
> Have you tried this
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Yes i have tried it a number of times but just to be on the safe side ill try it again and let you know.


Ok i tried it with no luck. This is what i did:

sudo grub
find /boot/grub/stage1  ((it found (hd2,4))
root (hd2,4)
setup (hd4)
quit


Evrything came up as a success but still no Grub. 
Any more suggestion please?

---

### Post by ubu_dynamite on 2009-01-26
Try with setup (hd2)
[https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows](https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows)


```
sudo grub
find /boot/grub/stage1 ((it found (hd2,4))
grub> root (hd2,4)
grub> setup (hd2)
grub> quit
```

---

