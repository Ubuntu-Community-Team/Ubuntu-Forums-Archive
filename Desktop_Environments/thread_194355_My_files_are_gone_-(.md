---
title: "My files are gone :-("
date: 2006-06-11
forum: Desktop Environments
---

### Post by Sandsound on 2006-06-11
This morning I had a ntfs with about 24Gb mp3-files (my whole cd-colection), but because I couldnt write to ntfs from Linux, I thought... why dont I convert this leftover of my windoze system to ext3... Now I have absolutely no ide where my mp3-files have gone and my Linux partition is taking up about 35Gb ???

This is what I did :

I copied all my mp3-files from my 80 Gb ntfs disk (hdb1) to my 80Gb Linux disk (hda1), this took about 20 minutes and after this I made shure that ALL the files were there.

Then I converted my ntfs disk to ext3 (useing gparted), made a partition wich i mounted in fstab and rebooted (just to be on the safe side).

Then I copied my mp3-files from my linux drive (hda1) to my new empty ext3 disk (hdb1), and again... made shure that ALL the files were there.

Then i rebooted my pc, and now my new ext3 disk (hdb1) is empty and my Linux partition is taking up 35Gb space ???

I cant figure this out... ?

From what I can read on the web, it is not possible to recover erased data from a ext3, at least not if i have emptyed my wastebasket (wich I ofcourse already have done :-( )
I cant find any mp3-files when i search useing "Places > Search for files", and they are not in my wastebasket, have even tryed to run "sudo su" and try to search my user-trash and my root-trash... all gone :-( ?

---

### Post by Sandsound on 2006-06-11
Hi again...

I can live with having to rip all my cd's once again, but right now I cant get any further with my ubuntu :-(
I wanted to make an image of my Linux today (useing partimage), so that i can play around with it without having to reinstall everything again (finaly have a perfect working amd64 installtion with ardour and other cool apps... or at least I thought so), so if I could just solve the problem with my Linux partition taking up all this space, i would be werry happy.

---

### Post by Anduu on 2006-06-11
Something similar happened to me...I made the mistake of copying all my files before I mounted the new partition.After I mounted it they were gone but my disks utility still showed that space as being used.
I unmounted it and browsed back and my files were there again.

Try this....

Remove the entry from your fstab for your new partition then reboot.

Now browse to the location you made as the mount point for the new partition and see what is there.

---

### Post by sarhento_lobo on 2006-06-11
What size was it before? Are you sure that the files aren't just hidden?

---

### Post by elbryan on 2006-06-11
Happened with me a few time ago to delete a partition for error...
I used "Stellar" ([http://www.stellarinfo.com/]("http://www.stellarinfo.com/")) to recover almost all the data ...

I saw that this program can recover from Linux partition too but I think it's only a Windows program..

---

### Post by Sandsound on 2006-06-11
[QUOTE=Anduu]Remove the entry from your fstab for your new partition then reboot.
Now browse to the location you made as the mount point for the new partition and see what is there.[/QUOTE]

Yahoo... they are back... all my mp3-files :D 

Cant believe how this could have happend, thought I knew what I was doing here :oops: 
Still.. cant understand why I couldnt see any mp3's at all in my search ?

Thanks Anduu... just saved me for several hours of ripping.

---

### Post by Anduu on 2006-06-11
Cool glad I could help....:D 

Now your next step should be to clean out  all those mp3's from your new partition then remount it.Then reboot and test a couple times to make sure you can put stuff there(rebooting each time of course...)and still find it.

When you are ***positive*** it is functioning correctly you can copy your mp3s over again ;-)

---

