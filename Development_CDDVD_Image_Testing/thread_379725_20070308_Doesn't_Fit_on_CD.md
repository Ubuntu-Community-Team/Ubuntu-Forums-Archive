---
title: "20070308 Doesn't Fit on CD"
date: 2007-03-08
forum: Development CD/DVD Image Testing
---

### Post by jerrylamos on 2007-03-08
Latest Herd (5?) 20070308 doesn't fit on CD-RW or CD-R either.  It's 738,691,072.  Yes, the MD5SUMS check.  By the way, Knoppix at 730,177,536 does fit.

Please let us know the image is too big for a CD before we burn up time and internet traffic.  I wonder, does someone check out cdimage after it is loaded?

Thanks, Jerry Amos

---

### Post by Rooy on 2007-03-09
Hi, there should be a file named feisty-<disk type>-<arch>.OVERSIZED in the folder when the corresponding image is too big to fit onto a 700MB CD.

I advice you to use rsync to update the disk image rather than download one every time. My rsync command is like this:

rsync -vvhh --archive --partial --progress --compress --stats --perms --copy-links rsync://cdimage.ubuntu.com/cdimage/daily/current/feisty-alternate-amd64.iso .

The link add one directory to the normal http link: ubuntu.com/**cdimage/**daily/,
 and the protocol is rsync.
--partial only downloads the different part between your image and the one on the rsync server, --compress zips the transferred chunks. Other switches are mostly for verbose info, i think (copied from somewhere else). Rsync guarantees a correct image, unlike HTTP and FTP downloads :)

---

### Post by kerry_s on 2007-03-09
Fiesty net installer, it will always be up to date :) -> [http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso](http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso)

---

### Post by jerrylamos on 2007-03-09
Thanks, I did see the "Oversized" iso with a 0 size and didn't realize it's significance.

I rsync'd (as usual) 20070309, using up some server and internet time, and it is oversized too.

I presume if the word "Oversized" shows up, not worth trying.

Thanks for the explanation.

Cheers, Jerry:(

---

### Post by jerrylamos on 2007-03-09
Took a look at Feisty net installer.  We have 5 different computers on our LAN, so what I usually do is make a CD Live Persistent set and play "ordinary desktop user" using Ubuntu CD Live "out of the box" to check out to see what runs and is broken on the several computers.  I haven't tried an install since Herd 2 wiped out the partition table.  Maybe if Feisty Beta looks more solid than Feisty Alpha, I've a number of bugs posted on launchpad.  However Persistent has been broken since 20070207, see launchpad.

More and more Linux distro's have USB installs, and USB's are getting bigger, which makes for a nice state of hardware independence for an "ordinary desktop user".

So perhaps "net installer" would get around the problem of Oversized, however that doesn't get a CD Live for the "ordinary desktop user" (see Official Ubuntu Book for definition).

So I did download net installer in case it might be of use sometime.  Thanks.

Cheers, Jerry Amos

---

### Post by cesium62 on 2007-05-27
I started downloading ubuntu-7.04-desktop-i386.iso from Monterey Bay CSU.  I immediately realized there was a very small chance that the whole thing would download, but left it running and went upstairs to see if I could get a copy off of emule.  Emule did appear to have the same software.   The next day, emule had downloaded the image and the download from CSU had stopped after 10MB, but the download window didn't particularly say that the download was broken.

Of course, when I try to write to the CD, I'm told that there are 697MB to be written to a 656MB CD.  Must be nice having big fat CDs.  It would be slightly easier for us to move away from Windows if we could shrink the image by about 1%.

recommendations:  (1)  Don't bother supplying ftp links to download mirrors.  the probability of being able to pull a big file is small.  (2)  Sure would be nice if we could download a small binary to a CD initially and upgrade components over the internet later on.

I'll go look and see if I can find a smaller linux iso somewhere...

---

### Post by loadfoo on 2007-05-28
net installer ???
This the matter that was not possible to user that did not have the internet connection.

but how if your new package compressed with LZMA compression. [squashfs lzma patches]("http://www.squashfs-lzma.org/")

sorry for my bad english.

---

