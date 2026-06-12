---
title: "Sick of this now. USB flash drive"
date: 2009-03-09
forum: General Help
---

### Post by jamesbeat on 2009-03-09
I have just plugged a brand new 16GB flash drive into my laptop to transfer some files to my desktop (both running intrepid) 
When I plugged the drive into the desktop, the contents were corrupt.

I am absolutely 100% certain that I unmounted the drive before removing it from my laptop.

Since I still had the files on my laptop, I decided not to mess around trying to save them, and just format the drive using Gparted.

The drive shows up on gparted, but when I unmount it to format it, Gparted just ends up in a 'scanning all devices' loop.

If I unplug and remount the drive, it shows up on my desktop as usual, but with capacity reduced by 2Gb (the size of the files I put on it)
As an experiment, I tried putting some more files on it, unmounting it and then plugging it back in. Sure enough, the new files are corrupted.

This is not the first time that this problem has happened to me, it happened with an 8GB flash drive that I had too.
I could format it OK with Windows, but then when I tried to use it in Ubuntu the same problem as above would occur. I ended up throwing it away assuming it was faulty.

Is it possible that my drive is faulty, or is Ubuntu causing the problem? 
I no longer have a Windows machine so I can't try using it to format the drive.

And why is formatting a drive so complex anyway? Is there a reason why Ubuntu doesn't have a simple 'format' option instead of having to use gparted?

---

### Post by Zimmer on 2009-03-09
Not just Linux...
[http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16820211149](http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16820211149)

[http://www.compusa.com/applications/searchtools/item-details.asp?EdpNo=3335434&SRCCODE=CNETCMPUSA&cm_mmc_o=2mHCjC2WHaCjCVqHCjCdwwp](http://www.compusa.com/applications/searchtools/item-details.asp?EdpNo=3335434&SRCCODE=CNETCMPUSA&cm_mmc_o=2mHCjC2WHaCjCVqHCjCdwwp)

[http://www.fixya.com/support/t1567106-photos_put_16g_usb_flash_drives](http://www.fixya.com/support/t1567106-photos_put_16g_usb_flash_drives)
[http://hak5.org/forums/index.php?showtopic=9499](http://hak5.org/forums/index.php?showtopic=9499)
To show but a few...

What make is your USB stick?

---

### Post by jamesbeat on 2009-03-09
It's Kingston. 
I did check the packaging and it claims to be compatible with Linux, not that I've had any problems with other drives that weren't marked as Linux compatible.

---

### Post by vanadium on 2009-03-09
I suspect that the drive is not properly closed even though you "unmounted" it. I remember having a similar trouble with a fat16 formatted mp3 player. Even though I unmounted it using right-click on the icon on the desktop, the file system would sometimes be corrupted. I guess it is due to some writing being cached into memory. Is it Ubuntu, or is it the hardware telling Ubuntu it is ready while it is not? I had this with that USB player, but I never have this with my cruzer minidisk.

You can reclaim the lost clusters by running the "dosfsck" utility (you may use the more familiar "fsck" command as well):

First make sure the drive is not mounted. Assuming your USB is /dev/sdc1:
```

sudo dosfsck -a /dev/sdc1

```

Then, take a habit of waiting ten seconds or so before removing the drive from the USB. Perhaps the "eject" command rather than the "umount" command would work better here.

---

### Post by jamesbeat on 2009-03-09
That's interesting.
I have noticed that sometimes I get a message saying that unmounted items are safe to remove, and sometimes I don't, seemingly at random.
I'll give it a go and report back

---

### Post by jamesbeat on 2009-03-09
Ok, I got tired of trying and took the thing back.
Rather embarrassingly, it worked perfectly when the guy in the store tried it on a Windows machine.

Nevertheless, I demanded a replacement, which works fine on my laptop, but not on my desktop.
When I plug it in, nothing happens. Gparted shows nothing except for my HDD.
If I plug it back into my laptop it works fine.

If I plug a different flash drive in, that works fine.

---

### Post by yther on 2009-03-09
> **jamesbeat said:**
> And why is formatting a drive so complex anyway? Is there a reason why Ubuntu doesn't have a simple 'format' option instead of having to use gparted?

As far as I know, you don't *have to* use Gparted to format a flash drive.  I do tons of these things at work and we later distribute them to people running Windows, so I format them with FAT32 using a Bash alias that also copies the files to them:

```
sudo mkdosfs -F 32 /dev/sdb1 && sudo mount -t vfat /dev/sdb1 /mnt/td && sudo cp -v * /mnt/td && sudo umount /mnt/td
```

I can't speak about formatting thumb drives with ext2/3, because I haven't done that yet.  I tried formatting a 1GB drive with NTFS and it went on for several minutes, whereas the FAT32 format takes about half a second.  :?  I eventually gave up and killed the NTFS format because I figured something must be wrong.

I think if I had to transport files on a flash drive and preserve any Linux-specific attributes, the safest thing to do would be to make a bzip2 archive out of them and store that on the drive.  Usually I'm just transporting PDFs or things that are already zipped, so it doesn't matter.

I can feel your frustration, though.  Those things are supposed to be simple and easy to use, not some ordeal where you can't even trust your files to survive!  :(

---

