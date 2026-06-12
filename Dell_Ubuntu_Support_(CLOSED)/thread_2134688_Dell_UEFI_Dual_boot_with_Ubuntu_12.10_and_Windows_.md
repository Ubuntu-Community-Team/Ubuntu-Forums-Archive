---
title: "Dell UEFI Dual boot with Ubuntu 12.10 and Windows 7"
date: 2013-04-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vasilisgrappas on 2013-04-11
I just bought a new Dell Inspiron 7520. It had windows 8 as an OS. I erased windows and installed Ubuntu 12.10 in UEFI boot mode. Now I want to create a Dual boot system with windows 7 because for me windows 8 is one of the worst OS.The procedure that I followed and was unsuccesful was:
-I installed Gparted and created a partion NTFS to install windows
-I changed the bootmode to UEFI with secure mode off
-I created a bootable usb  (FAT 32) with windows 7 iso.

But the problem is that when I enter the UEFI boot menu when the PC starts there no option appeared so that i can boot it from the usb.
I also tried to install Windows using a DVD but again the same problem!

Finally I enabled legacy boot option on boot menu and the bootable usb appeared as an option but when I selected it and tried to istall windows at the stage where I had to select the partion that I had created foe windows appeared a message telling me that the partion is of GPT type and windows cannot be installed. Help me plz!

---

### Post by oldfred on 2013-04-12
I have not installed Windows and do not ever expect to, but saved some links and info:

Windows will only boot from gpt partitioned drives with UEFI.

Windows requires specific partitions for UEFI boot.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)

Somewhere I saw that Microsoft was saying drivers for Windows 7 would not be updated to work with new features on Windows 8 computers, implying you should not install Windows 7. Several have posted that they have and it works, but it may depend on computer.

      
  You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
Install Windows efi to new drive.
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB](https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB)

---

### Post by vasilisgrappas on 2013-04-12
Thank you very much. I will give it a try. I only need windows to play games.

---

### Post by vasilisgrappas on 2013-04-12
I can't solve the problem. Maybe if I tried to install first windows 7 and then try to install ubuntu 12.10. But the problem is how to uninstall ubuntu and install windows 7 in UEFI mode. Its a dead end!!!! I am desperate!

---

