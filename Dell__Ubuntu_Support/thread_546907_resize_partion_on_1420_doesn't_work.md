---
title: "resize partion on 1420 doesn't work"
date: 2007-09-09
forum: Dell  Ubuntu Support
---

### Post by deserthowler on 2007-09-09
I  decided to resize the factory install of Ubuntu on my 1420n before I had too much work done on the computer just in case something failed.  I wanted to create a new partition to install Gutsy for testing.

I rebooted into gparted 0.2.5-4.  it showed the partitions fine.  I reset the partition size and hit the apply button.  It worked for a while and said it couldn't do the resizing. 

Up to now, I've had no problem resizing with this program.

Earl

---

### Post by HangLoose on 2007-09-10
What did it say exactly?

---

### Post by blackhowling on 2007-09-10
if u grab the gparted live CD [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)
that usually works for me hit enter, enter, type out Forcevideo then type vesa for it to work on 1420n

---

### Post by gbrainin on 2007-09-10
I had a problem with gparted (running off the Feisty live CD) in that it kept trying to mount all the unmounted partitions.  It can't resize or set up a filesystem on a mounted partition, so it fails.  I should figure out how to get it to not mount the partitions in the first place, but manually unmounting solved my problem in the short term.

---

### Post by notwen on 2007-09-11
Having no issues whatsoever resizing my 1420n's partitions.  Could you give more details on what you're doing and the error coming up once it fails?

---

### Post by blackhowling on 2007-09-11
use the gpart live cd and you won't have those errors.

---

### Post by deserthowler on 2007-09-13
I used the gparted 0.2.5-4 CD.  I use that exclusively with no problems that can't be solved by using 800x600 video.  I had no trouble with the video working.

I don't remember the exact error message. 

 I clicked on the partition and hit resize.  I chose 70 GB, about 1/2 of the disk.  I have only about 13 GB of disk space used.  I hit apply and it went to work.  

I took a shower and it was still working os I took the dog out for a while.  When I came back,  it was done with some message saying it didn't work.  

I didn't record the message because I figured I would have to reinstall.  It told me it would try to recover and might screw up the installation.  I told it to try to recover and rebooted when it was done.  Ubuntu worked and I decided not to go there again.

I just posted this to see if anyone else had problems or not.

Earl

---

