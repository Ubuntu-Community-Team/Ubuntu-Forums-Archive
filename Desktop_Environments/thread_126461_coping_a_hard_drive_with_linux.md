---
title: "coping a hard drive with linux"
date: 2006-02-06
forum: Desktop Environments
---

### Post by redmansk8 on 2006-02-06
I have an old HP that I loaded with ubuntu to learn to use and setup ubuntu which I have running and it runs good but it only has a 10 gig drive and it is almost full I was wanting to put a bigger drive in the computer but I do not want to lose my data! I know with a windows computer you can use Maxblast or western digital setup disk to copy the entire drive to the new drive. But maxblast will not copy a linux drive.

---

### Post by Ramses de Norre on 2006-02-06
Maybe it can when using this program [http://www.fs-driver.org/]("http://www.fs-driver.org/") I never tried but it might be possible.
Just give the linux drive a drive letter with this program and it should be accesable then.

---

### Post by cwaldbieser on 2006-02-06
[QUOTE=redmansk8]I have an old HP that I loaded with ubuntu to learn to use and setup ubuntu which I have running and it runs good but it only has a 10 gig drive and it is almost full I was wanting to put a bigger drive in the computer but I do not want to lose my data! I know with a windows computer you can use Maxblast or western digital setup disk to copy the entire drive to the new drive. But maxblast will not copy a linux drive.[/QUOTE]
Ghost for Linux : [http://sourceforge.net/projects/g4l]("http://sourceforge.net/projects/g4l")

or gparted should do the trick.

---

### Post by ardchoille on 2006-02-06
There is an app called partimage that can do what you want. Here's what I do:
1) Install Ubuntu on a mchine
2) reboot to a LiveCD that has partimage (I use sysresccd but MEPIS also has partimage)
3) run partimage to image the hard drive and burn the resulting image to a CD or DVD (MEPIS is great for all of this because it has partimage and K3b)
4) run partimage on the next computer and use the image from the first computer as the source to populate the second computer's hard drive

Partimage is available here: [http://www.partimage.org/](http://www.partimage.org/)

There is a System Rescue CD that has partimage on it, that rescue CD is available here: [http://www.sysresccd.org/](http://www.sysresccd.org/)

---

### Post by htoerrin on 2006-02-07
I'm not shure that I fully understand your problem, but there are several ways to take care of an old HD, depending on you wanting to reinstall ubunto, or not.

If you can fit another drive, you could just fit the new one, and continue to boot from the old drive. You would move some of the content from the old to the new drive to free up some space, eg /usr and /home.

If you want to get rid of the old drive, you could mount both drives, and use dd to copy the old one to a file on the new one. Assuming the old drive is sda, you would do this as root

dd if=/dev/sda of=<some filename on the new drive>

To access the files, you would mount this file to an empty directory

mount -o loop <image filename> <empty directory>

Or you could simply mount both drives and copy the contents with rsync

rsync -av <source dir> <destination dir>

Good luck, and be shure to read the man pages :-)

---

