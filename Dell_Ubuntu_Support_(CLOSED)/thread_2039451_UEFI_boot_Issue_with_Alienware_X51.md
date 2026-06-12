---
title: "UEFI boot Issue with Alienware X51"
date: 2012-08-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ahlf7bfdj on 2012-08-08
Hello there,
 
 
I bought an Alienware X51 with Win7 64 bit installed via UEFI Boot mode. Now, I would like to have Ubuntu installed alongside Windows but am having problems booting the Ubuntu Live USB (32 bit).
 
 
Firstly, here are my system specs:
 
 
Processor: Intel(R) Core(TM) i3-2120 CPU @ 3.30GHz.
BIOS Manufacturer: Alienware; Version A06.
MB Manufacturer: Alienware.
Video Adapter: Intel HD 2000 Graphics/Nvidia Geforce 545 GDDR5 OEM.
Memory: 4 GB, 1333 Mhz.
Hard Drive Device: ST31000524AS ATA Device, 1000 GB.
Optical Drive: HL-DT-ST DVD+-RW GA31N ATA Device.
Operating System: MS Windows 7 Home Premium Edition, 64 bit.
 
 
Second, my disk partitions:
 
 
I couldn't manage to connect to my home network after loading Gparted, so I had to take a picture of my screen. (Sorry!)
 
[IMG]http://img821.imageshack.us/img821/618/gparted.jpg[/IMG]
 
 
 
I set up both my Gparted and Ubuntu Live USB with Universal USB Installer. When booting...
 
 
[COLOR=black]With Ubuntu:[/COLOR] I am greeted with a black screen and I believe a white cursor flash (underscore key?) in the top left, before my machine proceeds to load Win7.
 
 
With Gparted: I am able to boot into the Linux distro, albeit in Failsafe Mode. **Why can I boot UEFI with Gparted but not with Ubuntu?**
 
 
 
When I switch my boot mode from UEFI to Legacy, I can boot the Ubuntu live USB. After entering, "nomodeset," I open the Ubuntu installation tool, but once I reach the part where the installer lists the partitions, it doesn't show Win7. (Because they use different boot modes, Win7 is UEFI and my Live USB is currently in Legacy).
 
 
I found this quote from [[COLOR=darkorange]https://help.ubuntu.com/community/UEFIBooting[/COLOR]]("https://help.ubuntu.com/community/UEFIBooting")
 
 
"Some machines ([[COLOR=darkorange]all Dell laptops, all new Apple from 2010 on, some Lenovo[/COLOR]]("https://lkml.org/lkml/2011/6/8/322")) have bugs in their UEFI firmware, preventing them from booting (black screen). Linux Kernel 3.0 (and higher versions) includes patches with workarounds for them. It is therefore recommended to use a Linux kernel of version 3.0 or higher."
 
 
I'm not sure if the above quote applies to me, but I think it is worth posting.
 
 
 
I have posted this question on some other forums, but none of the people who have helped have given me a step-by-step procedure on how to install Ubuntu with my machine. I am really lost when it comes to linux, I have just learnt the basics of navigating in terminal.

---

### Post by oldfred on 2012-08-09
The latest version of Ubuntu seems to install to UEFI for most systems, but still has the video issues that many of us have. I only have nVidia and have to use nomodeset on liveCD/USB and on first boot. 

Some with the newer system like yours with the Intel video built in seem to get it working with the Intel and then experiment with the nVidia and the nVidia drivers. 

Can you set which video you use in BIOS on connect to that output?
or 
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

GUIDE: (U)EFI installation Also full install post #52 superfreak on pg.6
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)

[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

Be sure to use the Windows tools to shrink the Windows partition first and reboot a couple of times so Windows can run chkdsk and update itself for its new size.

Another UEFI with issues on dual video:
[http://ubuntuforums.org/showthread.php?t=1994622](http://ubuntuforums.org/showthread.php?t=1994622)

---

### Post by drmrgd on 2012-08-09
It seems, though, that you're not able to actually boot the Ubuntu .iso, as indicated by the fact that it switches over to Windows 7.  This is what I've seen before when the system tries the first boot device, decides it's not valid, and moves on to the next one in the list.  So, I think altering Grub isn't going to fix it, as Grub never actually gets launched.  

It's an odd problem.  However, as I mentioned in the last thread, it looks like there's a number of posts on the Dell Support forums with similar problems, and there is a suggestion that there's a hardware issue booting into other media sources as UEFI.  One thing to check, which may not be what's happening here, is the format of the USB drive you made.  According to this post, if the drive is formatted any other way than FATx (FAT32 for example), the system will not recognize it as a valid, bootable UEFI device:

[http://en.community.dell.com/owners-....aspx#20144598](http://en.community.dell.com/owners-....aspx#20144598)

Since you can get Gparted to boot (which I do not believe is being booted in UEFI mode), and you can boot Ubuntu in BIOS mode, it would be helpful to boot to one of them and check the formatting of the Ubuntu USB drive you made to check that it's FAT formatted.  

If you need another source of confirmation, another quick test that I'll bet will work is if you unplug your hard drive(s), and try to boot the Ubuntu .iso in UEFI mode again.  I'm betting you'll get an error along the lines of non-bootable device or no disc found or something.

The other potential issue could be that this system is UEFI Secure Boot, and won't boot the .iso in UEFI mode because it's missing the signing key.  I believe the only workaround there is to disable the Secure Boot protocol, although I'm not sure how to go about that.

---

### Post by oldfred on 2012-08-09
I doubt that vendors would turn on secure boot until Windows 8 as that is a requirement with Windows 8.

But even some BIOS have a locked MBR, so there may be some other UEFI settings.

These were from users with BIOS that had to change settings, maybe something similar in your UEFI:

> BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA 6 Gbit/s  from 6 Gbs to a SATA II - 3Gbs 
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Raid meta data on drive - even if one drive (Vendor happend to set it on)
Changed IDE Mode to AHCI Mode
Then,when the SATA3G_1 selection appears in the drive list below,select the Enabled option.


Have not seen any Alienware systems that I can remember, so not sure of anything else unique with them.

---

### Post by ahlf7bfdj on 2012-08-09
Thanks both of you for your input. Here is my bootscreen after I press F12 on system startup:
 
[IMG]http://img689.imageshack.us/img689/9278/selectbootdevice.jpg[/IMG]
 
UEFI: KingstonDataTraveler is FAT32, it's the Gparted Live USB, it boots okay.
UEFI: Generic Flash Disk is also FAT32, it's the Ubuntu Live USB, it is the one that doesn't show anything when I choose it boot from it.
 
They are both linux distros, and it seems that when I choose "UEFI: KingstonDataTraveler," I am booting Gparted in UEFI mode, because I am able to see all of my Windows partitions. If I booted in Legacy with Gparted I wouldn't be able to see my installed os, it would say unallocated or something, shouldn't it?
 
 
With Ubuntu, I am not able to reach the screen where you are able to press tab to add more parameters. It immediately goes black and loads windows. (I take take a quick video to show this if needed).
 
Also, I tried switching my BIOS display mode from discrete to IGFX and realized after booting that my integrated graphics only has HDMI output, which I do not have. I only have DVI displays. So I wont be able to see if using integrated graphics solves the issue becauae I can't see anything! I switched it back to discrete.
 
I also can't find any mention of UEFI Secure Boot, though I found Intel XD Bit Technology in my BIOS, which I do not think applies here.
 
What do you guys reccomend I do? What steps should I take first?

---

### Post by oldfred on 2012-08-09
Is the install of Ubuntu on the liveCD ok? It almost seems like it is not a bootable version.

You can check that ISO you downloaded is ok. You did download the 64bit version not the 32bit?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by ahlf7bfdj on 2012-08-09
I checked my ubuntu-12.04-desktop-i386.iso with this hash:
 
d791352694374f1c478779f7f4447a3f
 
and it worked. So, my installation is okay, unless Universal USB Installer didn't write the iso to my USB correctly, which I doubt.
 
Do you recommend me downloading the 64 bit version instead?

---

### Post by drmrgd on 2012-08-09
After doing a bunch more Google scavenging, I'm finding more than a couple users with issues booting from either a CD / DVD or USB device, and some of them are also seeing the system go straight to Windows instead of booting their alternate device.  From my reading, I'm beginning to think there's an issue with these motherboards or the way the BIOS is configured.  Here's another example of a user that can't boot from any USB or CD (no solution unfortunately):

[http://en.community.dell.com/owners-club/alienware/f/3746/p/19442250/20076437.aspx](http://en.community.dell.com/owners-club/alienware/f/3746/p/19442250/20076437.aspx)

And another who couldn't even boot from a Windows Server 2008 CD:

[http://en.community.dell.com/owners-club/alienware/f/3746/p/19437650/20056864.aspx](http://en.community.dell.com/owners-club/alienware/f/3746/p/19437650/20056864.aspx)

Although this is a totally different system (and this doesn't much make sense to me based on what you've decribed), I found this link suggesting to make sure you're plugged into a USB2.0 port and not a USB3.0 port:

USB3.0 vs USB2.0 Boot
[http://en.community.dell.com/owners-club/alienware/f/3746/p/19447741/20100012.aspx](http://en.community.dell.com/owners-club/alienware/f/3746/p/19447741/20100012.aspx)

That's a bit of a shot in the dark, but maybe relevant.  In case it's a hardware issue, I wonder if you tried other USB ports.  

Here's a post about a user experiencing some faulty motherboards:

[http://en.community.dell.com/owners-club/alienware/f/3746/t/19445129.aspx](http://en.community.dell.com/owners-club/alienware/f/3746/t/19445129.aspx)

Since you *can* boot the Ubuntu installer in BIOS, but *can not* boot it in UEFI mode, I would think it's not the fault of the USB drive or the .iso.  You did mention in the first post that you've made a 32-bit .iso.  Maybe this has something to do with it?  Does anyone know if the UEFI boot stuff is in both the 32-bit and 64-bit versions?  Is there any reason you don't want to use the 64-bit version?

EDIT:  Just re-read Fred's post.  I think it has to do with the 64-bit vs 32-bit versions.  Need to find out for sure if UEFI is supported in the 32-bit version natively.

---

### Post by drmrgd on 2012-08-09
OK, I think this is it.  The problem is that you have a 32-bit .iso, and you need a 64-bit .iso.  The 32-bit .iso does not have built in support for UEFI like the 64-bit version does.  I just looked through the package lists here, comparing 32-bit to 64-bit, and there's no .efi files in the 32-bit version:

[http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)

Try the 64-bit installer and let us know how it goes.

---

### Post by ahlf7bfdj on 2012-08-10
Using the 64 bit iso worked! I reached the grub-1.99 screen, pressed e to enter the "nomodeset" command, and booted up Ubuntu successfully. Now, would you guys kindly explain how to partition my hard drive to fit Ubuntu? Would 50GB be enough? I don't want to destroy my Win7 partition in the process, how do I make it install safely?

I'm not sure about these sda drives, or what to do:

[http://imageshack.us/photo/my-images/534/pic1gj.png/](http://imageshack.us/photo/my-images/534/pic1gj.png/)
[http://imageshack.us/photo/my-images/829/pic2cyu.png/](http://imageshack.us/photo/my-images/829/pic2cyu.png/)
[http://imageshack.us/photo/my-images/268/pic3zd.png/](http://imageshack.us/photo/my-images/268/pic3zd.png/)

(I didn't want my post to be huge so if you like can you please look at those pics)

---

### Post by oldfred on 2012-08-10
You can easily post screen shots or camera photo (reduced in size) by using the paperclip icon in the edit panel of your message. Also you can use gdisk to list partitions. I suggest adding gdisk as it is a tool to see & edit gpt partitions.

Not sure if it is true with gpt drives, but with MBR we always suggest to use the Windows tools to shrink the Windows NTFS partition, then reboot several times, so it can run chkdsk and recognize its new size. Also backups of the Entire Windows & a Windows repairCD should be made just in case. Also backup efi partition, there was a bug in earlier versions of the installer/grub that overwrote the efi. It is fixed in current version, but if you happen to try an older install it still will have that bug.  

Ubuntu will run in as little as 5GB, but that requires significant effort to regularly houseclean. It depends a lot on what you plan to do and if not sure the default install of just / (root) and swap in the 50GB unallocated is fine. Alternates are two added partitions, a separate partition for /home and separate NTFS partition for shared data.

I usually suggest separating systems (both Windows & Linux) from data. Since /home is mostly data many of us suggest separate /home partition. 

And Windows does not like a lot of writes into its system partition. LInux' NTFS driver exposes all the normally hidden files & folders so it is easier to accidentally move or delete something. I used to unhide everything in Windows and regularly did something that required major repairs. So I might make the Windows system partition smaller and create a shared NTFS data partition. That was the first thing I did with my system and it allowed me to move the Firefox & Thunderbird profiles to my shared. Then I did not have to reboot to see email or have all my bookmarks from Windows.

You can use gparted to create the Linux partitions as it works with gpt partitioning, if you want to create partitions in advance. One advantage of gpt is all partitions are primary. I do not notice any difference in using gparted with gpt drives or MBR other than there is no logical drives.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

My standard suggestion, others may have different opinions and many of us use system differently so needs vary. I find my own optimal partitioning is not so good a couple of years later, but then buy a new drive anyway.

For the Total space you want for Ubuntu, You already have the efi partition, an do not need the bios_grub if only booting UEFI:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32
    1 MB bios_grub  no format 
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by ahlf7bfdj on 2012-08-10
You certainly provided a lot of information! However, I not exactly partition-savvy when it comes to this.

The Ubuntu installer told me, "No operating systems detected." I hope that is okay!

I started out by making a 100 GB unallocated partition in Windows Disk Management.

So should I create a 50GB NTFS partition to use as data across Win7 and Ubuntu?

And near the end of your post you said that I should make another 250MB efi partition, dont I have one already? Im just confused about the end of your post.

I know respected forum members are hesitant to give step by step instructions for newbs like me, but to be honest, it seems like that is exactly what I need right now. Is it possible that I can just use the partition manager in the Ubuntu installation instead of using gparted?

If it makes it easier, I dont need to use hibernation on my pc.

I dont know anything about this, heck I didn't even know what a MiB was until today!

---

### Post by oldfred on 2012-08-10
The installer should see your Windows. Not sure if with UEFI it it somehow different or not. 

My standard instructions assume a blank drive, so you already have the efi partition and that is fine.

I find it best to use manual partitioning and then use manual install. I do not want auto install to go off and accidentally delete everything.  And if it is not seeing your Windows it is a problem.

If you go into manual install does it show the existing NTFS partition(s)? I have use the install to unallocated space but again with UEFI everyone before has posted it works best if partitions are created in advance with gparted. You can use gparted tutorial to understand it better.

You need the /, /home & swap partitions and optionally the NTFS shared data partition, 50GB should be fine. It really depends on how much data you may want to share.

---

### Post by ahlf7bfdj on 2012-08-10
I can see all 3 of my NTFS partitions: Recovery, Win7 OS, and my new 50GB partition for file sharing.

I have a warning symbol next to my /dev/sda3 partition, the one with the flag msftres. Maybe that is what is causing my operating system to be undetected? As of writing, in gparted running in Ubuntu Live USB, sda3 is the only partition with the warning icon next to it.

When I am done making these partitions, when installing Ubuntu manually, what do I select for "Device for boot loader installation?"

---

### Post by oldfred on 2012-08-10
With UEFI booting, Windows has a hidden unformated partition for some code. That is just the Microsoft reserved area & should be ok. Gparted cannot parse unformated partitions.

With UEFI you choose the efi partition which should be sda1 as the location to install grub. You are installing grub-efi not the BIOS grub-pc version.

Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by ahlf7bfdj on 2012-08-11
Okay, I got everything working thanks to both of your guys' help. I have my system set up to load windows by default and if I press f12 on startup I can select ubuntu.

Ill make sure I mark this thread as solved once I get back from a walk.

Again, I cannot stress how helpful you two were, truly exeptions to the usual comments I have gotten on other threads.

---

### Post by Omegus on 2012-10-12
I know this has been solved but my issue is I have wiped windows off and made Ubuntu my sole OS on the X51. After I installed it and rebooted it comes up with the purple backround for the Ubuntu load screen but after it goes black then nothing loads. Is there anything I need to change towards BIOS. Here is my Partition:

1gb to "EFI"
1gb to "BootGRUB"
3gb to "/boot"
40gb to "/"
3gb to "swap"
and the rest went to /home.

---

### Post by oldfred on 2012-10-12
If you are booting and get grub menu, or can get it with shift, then it is probably video issues. Do you also have the dual video which is another can of worms.

I think in UEFI/BIOS you need to set to boot with one or the other video chip to get it working.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Switchable Graphics is killing my Ubuntu Experience - see post #9
[http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317)

---

### Post by Omegus on 2012-10-12
When I installed it from my live dvd I changed quiet splash to no quiet no splash nomodeset just to get it to load. I then went to trial it before install. There I went into the termenal to change the grub but it wouldn'tlet me update the changes. Do you think that might have something to do with it?

---

### Post by oldfred on 2012-10-12
With my nVidia 9600GT on an older system, I have to remove quiet splash and use nomodeset on all liveUSB boots and first boot after install. Once nVidia driver is installed then I have no issues.

If you only have Ubuntu you may not get grub menu. Holding down shift from BIOS should get grub menu. Not sure if that is now fixed if in UEFI mode, there used to be a bug.

---

### Post by Omegus on 2012-10-12
Which driver did you get? Is it in the software center? So I should boot up the live session and change the grub file from there?

---

### Post by oldfred on 2012-10-12
You need to boot and get grub menu. Then you can use e to edit and remove the splash quiet and replace with nomodeset. That will give you minimal video but then you can install the nVidia driver from system settings, additional drivers. 

Also see post #2 which has links on above procedure.

I think during install you can specify to include proprietary drivers now, so you do not have to leap thru the hoops to get it to work.

---

### Post by Omegus on 2012-10-13
yeah I tried to boot up the grub menu but it won't load . The screen goes purple then black. The only time I can load up the grub menu is when I load the live DVD or USB stick. I tried hitting shift and then shift+f10 still nothing.

Edit- - got the grub to boot I had to do the rapid shift key tap. Thanks for the help. I am happy I learned something new.

---

