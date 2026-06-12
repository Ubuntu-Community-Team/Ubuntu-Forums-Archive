---
title: "How i achieved GRUB &quot;Error 17&quot;"
date: 2009-06-11
forum: General Help
---

### Post by Mycle on 2009-06-11
5th attempt at installing and using Ubuntu. This time Ubuntu Server 9.04 Jaunty Jackalope.
Ubuntu to date has been problems at every step. That's OK, I'm sufficiently masochistic for the job, if not bright enough to stroll through the process unscathed.  
I'm attempting to minimise the problems to no more than one per step. So, instead of Dual/Multi-booting with Windows
I have Windows on HD0 and Ubuntu on HD1. I choose which OS to run by Changing the BIOS boot order at start-up (F11).

To help in early-learning the configuration of Ubuntu Server I installed the GUI. 
I read there's a way of switching between the GUI and Command-line option at boot up but I didn't sort that one yet.

I did struggle for quite a while getting the video driver working. After some searching I used the "ENVY" utility to do the config automatically.
Such a sense of relief followed the success of that step that I got the urge to image the Linux partitions before going any further.

I chose to use Terabyte's Image for Linux for this job partly because I bought it as part of a bundle which included BootItNG, this for when my 
boot options need to get more flexible.

On the first run of the "Image for Linux" software I got the error message:
"Problems were found in the list of partitions".
Terabyte Support responded that: 
"One of the linux tools creates invalid extended partitions that has volumes that jump over other volume (mainly the first one which should always be the beginning).  If you use windows to add or remove a partition of any type, it will reorder it."

The only relevant partition that WinXP would let me delete without major damage to Ubuntu was the extended partition holding the small Linux-Swap partition and a larger NTFS partition which was set-up to be a shared file location. I then rebuilt the extended partition in WinXP. With GParted I remade the Linux-Swap and the NTFS partition.

Sure enough, no more error message in "Image For Linux" when I cloned the Ext3 Linux Boot partition. :-)

BUT now when I try to boot Ubuntu, I get GRUB "error 17". On reflection I suppose it's pretty obvious that I would.
What isn't so obvious to me is which files I need to edit to get back to a successful boot of Ubuntu.
I did several searches and saw many varied suggestions which included potentially a lot of files to change to overcome the "Error 17" problem.
I'm hoping that someone can tell me the files I need to change regarding these specific circumstances.
Please.

I don't have a record of what the partition order was before the "cure". GParted shows the current partition order as:

/dev/hdb1	ext3	,,,	boot		   
/dev/hdb2	extended	,,,	lba		   
       /dev/hdb5     linux-swap				   
       /dev/hdb6	NTFS

---

### Post by zvacet on 2009-06-11
Maybe [this]("http://members.iinet.net.au/~herman546/p15.html#17") will be helpful.

---

### Post by Mycle on 2009-06-11
> **zvacet said:**
> Maybe [this]("http://members.iinet.net.au/~herman546/p15.html#17") will be helpful.

Thanks. The info on the link suggested that at this stage of Ubuntu development, all that should be necessary to solve GRUB Error 17 problems is to do a file system check. I did one of these with GParted but on reboot the error remained. There were further suggestions that were only to be associated with older versions of Linux. Maybe I should try some of these.
--
Regards,
Mycle

---

### Post by Mycle on 2009-06-16
Ok, just in case it's of any help to anyone in the future, my Grub and Ubuntu Server 9.04 are functional again.

I followed the instructions on [this]("http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/") page.

Although the menu.lst and fstab in Ubuntu Server 9.04 use UUID to identify the partitions, rather than the earlier method, I found that reinstalling GRUB which doesn't use the UUID, brought Grub and Ubuntu back to health once again.

---

