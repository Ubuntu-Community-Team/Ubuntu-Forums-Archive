---
title: "How To Disable Ubuntu OS Probing and GRUB (multiboot)?"
date: 2013-03-08
forum: Desktop Environments
---

### Post by noloader on 2013-03-08
Hi All,

Ubuntu's OS Prober may not pick up Fedora 17 or Fedora 18 on miltiboot systems ([there's an open bug report]("https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/1038093")). Apparently Fedora changed something in [FONT=courier new]initrd[/FONT] that has upset Ubuntu's prober which causes grub to drop menu entries. When GRUB is modified with Ubuntu's version, the F17 and F18 versions do not show as a boot selection (this seems to be a separate Ubuntu problem). Though reported in August 2012 (9 months ago), [its still not fixed]("https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/1038093").

I want to disable Ubunut's OS Prober and updating of GRUB since Fedora picks up all the OSes. How do I disable Ubuntu's boot related stuff, such as its OS Prober and GRUB?

Since this is a test system that multiboots, I need Ubuntu's update process to still work on 3 flavors of Ubuntu (11.10, 12.04, and 12.10). (The system also has two Windows hosts and two BSD hosts).

Thanks in advance,
Jeff.

---

### Post by dabl on 2013-03-10
I may or may not understand what you are asking .....

If the Fedora os-prober is working as you need, and Ubuntu's is not, then why not reinstall grub-pc from Fedora, and delete grub-pc and os-prober from each Ubuntu?  I see no reason why this should interfere with Ubuntu updates, if you have removed grub-pc and os-prober from the Ubuntu OS's.

---

### Post by oldfred on 2013-03-10
Fedora usually installs to lvm and Ubuntu does not include lvm driver as standard. If you install lvm driver and mount the Fedora partition os-prober will work.

       sudo apt-get install lvm2

If you want to turn os-prober off.
      
 Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober

Debian based systems have links in / (root), so you can boot the partition and always boot the most current kernel. Not sure about other distributions. But by booting a partition, you can just create one permanent entry in 40_custom to always boot the newest version with out having to boot both installs and running updates.

[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Making_the_custom_Grub2_Menu_entries-1](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen#Making_the_custom_Grub2_Menu_entries-1)

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

---

### Post by xana40 on 2013-03-31
I understand the problem. I have ubuntu 12.04, linux mint, vista, and opensuse. I did have fedora 18 also, but opted out of that one. It seems that the "red hat" distos use a grub 2.0 and the "debian" (ubuntu and mint) use a grub 1.99. I did not use lvm so that is not even a consideration.

The problem only came up with the ubuntu automatic updates. I wasn't paying attention and it updated it's grub and completely wrote over my opensuse grub which I was using. All those annoying menuentries re-appeared and fedora disappeared. You basically have to have the fedora partition mounted while the os prober is doing it's thing. I rewrote with opensuse grub 2.0 and have the nice grub back. Linux mint doesn't seem to do the auto gub update so it hasn't been a problem so far. It may have to do with the way I installed the mint os because I might have selected to install grub to the partition.

I'm not sure what disabling the os prober in the ubuntu grub file would get me, because that grub isn't the one that's currently loading. If I could manually tell ubuntu's updater to leave the grub out that would be good. Hope this helps clarify.

---

### Post by oldfred on 2013-03-31
Grub remembers where to reinstall. This should let you change that location so it does not reinstall to the MBR. You could install to partition more as a throw away like you did with Mint. As long as you have another grub that will find & boot your installs it does not matter that grub is in a partition. It just is that is not normally recommended. If you do not select anything, I believe it does not reinstall on updates.

 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

