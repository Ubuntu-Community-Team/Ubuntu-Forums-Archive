---
title: "USB stick became 'Read Only' how to change"
date: 2008-02-02
forum: Desktop Environments
---

### Post by nicenick on 2008-02-02
Ubuntu 7.10
JOGR 8GB USB drive.

When I first started using this USB drive, everything was perfect.  Then slowly, especially when moving things to trash, Files and or Folders would become 'Read Only'.  No problem, use Nautilus to change the permissions back to Read and Write.  Slowly, over weeks the problem became worse, more file and more directories would become Read Only, even during multiple file transfers, begining files would transfer and suddenly folder became Read Only and the rest of the files could not transfer.

Well finally today, the Whole USB Drive became Read Only.  Now I can not delete, empty trash,or transfer files to the entire drive.  I can not change permissions because " Read Only Drive". I do not have permissions to the drive.

When I plug in the USB drive, It just shows up on the desktop and launches into the root of the USB drive (a single folder with many subdirectories

How can I force permissions (or tell it that it is a read and write drive) back into the USB drive?

I use only Ubuntu 7.10, no NTFS partitions or Windoze on my desktop at all.  I do not ever plug the USB stick into other computers. USB stick is formatted vfat (came out of the box that way and worked, so why bother to change it).

---

### Post by nicenick on 2008-02-02
OK, found out something, maybe useful.
I closed Nautilus, Disk is showing on desktop. Then I pulled down 'Places' clelcked 'Computer' Right Clicked on USB 2.0 Disk and selected, Unmount, then Mount, then Unmount again and it ased me if I wanted to empty my trash, I did and it worked. 
I removed the USB drive, rebooted my computer and then reinstalled the USB drive.  When Disk appeared on the desktop, I changed permission to Read and Write,  Applied permission to enclosed files.

Now everything works again.

Solved?? No I do not think so. I think this only a work around until I can find out what is changing permission to Read Only on the fly and locking me out of the disk.

---

### Post by nicenick on 2008-02-02
Well that lasted only 3 minutes.  I did not even transfer any files. When I finished my reply, I went back and opened the drive on my desktop and BEHOLD nice little locked icon on the folder and entire drive is 'READ ONLY' and can't change permissions etc, 

Any idea what is happening and how to prevent it?

---

### Post by jphekman on 2008-02-03
I've been having the exact same problem. I did find some interesting pages about it via google ("ubuntu usb 'read only'"), the best being at

[http://https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/61235]("http://https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/61235")

So apparently there actually is a bug. Some people fixed it by upgrading to gutsy (I'm on feisty) but it looks like you're already on gutsy.

But then I found an Ubuntu help page that suggested fscking my thumbdrive (and I did unsafely eject it a few times so it could have been dirty) and I thought why not:

# dosfsck -a -v /dev/sdb1

And that fixed it (so far)!

Good luck,

Jessica

---

### Post by CodeNosher on 2008-02-04
[SIZE="2"]What a life saver!!  I just bought a 4gig drive and stuck it in an old machine with xubuntu on it.  I don't know if I pulled it out too soon or not since ubuntu always tells me it is unsafe to remove the drive.

Anyway the new drive showed 62 files that where of type unknown, size unknow and all had names that were just flat weird, such as:
[/SIZE]
&#9532;&#9566;&#9567;&#9562;&#9556;&#9577;&#9574;&#9568;.&#9552;&#9580;&#9575;
????????.???
+,-./012.345
FGHIJKLM.nop
lmnopqrs.tuv
%&'()*+,.-./
????????.???
,-./0123.456
ghijklmn.opq
lmnopqrs.tuv
&#9566;&#9567;&#9562;&#9556;&#9577;&#9574;&#9568;&#9552;.&#9580;&#9575;&#9576;
????????.???
àåçêëèïî.ìäå


[SIZE="3"]To fix it I ran:
[COLOR="Navy"]**dosfsck -r -v /dev/sdb1**[/COLOR]

-a didn't work so I used -r and told it to delete anything it couldn't figure out.

Viola! It works.[/SIZE]

---

### Post by sunny_nwho on 2008-02-05
> **CodeNosher said:**
> [SIZE=2]What a life saver!!  I just bought a 4gig drive and stuck it in an old machine with xubuntu on it.  I don't know if I pulled it out too soon or not since ubuntu always tells me it is unsafe to remove the drive.

Anyway the new drive showed 62 files that where of type unknown, size unknow and all had names that were just flat weird, such as:
[/SIZE]
&#9532;&#9566;&#9567;&#9562;&#9556;&#9577;&#9574;&#9568;.&#9552;&#9580;&#9575;
????????.???
+,-./012.345
FGHIJKLM.nop
lmnopqrs.tuv
%&'()*+,.-./
????????.???
,-./0123.456
ghijklmn.opq
lmnopqrs.tuv
&#9566;&#9567;&#9562;&#9556;&#9577;&#9574;&#9568;&#9552;.&#9580;&#9575;&#9576;
????????.???
àåçêëèïî.ìäå


[SIZE=3]To fix it I ran:
[COLOR=Navy]**dosfsck -r -v /dev/sdb1**[/COLOR]

-a didn't work so I used -r and told it to delete anything it couldn't figure out.

Viola! It works.[/SIZE]

I had the same problem but i used the chkdsk /f command from Windows. 

Thanks for the new command mate..

---

