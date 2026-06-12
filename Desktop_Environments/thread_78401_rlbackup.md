---
title: "rlbackup"
date: 2005-10-18
forum: Desktop Environments
---

### Post by beercz on 2005-10-18
Hi Guys

Trying to install rlbackup ([http://www.math.ualberta.ca/imaging/rlbackup/]("http://www.math.ualberta.ca/imaging/rlbackup/")) on one of my ubuntu boxes.

I am having real trouble installing the server component in ubuntu.  I follow the instructions ([http://www.math.ualberta.ca/imaging/rlbackup/INSTALL]("http://www.math.ualberta.ca/imaging/rlbackup/INSTALL")) given, and I get an error when I run:

make install-server

Here's the output from the above command:

dd if=/dev/zero of=/usr/local/bin/rlbackup.ext2 bs=4k count=1024
1024+0 records in
1024+0 records out
4194304 bytes transferred in 0.028486 seconds (147240643 bytes/sec)
umount /backup/*/bin
umount: /backup/*/bin: not found
make: [install-server] Error 1 (ignored)
mke2fs -q -F -m0 /usr/local/bin/rlbackup.ext2
tune2fs -c 0 -i 0 /usr/local/bin/rlbackup.ext2
tune2fs 1.38 (30-Jun-2005)
Setting maximal mount count to -1
Setting interval between checks to 0 seconds
mkdir -m 0700 -p /backup /backup/bin
chown root.root /backup /backup/bin
chmod 0700 /backup
losetup -d /dev/loop2
loop: can't delete device /dev/loop2: No such file or directory
make: [install-server] Error 1 (ignored)
losetup /dev/loop2 /usr/local/bin/rlbackup.ext2
/dev/loop2: No such file or directory
make: [install-server] Error 1 (ignored)
mount -t ext2 -o rw /dev/loop2 /backup/bin
mount: special device /dev/loop2 does not exist
make: *** [install-server] Error 32

I have two ubuntu boxes and three debian (sarge) boxes available.  The server install works on all three debian boxes, but does not work on either ubuntu box - the output on either box is the same.

Anyone know what's missing, or going on here?  Has anyone got this to work?

Thanks in advance.

Ian

---

