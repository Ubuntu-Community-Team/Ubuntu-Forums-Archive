---
title: "How do I uninstall Debian on dual-boot laptop with Ubuntu OS and Debian OS?"
date: 2013-12-10
forum: Debian
---

### Post by michael2009 on 2013-12-10
I own an HP Pavilion Sleekbook 14 with Ubuntu 12.04 LTS installed. A few weeks ago I installed the latest Debian (Wheezy?) as a dual boot system alongside Ubuntu. Both work fine, but I have decided to uninstall Debian because I cannot get my grey head around a new system with commands that don't seem to work or are not as straightforward as Ubuntu (for example, tried using the same commands as I used in Ubuntu for installing the wireless drivers in Debian with no success). 

Having decided to uninstall Debian, I am worried about losing my precious Ubuntu 12.04 with all the updates in the process, as this has already happened to me several times in the past when trying to install or uninstall another OS alongside Ubuntu. 

It may be relevant to note that Debian installed its own GRUB over Ubuntu, resulting in an overcrowded and laborious boot menu. When I select Ubuntu and press enter, the next screen is blank except for this message:

error: no argument specified 
Press any key to continue...

When I press a key, Ubuntu starts up normally. 

So, essentially, I just want to uninstall Debian together with the Debian GRUB, and revert to my original single boot into Ubuntu, which was very smooth, fast and error free. Is there a straightforward way of doing this, without losing my original Ubuntu installation?

Any advice would be much appreciated :)

---

### Post by oldfred on 2013-12-10
Are you able to boot into Ubuntu from Debian, if so install Ubuntu's grub back into the MBR. Once tested that you can boot Ubuntu directly, you can use gparted to delete or reformat the Debian partition. If a logical partition you will have to use gparted from Ubuntu live installer or download gparted's live ISO or PartedMagic's ISO. With live installer swap is usually mounted for faster installs, so in gparted click on swap and right click swap off. I do not think gparted live ISO mounts swap automatically.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

If that does not work or you have additional issues post the link so we can see details.
      
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by michael2009 on 2013-12-11
Re: [http://ubuntuforums.org/showthread.php?t=2192967](http://ubuntuforums.org/showthread.php?t=2192967)

> **oldfred said:**
> 

... If that does not work or you have additional issues post the link so we can see details.
      
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Thank you for your assistance. I booted into Debian and followed your instructions for reinstalling the grub. I haven't succeeded yet as the following output shows:


admin@debianjisec:~$ sudo fdisk -l

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for admin: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00047e54

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    64452607    32225280   83  Linux
/dev/sda2        64454654   976771071   456158209    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5        64454656    67383295     1464320   82  Linux swap / Solaris
/dev/sda6        67385344   937697843   435156250   83  Linux
/dev/sda7       937699328   976771071    19535872   83  Linux
admin@debianjisec:~$ sudo grub-install /dev/sda1
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.
admin@debianjisec:~$ sudo grub-install --recheck /dev/sda1
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.
admin@debianjisec:~$ 

Perhaps I should install the boot-repair?

---

### Post by oldfred on 2013-12-11
You want to boot into Ubuntu not Debian and install grub to the MBR (sda) not a PBR (sda1) which is a partition boot sector. 

Only if booted in Ubuntu as whatever you have booted it reinstalled to MBR.  Note sda not sda1.
sudo grub-install /dev/sda

Computer boots from MBR and only if you have a boot loader in grub from one install is it even possible to have a grub in a PBR work. Plus it pointed out the disadvantages of grub in a PBR.

---

### Post by michael2009 on 2013-12-12
Thanks for your reply. Unfortunately I forgot to mention that I lost access to Ubuntu the day after my first post on this thread. After selecting Ubuntu on the grub menu, it appears to be is booting but then a text appears on the blank screen reading: 

broken pipe.

I cannot get beyond this screen even in recovery mode. I shall try to boot in recovery again, & try to make a note of any errors or related messages that I find, then I shall post them here if that's ok with you.

 This happened BEFORE I tried reinstalling the grub in Debian, and I understand now from re-reading your posts that I should have reinstalled grub working from the Ubuntu OS, and on the sda drive, not the sda1 partition. I am sorry, this was my own misunderstanding.

I do not know why I can't boot into Ubuntu, it had been working fine the day before. My son had been using this laptop after me, to access some of his music files, but he maintains that he did not mess about with the system...

---

### Post by oldfred on 2013-12-12
I do not know exactly how to fix broken pipe. But it seems you may have to chroot into it and run updates if you cannot get in with recovery mode boot.
You can chroot from your Debian install, a Ubuntu live installer or Boot-Repair.

These include chroot and just a grub fix. But you may need more.
 To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

      All the # are just comments do not copy or type anything after the # or comment.

 #Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
apt-get -f install
dpkg --configure -a

---

