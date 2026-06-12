---
title: "Write permissions in a mac-formatted iPod"
date: 2006-06-02
forum: Desktop Environments
---

### Post by darteaga on 2006-06-02
Hi all,

I have an hfsplus-formatted iPod, and I'd like to use it as a disk under Ubuntu Dapper. It mounts automatically and I can read files from it. The problem arises when trying to copy a file to the iPod. It complains "Read-only filesystem". However, as far as I understand, the iPod is mounted with write support. Here is the output of mount.

/dev/sdc3 on /media/ipod type hfsplus (rw,nosuid,nodev,uid=501,gid=100)

If I remember well, I could transfer files to the iPod under Ubuntu 5.10 (I just upgraded to Dapper)

Any idea? Many thanks,

Dani

---

### Post by corefile on 2006-07-02
I had the same problem, and I just got it working.

There seems to be some issue with journal hfs+ and 2.6.15 kernels (shipped in Dapper).
[http://www.ussg.iu.edu/hypermail/lin...11.0/0941.html](http://www.ussg.iu.edu/hypermail/lin...11.0/0941.html)

You have to disable the journal on your ipod for the kernel to mount it read/write. To do this I plugged my ipod into a mac and ran
diskutil disableJournal /Volumes/iPod

The instructions I followed are here:
[http://gentoo-wiki.com/HOWTO_hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus)

---

### Post by darteaga on 2006-07-03
[QUOTE=corefile]I had the same problem, and I just got it working.

There seems to be some issue with journal hfs+ and 2.6.15 kernels (shipped in Dapper).
[http://www.ussg.iu.edu/hypermail/lin...11.0/0941.html](http://www.ussg.iu.edu/hypermail/lin...11.0/0941.html)

You have to disable the journal on your ipod for the kernel to mount it read/write. To do this I plugged my ipod into a mac and ran
diskutil disableJournal /Volumes/iPod

The instructions I followed are here:
[http://gentoo-wiki.com/HOWTO_hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus)[/QUOTE]

Thanks a lot for the info. Do you know if disabling the journal can cause any problem?

I think that this s a serious bug, since many people is using an iPod nowadays. Do you have any idea of whether this will be fixed in a future update of Dapper?

---

### Post by theshibboleth on 2006-07-28
My understanding of journaling is that it keeps track of changes made to the drive and thereby prevents write errors. It could cause problems to disable it, but I don't think  it would cause any problems that can't be resolved by restoring the iPod with a Mac.

---

