---
title: "HowToRemoveWindows (make better use of your HD) ; request for help"
date: 2005-12-03
forum: Desktop Environments
---

### Post by walterBE on 2005-12-03
Hi,

Many users of Ubuntu will have started first with a Windows-only pc and added Ubuntu on it so the have a dual-boot computer. 

After some time I belive a fair amount of those users will come to the conclusion; why am I wasting so mush harddisk space for that Windows installation I not even use anymore? So the would like to remove it safely and use that space for there Linux installation.

Or at least reduce the size of the partition of the Windows-partition to the minimum.

I am now in that situation.  I have 40gb  for an Windows installation that I do not use. I would like to reduce it to 8 gb and use the the rest for Linux.

I have been looking on the internet about a howTo about his. The only one I have found is one of 1999. That seems to me not a good idea to follow this if you do not know mush about it.

So I ask here for help. Not only for my but for all Ubuntu-users. I have made I page on the Wiki to write down the advice how to to this. 
[https://wiki.ubuntu.com/HowToRemoveWindows]("https://wiki.ubuntu.com/HowToRemoveWindows")

This really something where should be information about it. I hope for the help  of all you knowlegeable people to help make this HowTo.  Help the users of Ubuntu to get rid of Windows in a save way.

Thanks in advance!

Walter

---

### Post by tommythecat on 2005-12-03
I could be wrong, but the only way I know of to do this is with a 3rd party disk management utility.  

I regularly use Acronis Disk Director to reduce the size of fat32 and ntfs partitions without damaging the windows installs on them.  I do not have any idea how you would add that space to an existing linux formatted partition, but it would be really easy to create an aditional linux partition if that meets your needs.

---

### Post by tomchuk on 2005-12-03
To shrink your Windows partition from 40 to 8GB:
1. Boot into Win and defrag your filesystem.
2. Boot up the Breezy LiveCD and start up gparted.
3. Shrink your Windows partition by half.
4. Reboot into Windows, let chkdisk run, defrag the drive again.
5. Go to 2 repeat as necessary.

You can only shrink an NTFS partition by 1/2 each step - there is a MFT mirror in the middle of the partition which limits how much you can shrink it.

You can then repartition the free space or grow your existing partitons to fill.

---

### Post by walterBE on 2005-12-03
[QUOTE=tomchuk]
You can then repartition the free space or grow your existing partitons to fill.[/QUOTE]

Thanks. This looks like a good big step in good direction.

And if I want to remove Windows totaly I boot with the live cd and I delete the partition? 

To grow the existing partition; you mean that when you are booted from the live cd and use QTparted to grow the existing partition? Does it is a problem that the Windows partition is a primari and the others extended? 

Thanks for your advice

---

### Post by tomchuk on 2005-12-03
[QUOTE=walterBE]Thanks. This looks like a good big step in good direction.

And if I want to remove Windows totaly I boot with the live cd and I delete the partition?[/QUOTE]Yup

> To grow the existing partition; you mean that when you are booted from the live cd and use QTparted to grow the existing partition? Does it is a problem that the Windows partition is a primari and the others extended?

Yup, gparted should be able to do everything you need. As long as your linux partitions keep the same partition numbers, grub and /etc/fstab should be fine, if they don't you might need to make some changes.

---

