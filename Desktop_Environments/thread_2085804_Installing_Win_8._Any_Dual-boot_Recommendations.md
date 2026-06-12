---
title: "Installing Win 8. Any Dual-boot Recommendations?"
date: 2012-11-19
forum: Desktop Environments
---

### Post by lemonoid on 2012-11-19
Okay. I have Windows 7 Installed and Ubuntu 12.04. I am about to Install Windows 8. My plan right now is to make a bootable installation of Windows 8, plug it in, boot my computer, and let it's do its thing. I know nothing when it comes to partitioning for Windows so I'm just hoping that I will be given the option to wipe my hard drive and do a clean install of Windows 8. I have come to terms with losing my current 12.04 installation and having to re-install that or 12.10. I have backed up all the data I need from my Ubuntu on an external HDD and can just restore it later. I was just wondering if there are any recommendations from those here before I proceed with my planned process. I recently have come across OS-Uninstaller. I know that sometimes there can be problems deleting Windows NTFS partitions due to them being marked as secure? (I could be wrong here in my wording). I am wondering if the best way to go about this would be to use OS-Uninstaller to uninstall my Windows 7, and then use my bootable Windows 8 USB to install such OS. Then after that's done, re-install Ubuntu. So I guess there are two options there. My first option of just popping in the USB and hoping it will wipe my hard drive and partition it as it needs to be, or the second which is using OS-Uninstaller to delete Windows 7 and then continuing my installation. So my question is, for those who care to input, which way should I go, the first or the second? And if there is something I am missing in one of the processes please let me know. I don't have any new fancy UEFI, my computer is an old, custom build desktop by a friend of my dad with a small 1TB hard drive, 4GB Ram, AMD Sempron 2500+ processor. I have never had a problem with any installation/partitioning of any extra OS'es on this desktop, but Windows has always been installed on here. I am very unfamiliar with installation of Windows. Any help here would be greatly appreciated. Thank you very much.

(ps I have live media of Boot-Repair, GParted, Ubuntu 12.10, and a whole bunch of other OS's if that helps)

---

### Post by YannBuntu on 2012-11-19
Hello

If you plan to delete Win7 after installing WIn8, i recommend you delete Win7 BEFORE installing Win8 (else, Win8 will mix its boot files with Win7).

If you want more advise, please run Boot-Repair --> Create BootInfo and indicate the URL that will appear.

---

### Post by offgridguy on 2012-11-19
Hi lemonoid;  It sounds like you have a pretty solid grasp of what you are doing, i don't
anticipate any problems either way.

---

### Post by oldfred on 2012-11-19
Is your Windows 8 a full install or an upgrade? If an upgrade I think you have to have the old install or else it will not work.

---

