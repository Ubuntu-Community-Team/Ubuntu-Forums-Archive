---
title: "Lost dual boot LinuxMint and Ubuntu 22.04"
date: 2024-07-06
forum: Desktop Environments
---

### Post by lragan2 on 2024-07-06
I needed Ubuntu to run KiCad, so I installed Ubuntu  22.04. I let it run out of memory, and gdm3 would not load.  Booted into recovery mode, and went down the list presented, including updating grub. Used CLI to delete data and uninstall apps, to no avail.  Used Gparted (after backups) to free up Ubuntu, reinstalled gdm3, and Voila Ubuntu works great.  Now I cannot get to the Mint OS.  I suspect, but don't know, that the problem is due to update on grub, which, I learned, defaults to NOT looking for other OS installations.  So I edited /etc/default/grub to enable the line "GRUB_DISABLE_PROBER=false". But "grub-update" was not available, and apt did not know it.  I read how to manually update, but "mkconfig" is missing as well. The 2.1 GB boot repair file I downloaded only addresses EFI.  I am reluctant to try to switch to this modern system.  So I am stuck. I appreciate help to fix this problem. Like, really appreciate it...

---

### Post by guiverc on 2024-07-06
Whilst upstream Grub does not scan for other OSes in all cases now (with Grub 2.06 & higher), Ubuntu carries patches that keep the prior defaults for Ubuntu users in most cases  (*there an install case where a secondary install can cause another OS to not be detected which will cause Ubuntu to have the upstream re-scan disabled; but only because the other OS isn't detected** and thus the system is treated a single boot install; this issue impacts all OSes using grub though*).

You mention `grub-update` which is not a normal command, and I suspect a typo.  The command Ubuntu uses is `update-grub` to re-scan for other OSes.

---

### Post by oldfred on 2024-07-06
Hardware since 2012 is UEFI with gpt partitioning as Microsoft required UEFI/gpt install by vendors for Windows 8.
Only place for BIOS boot is for Windows install on systems prior to 2012. Since about 2010 you could install Linux on gpt partitioned drives.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If installing multiple systems they must all be in same boot mode or all UEFI or all BIOS.
UEFI & BIOS are not compatible, once you start booting, you cannot switch. Or grub can only boot other installs in same boot mode.

---

### Post by lragan2 on 2024-07-07
Thank you both for your replies.  My system is BIOS, according to the following search:
/sys/firmware$ ls
acpi  dmi  memmap
It is my understanding that a directory should exist for emi.  The referenced boot repair iso is quite clear that it is for emi or uemi only.
Am I missing something?

---

### Post by oldfred on 2024-07-07
My Dell from a couple of years ago says "BIOS", but when I go into BIOS it says it is UEFI only.
Systems since about 2020 are UEFI only.

Some systems that have UEFI hardware, may have BIOS installs of Windows.
If system is only BIOS, Ubuntu is probably too much system for it.
My old laptop from 2006 would not boot Ubuntu, I could boot server install.
I was able to use Kubuntu on external SSD with that old laptop.

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

---

### Post by yancek on 2024-07-07
So is the problem that you installed Ubuntu along with your already existing install of Mint and now you cannot access Mint?  Did you create new partitions for Ubuntu so as not to overwrite Mint.  

>  But "grub-update" was not available, and apt did not know it.  I read how to manually update, but "mkconfig" is missing as well 

There is no 'grub-update', it is update-grub and needs to be prefixed with sudo so you have root permisisons.  the 'mkconfig' script is grub-mkconfig and both these scripts are in the /usr/sbin directory.  If you run:  ls -l /usr/sbin/update-grub and ls - /usr/sbin/grub-mkconfig you should see output.  If you don't have them something major is wrong with your system.

---

### Post by lragan2 on 2024-07-07
The computer in question is "Opliplex 7010" from Dell.  There is a store here in Austin that sells used Dell stuff.  I bought it there several years ago.  It came with Windows 10, which I removed to install Linux Mint.  (Like most housecleaning services, I do not do Windows). I began using Mint 15-20 years ago when I was gifted a "Mintbox", which I have updated over the years and my wife uses it to download recipes, etc. Ubuntu 22.04 installed alongside Mint without a hiccup, until I carelessly let it run out of memory--weeks after install.  
If you ever find life's rewind button, please tell me where it is...

---

### Post by lragan2 on 2024-07-07
My apologies for miss-typing the original posts.  Yes, I know that one must be super user to run either command, and tried them in the correct order..  I ran dual boot for three weeks or so without difficulty, and could access either Mint or Ubuntu -- did so at least daily.  
I created a file "upgrade-grub", which I learned is a stub for "grub-mkconig -o /boot/grub/grub.cfg", which is how I learned that is no mkconfig.

$ ls -|/usr/sbin/grub-mkconfig
bash: /usr/sbin/grub-mkconfig: No such file or directory,

 so yes, it appears that you are correct in your assumption that there is something major wrong...

---

### Post by oldfred on 2024-07-07
That Dell is UEFI as Intel I-series chips are all UEFI systems.
Yours is  i5-3470.

The rewind button is called good backups. And most of us have learned the hard way by losing data.

Does Boot-Repair report tell anything?

---

### Post by yancek on 2024-07-08
>  I created a file "upgrade-grub", which I learned is a stub for  "grub-mkconig -o /boot/grub/grub.cfg", which is how I learned that is no  mkconfig.


No, it is update-grub not upgrade-grub and on any Mint or Ubuntu install it should exist and you are correct, update-grub doesn't do any more than point to the grub-mkconfig script which you can easily see if you open it in a text editor.

 >  so yes, it appears that you are correct in your assumption that there is something major wrong... 		

One thing that was wrong was a typo in my previous post.  There should be a space after ls -l and before the path and that is always true with ls commands.  Below entry is correct.

```
ls -l /usr/sbin/grub-mkconfig
```

In your initial post, you indicate you  'ran out of memory' but it sounds more like you ran out of space on your hard drive(s).  If you run the df -h command you can see the size of partitions mounted and space used.  If you want the space on all partitions you can either use gparted or mount all partitions before running the df -h command.

The boot repair software you can get from the link in the initial post by oldfred can be used on either a Legacy or UEFI system.   Running that and selecting the option to Create BootInfo Summary and posting the link here will give information that can be used by others to help you.

---

### Post by lragan2 on 2024-07-08
Thank you for the additional time you have invested on my behalf.  Yes, the problem was drive space, not memory.  I began to realize, as yancek pointed out, that there is more wrong than a grub issue.  I took a different approach altogether by using my 24.02  ISO file on a USB stick and, after tweaking the allocations a bit with GParted, chose to "Install ... alongside Linux Mint and Ubuntu 24.02".  So I now have, in the order presented on start-up, the NEW 24.0, Linux Mint 20.1, and the OLD 24.02.  I have copied all the work product from the OLD install to the NEW one via a different hard drive.   (I can boot to any of the three and their recovery .  They are shown on /dev/sda5, sda6 and sda7.  I want to uninstall or delete, whatever term is correct the OLD installation of 24.02.  I do not know how to do this without losing the NEW 24.02.
I appreciate your patience and help.

---

### Post by yancek on 2024-07-08
You need to determine on which of those partitions you have each OS.  If you boot the new Ubuntu 24 and run:  df -h in a terminal  you can determine which partition it is on.  The example below shows the system booted is /dev/nvme0n1p4  show in the output below.  You can tell that is the / partition of the booted system because of the / symbol on the far right.

```
 /dev/nvme0n1p4   47G   26G   19G  58% /

```

Once you know which partition 24 is on you can mount the other partitions  and navigate to that partition to find the /etc/issue file which will show the release as in the  output below showing Ubuntu 22.04.

> cat /etc/issue
Ubuntu 22.04.4 LTS \n \l


If your new Ubuntu 24 is on sda 7 you can use:  sudo mkdir /mnt/sda5, then sudo mount /dev/sda5 /mnt/sda5 to navigate to that file:  cat /mnt/sda5/etc/issue should output the information.  Repeat the steps for sda6 or sda7, whichever it is.

---

### Post by lragan2 on 2024-07-09
Starting over has been reasonably smooth.  Thanks to all of you for your time, attention, and advice.
I discovered that gparted could be dowloaded and used, so it was not necessary to work from the Ubuntu ISO on my USB stick.  I simply deleted the corrupted OS installation, after saving the work product to a separate hard drive.
KiCad is a good design system for circuits and printed circuit boards.  I uses a lot of memory.  
One reason I "mis-spoke" calling the problem "memory' instead of "hard drive space" is that I use a SSD.  Looks, feels, and smells like memory to this 84 yr. old circuit designer.

---

