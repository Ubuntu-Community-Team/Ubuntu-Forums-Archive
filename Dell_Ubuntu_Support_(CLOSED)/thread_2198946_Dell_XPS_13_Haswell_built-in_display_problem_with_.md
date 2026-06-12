---
title: "Dell XPS 13 Haswell built-in display problem with Ubuntu 13.10"
date: 2014-01-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tuuk on 2014-01-11
I have received my new XPS 13 (Haswell) with Windows 8.1 on it (only because they did not offer it with Ubuntu when I had ordered it). The plan is to wipe it off and put Ubuntu 13.10 on it (not even dual boot). 
The hardware is i7-4500 processor and Intel HD 4400 graphics.

When I boot it from USB with Ubuntu 13.10 installation image, I have problems with the built-in display. It looks like 12 small desktops are displayed overlapping each other. And, there is a lot of flickering; it is almost impossible to read anything because of the flickering and because each desktop is quite small on the screen. It looks like a problem with the graphics driver. When I plug into an external monitor, the external display looks fine.

So, I have not yet installed Ubuntu (after seeing that the built-in display is not workable), because I am not sure whether the waiting updates will fix the problem after the installation.

Dell provides a driver support pack for the hardware ([http://www.dell.com/support/drivers/us/en/04/DriverDetails/Product/xps-13-9333?driverId=4NTWR&osCode=1204A&fileId=3322730329&languageCode=EN&categoryId=CS](http://www.dell.com/support/drivers/us/en/04/DriverDetails/Product/xps-13-9333?driverId=4NTWR&osCode=1204A&fileId=3322730329&languageCode=EN&categoryId=CS)), but they are based on Ubuntu 12.04. I am not sure whether that will help me. I suspect that some of these updates have already made into 13.10. And I cannot identify any drivers or fixes for video in that support pack.

Intel has latest graphics stack release ([https://01.org/linuxgraphics/downloads/2013/2013q4-intel-graphics-stack-release](https://01.org/linuxgraphics/downloads/2013/2013q4-intel-graphics-stack-release)), but it is not clear what, if any, I should install from that release. I also worry about ending up with an unstable system.

An alternative would be to install "Dell"'s 12.04 release and the driver support pack, but I would rather get the latest release of Ubuntu.

Does anyone have any experience with this? Or any suggestions I should try?

Thanks,
tuuk

---

### Post by tuuk on 2014-01-12
**Update:**

Today, I tried Ubuntu 14.04 daily build from USB on my DELL XPS 13 Haswell. It booted fine. The display worked with no problems. So, the problem with 13.10 must be a matter of installing recent enough versions of some certain packages (kernel or otherwise).

Now, the question is how I should proceed. Should I install and run 14.04 daily build until it is officially released? Or, should I try to identify the exact source of the problem and patch the Ubuntu 13.10 for the time being?

In the 1-2 hours I ran Ubuntu 14.04, I did not notice any problems, but, still, is it dependable to run? (Even though this is not my primary machine: it will mainly be used when I am on the go---not too frequently nowadays.)

Otherwise, should I just try to install a newer kernel on Ubuntu 13.10 to see if that helps?

Any suggestions?

---

### Post by kevin-pijpers on 2014-01-25
Perhaps my reply comes a bit late. I wanted to say I have the exact same laptop (off topic but do you experience coil whine?). 

I installed Saucy the other day, was not looking forward to the potential problems with UEFI but it actually all worked quite well. Only thing is the touchscreen which is bugged in upstream kernel. And had to install touchpad drivers for 2 finger scrolling.

To answer your question though, I am dual booting Win 8.1 and 13.10. I have had no problems with the display (except no touchscreen as mentioned). I could imagine this having to do with you booting the USB in legacy mode and not in UEFI mode. I'm not sure though. I'm not going to remove Windows 8.1, since I need it for some PhD research software. I might one day decide to run Win in VirtualBox but I decided to take it slow because I always seem to brick my system and get headaches when I try to go for everything.

---

### Post by oldfred on 2014-01-25
Intel has helped in many updates, not just video driver, but kernel & support software. It now is adding features for the next generation, some of which help current newer systems.

It often takes a while for all the changes to catch up to a distribution. And that is often why very new hardware needs the newest Linux distribution.

Someone posted that the Sputnik updates to 12.04 from Dell/Intel were in 13.10.

Dell's seem to have similar configurations, with just added options or different screen sizes, so much of this may apply.
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

If not where you can easily update it, I would not rely on 14.04. At any point some change may cause issues. They are a lot better now at making sure updates do not get out of sync and totally break system. 
But I might have two installs. Either 13.10 or two 14.04 and keep one working and only update the other.
You really only need another 20GB for another / (root) partition.

---

### Post by slcpunk on 2014-01-27
i have the same thing ( windows 8.1 because it was cheaper with a 3yr warranty than the Ubuntu version ... go figure )

I've been posting in the dell forums too - not much to add besides what you have found.  i was also not convinced by Dell's DEB files ( many in that pack were older than what are in 13.10 already )  I did go ahead and install the one for the display and the "work-around" for the backlight.  Not sure I noticed much difference.  

Generally, I would say I'm having pretty good luck running Linux Mint 16 ( basically ubuntu 13.10 w cinnamon instead of unity ).  

Your big issues ( 12 small desktops ) sounds fairly serious.  I would re-install and try again, but I never saw anything like that and I haven't seen anyone else complain of anything similar.

suspend/resume is not perfectly stable, but I can't quite nail down the behavior to even report exactly what's going on.  ( seems to change each time depending on how I suspend, how long its suspended and when i last rebooted. )

the touchpad is not nearly as good as the old-fashioned kind with real buttons ... its just not as easy to use... but I'm a Luddite.

would be nice if Dell put out a 13.10 PPA like they had for 12.04 ... maybe when 14.04 LTS comes out?  I can grant that this is all pretty new hardware at the moment. ( and really works pretty well in my book )

---

### Post by adamraybaker on 2014-01-27
I received my xos 13 just over a week ago and I am having the same problem with 12 small screens, some cut off, and a lot of flickering while the external display works fine. Everything else seems to work fine. I am no closer to a solution so I would be keen to hear of any progress you have made. Thanks.

---

### Post by joshua15 on 2014-01-27
Adam, is this what you're seeing?  If so, I'm in the same boat as you.  I ran into issues with installing 12.04.  The problem was an issue that grub couldn't install and the entire install aborted.  I checked a few forums that said the issue might be between grub/uefi.  A few versions said to give 12.10 a shot since there is more/better support for uefi but I only got a black screen during install.


Below is a URL to a pic taken with a cell phone camera of my screen while trying to install 13.10:

[http://www.dvcipm.org/site-images/IMG_20140127_135106_122.jpg](http://www.dvcipm.org/site-images/IMG_20140127_135106_122.jpg)

Just to clarify, I tried 12.04, 12.10, and 13.10 without success.

---

### Post by adamraybaker on 2014-01-28
> Adam, is this what you're seeing?

That is the same as I was getting. 

I ended up installing 14.04 because it worked and I needed to get some work done so I didn't want to keep playing with it. It feels like a crazy thing to do but it all seems to work fine so far. I would have tried 13.10 and upgrade the kernel otherwise but I am pretty new to this so that might be useless. Sorry I can't be more helpful.

EDIT: Actually I do have one small problem. Opening the laptop after sleep is unpredictable, sometimes it is fast and sometimes there is a black screen for a little while. It is not a huge hassle so I haven't looked into it but I did see some conversations about something similar so I am hoping it is a simple fix.

EDIT 2: and no two-finger scrolling...

---

### Post by wesley-langelaan on 2014-01-28
> **adamraybaker said:**
> That is the same as I was getting. 

I ended up installing 14.04 because it worked and I needed to get some work done so I didn't want to keep playing with it. It feels like a crazy thing to do but it all seems to work fine so far. I would have tried 13.10 and upgrade the kernel otherwise but I am pretty new to this so that might be useless. Sorry I can't be more helpful.

EDIT: Actually I do have one small problem. Opening the laptop after sleep is unpredictable, sometimes it is fast and sometimes there is a black screen for a little while. It is not a huge hassle so I haven't looked into it but I did see some conversations about something similar so I am hoping it is a simple fix.

EDIT 2: and no two-finger scrolling...

I've had the same problem with the touchpad. This should fix it:

open terminal
sudo nano /etc/modprobe.d/blacklist_i2c_hid.conf
Type "blacklist i2c_hid" (without the quotes)
Save and reboot

---

### Post by realavaloro on 2014-01-31
Hi all,

I'm having the same issue with my dell xps 13 i4200u fhd. I posted my print screen on the thread I opened when I couldn't find this one.

[http://ubuntuforums.org/showthread.php?t=2202717&p=12915437](http://ubuntuforums.org/showthread.php?t=2202717&p=12915437)

I will give it a try with ubuntu 14.04 but I'm not very happy about it :)

Has anybody found any other workaround? Or even another linux distribution where I could work it out? I'm looking to have dual boot win8.1 and ANY Linux (preferably ubuntu and stable) on same SDD drive with uefi boot. 

Thank you

---

### Post by realavaloro on 2014-02-01
I have installed Ubuntu 14.04 (gnome alpha 2) with no success as I am unable to boot (although it was displayed well).
The EFI partition has two folders (entries) one for Windows Booter and another for Ubuntu
but Grub does not load, so Windows 8.1 always boots

If I press F12 when starting I can see the boot options Windows Booter and ubuntu. If I select ubuntu and press intro it still loads Windows :confused:

I have the following partitions on my SSD drive:
/dev/sda1  recovery NTFS
/dev/sda2 EFI system FAT32
/dev/sda3 unknown Microsoft Reserved
/dev/sda4 NTFS Windows8 (my C: in windows)
/dev/sda5 NTFS Data (my D: in windows)
/dev/sda6 Ubuntu ext4

I tried with the LiveCD Ubuntu 14.04 to install grub, but it says that /boot/grub is not readable on boot. Impossible to install. Aborting.. or something like that
I tried to apt-get install the boot repair within the live CD but it seems some repositories are missing so it won't install it
I downloaded the boot repair ISO and put it in a USB pendrive. When I boot with it the screen is black and it does not do anything. Also after that most of the options of the UEFI (within Windows 8.1) have disappeared :confused: and I can only select Edit EFI System.

I don't know what else to do.. I'm regretting having bought this laptop.. :(

---

### Post by sergiotorresperez on 2014-02-01
[COLOR=#333333][FONT=UbuntuRegular]I am also suffering from the distorted screen problem... with a twist.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Yesterday I tried the live usb versions of Ubuntu and Mint 13.10. I could boot from the USB and both worked fine. Image was good.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Today I ended up installing Ubuntu 13.10, everything in UEFI mode. The installation process was OK, however, when booting to the newly installed OS, the screen issue emerged. I thought: OK, the installer has downloaded and installed a newer kernel or graphic card drivers than the ones used by the installation usb. They may be causing the problem...[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]My surprise was that aftar that installation, the screen issue happens when booting from the Ubuntu or Mint USB! I'm runnig exactly the same system that hours before, and now the screen issue happens!. The only difference is that I installed Ubuntu 13.10 in UEFI at some time....[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]So, I reckon the issue is not in the kernel or the graphic card, but something going on in the UEFI setup made by the Ubuntu installation process, as this is the only thing that changed.[/FONT][/COLOR]

---

### Post by oldfred on 2014-02-01
New Haswell Sputnik - Dell orbits Linux a third time with revamped Sputnik notebooks
[http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/](http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/)

Also links back to this as posted above.

 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)

---

### Post by realavaloro on 2014-02-01
That's odd..
I'm surprised you were able to install Ubuntu 13.10 properly in UEFI mode. I tried that and I couldn't manage the distorted screen issue..

I gave up. I have spent some days already trying to get Ubuntu dual booting with Win 8.1 but Microsoft won the battle..
I have now created a NTFS partition occupying the space I had left for Linux, but on that partition I have placed a VirtualBox Ubuntu 13.10 machine. I wish I could have dual booting but the problems with Grub on UEFI and failing to use the boot repair tools (I couldnt apt-get install it in Ubuntu 14.04 live cd) fed me up.

Good luck with it. Maybe in the future when everything is more stable I will give it another try.

---

### Post by snapdragon2 on 2014-02-02
Hey, I did experience the same problem with 13.10.
The solution is to install it with legacy mode turned on in UEFI and disabling secure boot.
After that you install it normally and update it. If you have all updates installed you can disable legacy mode again and it should be working.

---

### Post by gustaf.granath on 2014-02-03
> **snapdragon2 said:**
> Hey, I did experience the same problem with 13.10.
The solution is to install it with legacy mode turned on in UEFI and disabling secure boot.
After that you install it normally and update it. If you have all updates installed you can disable legacy mode again and it should be working.

Just got this machine and never done dual boot with UEFI before. Is there a recent tutorial that is recommended? I have found many older posts but nothing recent.

Anyways, several people seem to have problems to get everything to work on this machine so before I go ahead and wanted to make sure I got it right.
Would this be the general procedure for ubuntu - win 8.1 dual boot on XPS 13 Haswell?

0. Make win recovery USB (so factory settings can be recovered)
1. Free up disk space (in Win)
2. Open UEFI to disable secure boot and to turn on legacy mode.  
3. Install ubuntu 13.10 (latest kernel) from USB. Place the bootloader on a separate partition.
 4. Open UEFI and allow secure boot and turn on UEFI mode. 

Should this work or am I missing something?

---

### Post by oldfred on 2014-02-03
In my signature is a link are lots of links to more info on UEFI.
But new Haswell systems have some extra issues, see link above on Precision Dell but applies to all Intel Haswell systems.
Dell's have been one of the systems that users had the least issues with (until this thread).

       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


 Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
      
 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell 17R Brightness
[http://ubuntuforums.org/showthread.php?t=2195650](http://ubuntuforums.org/showthread.php?t=2195650)

     

These were Toshiba's but discuss some Hawell issues that may not be just Toshibas.

 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
> Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by Vicbus on 2014-02-09
> **gustaf.granath said:**
> Just got this machine and never done dual boot with UEFI before. Is there a recent tutorial that is recommended? I have found many older posts but nothing recent.

Anyways, several people seem to have problems to get everything to work on this machine so before I go ahead and wanted to make sure I got it right.
Would this be the general procedure for ubuntu - win 8.1 dual boot on XPS 13 Haswell?

0. Make win recovery USB (so factory settings can be recovered)
1. Free up disk space (in Win)
2. Open UEFI to disable secure boot and to turn on legacy mode.  
3. Install ubuntu 13.10 (latest kernel) from USB. Place the bootloader on a separate partition.
 4. Open UEFI and allow secure boot and turn on UEFI mode. 

Should this work or am I missing something?


Hi,

I just did that but now I can't boot Windows anymore !

When secure boot is disabled, I can load Ubuntu without problems in UEFI or in legacy mode.
When secure boot is enabled, I can't do anything : "No bootable devices found"...


Edit : I just saw that the Windows partition does not exist anymore. Ubuntu took his place ... I have to reinstall Windows.

---

### Post by oldfred on 2014-02-09
Did you do a reinstall of Ubuntu?
If so add yours to the ones with that issue.

       Reinstall says overwrite Ubuntu but it also erases existing Windows.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by Vicbus on 2014-02-09
> **oldfred said:**
> Did you do a reinstall of Ubuntu?
If so add yours to the ones with that issue.

       Reinstall says overwrite Ubuntu but it also erases existing Windows.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)


Yes, I did ! So here is the reason why Windows was overridden. 

Thanks !

---

### Post by gustaf.granath on 2014-02-10
When you installed in legacy mode, did you put the boot loader on a separate partition or with the windows one?
Cant find the post(s) anymore where this procedure is describe and how to convert the installation to an efi afterwards.

Im not sure how much problems this will cause when it is time to upgrade to 14.04, which seems to not have the screen problem. Maybe it is just better to wait.

---

### Post by oldfred on 2014-02-10
With a BIOS boot and MBR, you install the grub boot loader to the MBR of the hard drive as we have done for over 30 years. Both Windows on Ubuntu only boot from MBR(msdso) partitioned drives with BIOS.

If using UEFI you have to have the newer gpt partitioning and both Ubuntu and Windows only boot with UEFI.

Only Ubuntu will install to gpt partitioned drives and boot in either BIOS or UEFI. With BIOS you have to have a 1 or 2 MB unformatted partition with the bios_grub flag. With UEFI the first partition should be the efi partition which is FAT32 formatted and has the boot flag. Boot-Repair then can convert Ubuntu from UEFI to BIOS or vice-versa if correct partitions and gpt formatted. But Windows does not easily convert.

---

### Post by gustaf.granath on 2014-02-10
Thanks! However, after testing 14.04 that works excellent (no display  issues in uefi mode and many other things that works much better), it  seems like a better option to go with that version. Only 2 weeks until  the beta release.

---

### Post by oldfred on 2014-02-10
Just understand there may be breakage. 
But they are a bit better now about not updating one part that depends on another and not doing the other so it breaks.

---

### Post by Vicbus on 2014-02-19
Hello,

I re-installed Windows 8.1 with factory settings and then installed Ubuntu in dual-boot in legacy mode.

I was not able to launch Ubuntu in UEFI mode so I used boot-repair. After replacing the GRUB files at the good location I have now a "grub rescue" issue and I'm not able to boot Ubuntu anymore (Windows still works).


Thank you for helping

---

### Post by monkeybrain20122 on 2014-02-19
Since this is a dual boot with Win8 with uefi and what not I am not sure if this would work (it would if you have a pure Linux system whether single or multiboot)

boot from a live usb. Find out where is Ububtu's root (/) partition or just where Ubuntu is if you have no separate root.

```
blkid
```
(or sudo blkid if the command doesn't show anything)

Mount the partition where your Ubuntu / is (or where Ubuntu is if you have no separate / partition), let's say it is in sda5
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Then reboot.

Notice the first command involves the partition (/dev/sda5 here) while the second involves the whole drive (/dev/sda here)

Edited: life would be a lot simpler if you get rid of Windows. :)

---

### Post by Vicbus on 2014-02-19
> **monkeybrain20122 said:**
> Since this is a dual boot with Win8 with uefi and what not I am not sure if this would work (it would if you have a pure Linux system whether single or multiboot)

boot from a live usb. Find out where is Ububtu's root (/) partition or just where Ubuntu is if you have no separate root.

```
blkid
```
(or sudo blkid if the command doesn't show anything)

Mount the partition where your Ubuntu / is (or where Ubuntu is if you have no separate / partition), let's say it is in sda5
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Then reboot.

Notice the first command involves the partition (/dev/sda5 here) while the second involves the whole drive (/dev/sda here)

Edited: life would be a lot simpler if you get rid of Windows. :)


Thanks ! But when I try this it writes "mkdir: cannot create directory 'mnt/boot/grub/i386-pc' : Read-only file system" :???:

---

### Post by oldfred on 2014-02-19
After Boot-Repair converted to UEFI, are you still trying to boot in BIOS mode? You may have grub boot loader in the protective MBR, but will not work if now UEFI.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Vicbus on 2014-02-20
> **oldfred said:**
> After Boot-Repair converted to UEFI, are you still trying to boot in BIOS mode? You may have grub boot loader in the protective MBR, but will not work if now UEFI.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)


If I try in UEFI mode, I enter Windows without the possibility to choose Ubuntu.

If I try in legacy mode, I have a "grub rescue" issue and I can't load Ubuntu.

Here is the URL of the Create Boot-Info report : [http://paste.ubuntu.com/6965320/](http://paste.ubuntu.com/6965320/)


Thank you very much ! :)

---

### Post by oldfred on 2014-02-20
Your Ubuntu install has been converted to UEFI so the grub in the MBR will not work in BIOS boot mode.
But in UEFI you should have a choice to boot the ubuntu entry.

You do not have the secure boot version installed, so you must have secure boot off to see the ubuntu entry in uEFI as with secure boot on, only secure boot systems are shown.

Discussion of Haswell & Intel with Dell:
       Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
> Running in legacy BIOS mode or in UEFI mode both work, but for now  you'll need to enable "Legacy Option ROM" in the BIOS if you're running  in UEFI mode because of the display's backlight. This is because of an  issue with the Intel i915 driver that currently affects several systems  from many vendors. If you don't enable this BIOS option, the backlight  will be stuck at the lowest setting in Linux.
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

---

### Post by Vicbus on 2014-02-20
> **oldfred said:**
> Your Ubuntu install has been converted to UEFI so the grub in the MBR will not work in BIOS boot mode.
But in UEFI you should have a choice to boot the ubuntu entry.

You do not have the secure boot version installed, so you must have secure boot off to see the ubuntu entry in uEFI as with secure boot on, only secure boot systems are shown.




In UEFI I don't have any choices, Windows loads automatically, even when secure boot is off !

Perhaps it's a problem with the MBR / Windows Boot Manager ?

---

### Post by oldfred on 2014-02-20
Post this:
 # from live CD and use efibootmgr
sudo efibootmgr -v

      
 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
change label
[http://askubuntu.com/questions/383166/having-trouble-adding-uefi-entry-using-efibootmgr](http://askubuntu.com/questions/383166/having-trouble-adding-uefi-entry-using-efibootmgr)

And you may have to do this:

 UEFI NVRAM boot entries are cached in the BCD store
BCD has 1:1 mappings for some UEFI global variables
Any time {fwbootmgr} is manipulated, NVRAM is automatically updated

   Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

---

### Post by Vicbus on 2014-02-20
Thank you very much !

I used BCDedit and changed the path to grubx64.efi. Everything worked fine, but not in secure boot mode, so I changed grubx64.efi to shimx64.efi and now Windows does not boot anymore (the Grub menu appears but when I choose Windows it writes "invalid EFI path"). :confused:

---

### Post by oldfred on 2014-02-20
Can you boot Windows from UEFI menu?

Did you also run Boot-Repair and its buggy UEFI rename. That usually is not required for Dells and then you can only boot Windows with Boot-Repairs entry to boot the renamed Windows efi file.

Grub2's os-prober in 13.10 should create correct chain load to Windows efi file entries. Older versions of grub did not and only Boot-Repairs version would work.

---

### Post by Vicbus on 2014-02-21
Ok, since I used os-prober I can boot Windows but only in UEFI when the secure boot is **off** (Ubuntu is always working good).

Any idea to make Windows working also in secure boot ?


Thank you very mych for your help ! :)

---

### Post by oldfred on 2014-02-21
I am a bit surprised that Windows will boot with secure boot off, but not with it on. 
Is it not nice that Microsoft sets up this complicated secure boot feature and then cannot use it itself.

       [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

---

