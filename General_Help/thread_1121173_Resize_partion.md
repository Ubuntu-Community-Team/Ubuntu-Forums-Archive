---
title: "Resize partion"
date: 2009-04-09
forum: General Help
---

### Post by dubstar92 on 2009-04-09
I'm currently dual-booting vista and ubuntu. Is there any way I can shrink the vista partition and expand the ubuntu partition into the new space leftover. I don't have my original vista dvd, just in case that matters.

---

### Post by FrankT-Qc on 2009-04-09
Don't forget the 11th commandment : Thou shall have a backup...

Anyway, what you should do :

From within Vista, you can go to Administrative Tools->Computer Management and then go to the Storage / Drive section... From there, you should be able to shrink your partition.

Unfortunately, you will be limited because you wont be able to move used files... Close as many programs as you can (feel free to kill all those unnecessary services as well) before you shrink...

You could also use a live CD (do a backup, do a backup, do a backup...) and try to mess with your NTFS partition buy only if you're a cowboy... One of the thing that I have seen happening when one resizes it's windows partition without it being mounted is that the page file ends up being fragmented... Quite uncomfortable for an OS that relies so heavily on it...

Give the Windows way a try and see if you feel like you freed enough room before going the liveCD way...

Oh... and don't forget to do a backup

Have fun

---

### Post by dubstar92 on 2009-04-09
could this ruin vista and require me a to buy a new vista installer, or do I just needed too back-up all my files. Also, if it does mess up my vista, would the recovery drive that came built into my computer bring it back to how it was before the resize?

---

### Post by FrankT-Qc on 2009-04-09
Well... yes and no...

From within Vista, I have never seen it fail but it's still known to be a little risky.

If you backup only your files, you still could mess your boot record and make Windows stale (Windows haters should start making joke after this comment...). Doesn't Vista offer you the possibility of creating a recovery image from your current installation ??? I don't have an installation at hand to confirm though... If you use the recovery drive that came with your computer, I'm pretty sure you'll go back to how it was when you bought it (no one can tell except your documentation...)

Anyway, you could do a backup of your master boot record too...

You should google this exhaustively before you start playing with your MBR (master boot record) but here's a hint : Let's say that your MBR was on device sda, then the following code at the shell prompt (as root)

```
dd if=/dev/sda of=/home/me/myMBR.bkp bs=512 count=1
```

would copy your MBR to the file /home/me/myMBR.bkp ... (credits to M. [Sander van Vugt]("http://www.apress.com/book/view/9781590599235") for this one, sorry for somewhat publicizing, but it's a damn good book)

BEFORE YOU RESTORE A BROKEN MBR ... You should be ready to face a broken file system too... If you have fooled around since your backup, you will not want to restore the 512 bytes of your MBR or that would also overwrite your new partition table... Actually, the partition table sits at byte 447 and up so restoration could look like

```
dd if=/home/me/myMBR.bkp of=/dev/sda bs=446 count=1
```

That brings me to an even easier solution... This code, from a LiveCD (i.e. your hard drive not mounted)

```
dd if=/dev/sda of=/path/to/PlentyOfRoom/MyWholeDrive.bkp
```

Would make a complete copy of your drive that you could write back (including MBR) if something would fail to go back to how it was before resizing... Be aware that it's an overnight thing if your drive is big. Of course, this assumes that you have enough room on, let's say, an external drive and that this drive can handle large files...

--EDIT--
When I say that your drive should be able to handle large files, I mean that the file system on your hard drive has to be able to do it... per example, FAT32 (very common for external drive) stops somewhere at 2GiB... go [there]("http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits") to see what your's can take
--END EDIT--

Don't forget to replace "sda" with whatever your hard drive is...

---

### Post by Yvan300 on 2009-04-09
If you repartition using the live cd, most likely vista's mbr will be currupted and will require your vista recovery disk or the installation disk. But if you do it from within vista, using the built in function (which is a bit buggy and does not provide great functionality) then everything may occur without problems. But take care and backup because bill gates was never seen to fulfill his promises :)

---

