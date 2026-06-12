---
title: "[Elementary OS] Dual-boot Elementary OS and Windows 8.1 - 64-bit UEFI"
date: 2014-03-12
forum: Debian
---

### Post by Heisenburger on 2014-03-12
Hi everyone,

First-time Linux user here. Today I attempted to set up a dual-boot of Windows 8.1 and Elementary OS (based on Ubuntu), both 64-bit and using UEFI. I wanted to have the Windows 8.1 bootloader instead of Grub for personal reasons. I followed the following instructions to the best of my abilities:

[LIST]
[*][http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
[*][http://apcmag.com/how-to-dual-boot-windows-8-and-linux.htm](http://apcmag.com/how-to-dual-boot-windows-8-and-linux.htm)
[*][https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[/LIST]

Following the first thread, I shrunk my main partition in Windows 8 to make space for Elementary. I then disabled Fast Boot and Secure Boot (since the Elementary Live USB wouldn't load otherwise). Using the Elementary Live USB, I created a 4 GB swap drive and a ~60 GB root drive for installation; other than that default options were used. Installation completed successfully and I rebooted the computer.

To my surprise, my computer booted to Windows 8 after installation. I opened EasyBCD and added the Elementary partition to the Windows bootloader. When restarting and attempting to open it however, I got the following message: [http://i.imgur.com/UEZSDZ1.jpg](http://i.imgur.com/UEZSDZ1.jpg)

I then booted back to my Elementary Live USB and ran boot-repair (as described at [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) using the default settings (and I said yes to renaming Windows files). After that process finished and I rebooted my computer however, I was confronted by this screen: [http://i.imgur.com/h0ecEXg.jpg](http://i.imgur.com/h0ecEXg.jpg)
I was unable to open Elementary OS from here. Here is the report generated afterwards: [http://paste.ubuntu.com/7082375/](http://paste.ubuntu.com/7082375/)

Fortunately, I was able to get to the BIOS settings after entering exit, and I was able to boot back to the Live USB. I retried boot-repair while saying no to renaming Windows files instead. After reboot, I was confronted by the same screen again and still could not open Elementary OS. Here is the report: [http://paste.ubuntu.com/7082412/](http://paste.ubuntu.com/7082412/)

When I returned to the Live USB, I disabled the Secure Boot option in boot-repair and repeated the process (and said yes to renaming Windows files). Report: [http://paste.ubuntu.com/7082458/](http://paste.ubuntu.com/7082458/) After restart, I saw the same screen again. However, when I exited to the BIOS and selected the Elementary OS partition, I was able to access Grub, which gave options for Elementary OS (the installed version) and Windows. I booted to Elementary OS and ran boot-repair again (report: [http://paste.ubuntu.com/7082475/](http://paste.ubuntu.com/7082475/)). Rebooting resulted in the same situation: having to exit from the initial grub screen, go to the BIOS to select the Elementary partition, and then go to the "actual" grub.

I booted to Windows and started EasyBCD again. I moved a newly-created Elementary boot entry (it linked to some EFI file) to the bottom of the list and set Windows as the default OS. I overwrote the MBR, which brought back the Windows Boot Manager (looks like this now: [http://i.imgur.com/r48o6Zz.jpg](http://i.imgur.com/r48o6Zz.jpg)). There are three entries - the default Windows 8.1, the Elementary OS entry I created, and the Elementary option that appeared after using boot-repair. Attempting to open either Elementary options results in the initial problem showing up again (this screen: [http://i.imgur.com/UEZSDZ1.jpg](http://i.imgur.com/UEZSDZ1.jpg)).
[B]
At the moment[/B], I am currently on Windows and hoping that I didn't break anything important. I would like to use the Windows bootloader to start Windows and Elementary, but I am running into the issues above. Running boot-repair doesn't help since I run into the issue with the two grub screens and having to go to the BIOS to start Elementary's grub.

Your help is greatly appreciated. Thank you so much in advance!

---

### Post by oldfred on 2014-03-13
Moved to OtherOS since Elementary.

I understand with BIOS why some may want Windows boot loader, as with BIOS you can only have one system in MBR and that one is in control
With UEFI every system is equal and installs its boot files into separate folders in the efi partition. UEFI then lists all bootable systems and you just set one as default. You do not have to use either Windows or grub to choose to boot, but can choose from UEFI menu or your one time boot key.
UEFI is a boot manager which lists boot options, grub is both a boot manager and a boot loader for Ubuntu. And then you are adding another boot manager with EasyBCD.

Do not run the Boot-Repair rename. That is only for those systems where vendors have modified UEFI to only boot Windows. With the file rename booting Windows from UEFI actually boots grub/shim as that is the only way with those systems. But then you can only boot Windows from grub menu. 

 Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

Originally EasyBCD did not work with UEFI, so make sure you have the most current version.

 Wndows 8 BCD 
[http://ubuntuforums.org/showthread.php?t=2110638](http://ubuntuforums.org/showthread.php?t=2110638)
[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)

You can just add grub to UEFI/BCD. Maybe this is all EasyBCd does now with UEFI?

      
 Remove Duplicate Firmware Objects in BCD and NVRAM
[http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx)
UEFI NVRAM boot entries are cached in the BCD store
BCD has 1:1 mappings for some UEFI global variables
Any time {fwbootmgr} is manipulated, NVRAM is automatically updated

   Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

Boot-Repair also cannot tell which efi files in efi partition you really need to boot. Some vendor put many efi files for repair or whatever into efi partition. Then you get too many entires. Details on editing 25_custom in link in my signature.

---

### Post by Heisenburger on 2014-03-13
Thank you for your reply and my apologies for posting in the wrong forum.

I have version 2.2 of EasyBCD and I was told that it is the latest version.

To clarify, I will need to do the following:
1. From the Elementary Live USB, run Restore EFI Backups (I did not run a backup before running boot-repair and already overwrote the boot loader using EasyBCP, will this still work?)
2. Add Elementary back to UEFI using EasyBCD.
3. Remove duplicate objects.

I do not understand the section on Alternative to Boot Repair and everything after that. Could you explain that further?

Thanks for your help!

---

### Post by oldfred on 2014-03-13
I think the restore should work as Boot-Repair has renamed files. EasyBCD is editing BCD, I do not think it does renaming of efi files.
But it never hurts to have a full backup of the efi partition.
If not:
       Boot-Repairs rename copies this /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi, becomes this:
/EFI/Microsoft/Boot/bkpbootmgfw.efi

    Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

The alternative is instead of EasyBCD, just edit BCD yourself. That then adds the entry you need.

---

### Post by Heisenburger on 2014-03-13
I was able to run the Boot-Repair backup (and selected No to the file replacement question this time), report at [http://paste.ubuntu.com/7086899/](http://paste.ubuntu.com/7086899/)
Back in Windows, I set up elementary OS on EasyBCD again. There were no duplicates it seemed so I didn't really remove any entries from EasyBCD.

Now I have Windows 8.1 starting automatically, with the options to run 8.1 and elementary OS in the Windows bootloader. However, selecting elementary OS still gives me this: [http://i.imgur.com/DCXZ4FM.jpg](http://i.imgur.com/DCXZ4FM.jpg)
When pressing ESC to go to the UEFI settings, there is a choice to boot to elementary OS: [http://i.imgur.com/vkjaOal.jpg](http://i.imgur.com/vkjaOal.jpg)
Selecting the second choice finally gives me the Elementary grub. So right now I have a really roundabout and sketchy way of getting to Elementary OS. Re-running boot-repair on Elementary doesn't seem to do anything however. (report: [http://paste.ubuntu.com/7086966/](http://paste.ubuntu.com/7086966/) )

What should I do next?

---

### Post by itscarlos on 2014-03-13
I was about to make a thread about this, i'm also having a hard time installing eOS on Windows 8.1

---

### Post by oldfred on 2014-03-14
@itscarlos
If suggestions here do not work for you, then please start a new thread. Just about every users hardware and configuration ends up somewhat different and it gets too difficult to make suggestions to help more than one in one thread.

---

### Post by Heisenburger on 2014-03-14
Hey oldfred, I'm still having issues with the boot loader. :/ I can access elementary OS from the Windows boot loader, but it involves getting an error message and having to go to the BIOS. I'd like eOS to boot immediately when selected instead of having to go through that.

Thanks for your help!

---

### Post by oldfred on 2014-03-14
Are you booting with EasyBCD/Windows and using that to boot grub?
Or are you booting the elementary entry from UEFI menu?

Someone posted that Windows always forces a reboot when booting something else via BCD.

---

### Post by Heisenburger on 2014-03-14
The first one is what I'm trying to get right now and I have it set up that way. However, I keep on getting this error: [http://i.imgur.com/DCXZ4FM.jpg](http://i.imgur.com/DCXZ4FM.jpg)

I'm assuming that this is what you mean by UEFI menu: [http://i.imgur.com/vkjaOal.jpg](http://i.imgur.com/vkjaOal.jpg) which is the only way to get to Elementary at the moment.

How do I go from the second one to the first one?

---

### Post by oldfred on 2014-03-16
Is your post from one time boot key, not UEFI. 
You should be able to change settings in UEFI on default boot order of devices.

Do you still have EasyBCD, if so you may need to ask them.
       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by Heisenburger on 2014-03-21
Hi again,

I posted on the [EasyBCD forums]("https://neosmart.net/forums/showthread.php?t=12850") and was told that my preferred setup cannot be done since Windows 8.1 does not allow non-Windows OSes to boot from its bootloader. For the sake of convenience, I would like to give grub a try.

My problem right now however is that my BIOS settings do not allow me to change the boot order to start with the Elementary partition first.

The last time I tried boot-repair and used the rename option, I was met by the following screen: [http://i.imgur.com/h0ecEXg.jpg](http://i.imgur.com/h0ecEXg.jpg)
I had to use the exit command to get to these boot settings: [http://i.imgur.com/vkjaOal.jpg](http://i.imgur.com/vkjaOal.jpg) and start grub from there, so this is even more inconvenient.
I currently have Secure Boot disabled since that was the only way Elementary's live USB would load and install.

How should I proceed with trying to get grub as the default boot loader?

---

### Post by oldfred on 2014-03-23
Some just use one time boot key to choose what to boot. Others may use the rename function in Boot-Repair, but then you can only boot Windows from grub and backkups of efi files are important. A third choice I have seen is this. Not sure if difference with 8 vs. 8.1 works with these choices or not.

 Remove Duplicate Firmware Objects in BCD and NVRAM
[http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx)
UEFI NVRAM boot entries are cached in the BCD store
BCD has 1:1 mappings for some UEFI global variables
Any time {fwbootmgr} is manipulated, NVRAM is automatically updated

   Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

---

### Post by Heisenburger on 2014-03-23
It's working perfectly now, thanks oldfred! :D

Also, I currently have Secure Boot disabled (which I did so that Elementary's live USB could run and install in the first place). Would it be a good idea to reenable Secure Boot again or just leave it as is (if it ain't broke don't fix it kind of thing)?

**What I did:**

**Step 1:** [http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)

On Windows, I started cmd.exe in Administrator mode and typed the following command. This is **only if you have Secure Boot disabled**:

```
bcdedit /set {bootmgr} path \EFI\elementary\grubx64.efi
```

If you have Secure Boot enabled, you will have to use shimx64.efi instead. In my case I couldn't get the live USB to run and install elementary so I had to disable Secure Boot.

I then restarted my computer.

**Step 2:** [http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order](http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order)

I restarted into Elementary and used the guide above to set Windows as the default boot on grub.

**Step 3:**

Back on Windows, I removed the two Elementary entries on the Windows Boot Manager using EasyBCD, so that a boot screen does not show up when loading Windows.

---

