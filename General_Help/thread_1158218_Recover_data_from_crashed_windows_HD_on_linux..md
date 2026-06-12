---
title: "Recover data from crashed windows HD on linux."
date: 2009-05-13
forum: General Help
---

### Post by trendal.toews on 2009-05-13
Is there any software available that:

#1 Runs on Linux
#2 Can attempt to recover data from a broken Windows Hard Drive.


Something similar to GetDataBack for NTFS?

I cannot seem to find any as of yet.

Thank you.

---

### Post by logos34 on 2009-05-13
[Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") and PhotoRec (CG Security)

make sure universe repository is enabled, then:

sudo apt-get install testdisk

sudo testdisk

or

sudo photorec

[http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)

you could also use dd command (or maybe [ddrescue]("http://www.gnu.org/software/ddrescue/ddrescue.html")) if the drive is dying

---

### Post by trendal.toews on 2009-05-13
I tried testdisk.  Unless I am not understanding it (which is more than possible) testdisk doesn't get any more data than I can get just by browsing the drive with Ubuntu file browser.  I was hoping for something more powerfull than that.

I haven't tried the other program you mentioned. (photorec)

Maybe I am looking for something that doesn't exist......

Edit:  I didn't see that link that you gave me.  Checking it out now.  Looks like I have stuff to learn about TestDisk.

Thanks

---

### Post by trendal.toews on 2009-05-13
Yes photorec is currently recovering data.  [This]("http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/") link got me going perfect. 
Thanks a lot.

I'm running it off of my Ubuntu install though not the cd.

---

