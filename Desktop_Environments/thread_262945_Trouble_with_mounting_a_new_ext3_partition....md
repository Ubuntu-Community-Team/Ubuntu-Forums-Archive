---
title: "Trouble with mounting a new ext3 partition..."
date: 2006-09-22
forum: Desktop Environments
---

### Post by mod187 on 2006-09-22
I am having a problem with mounting an ext3 partition. Here are the details:

hda: CDROM

hdb 60G: hdb1 25G: ntfs XP install
         hdb2 30G: ext3 ubuntu install
         hdb5  5G: ubuntu SWAP

hdc 250G: hdc1: ext3

hdd 250G: hdd1: ntfs

What I want to mount is hdc1 as full read/write, and MAYBE (one day) hdd1 as full read/write.

I followed the Ubuntu Dapper Wiki tutorial ([http://ubuntuguide.org/wiki/dapper](http://ubuntuguide.org/wiki/dapper))
and several others, but I am at the point where either:
a)I am overlooking something VERY SIMPLE I forgot
b)There is something wrong with my system.

This is what my fstab looks like:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0 
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0 
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1        /media/VOL_0    ntfs-fuse    auto,gid=1002,umask=0002    0    0
/dev/hdd1        /media/VOL_1    ntfs-fuse    auto,gid=1002,umask=0002    0    0 
/dev/hdc1       /media/VOL_2    ext3    defaults,errors=remount-ro 0       1
# /dev/hdc1        /media/VOL_2    ext3    defaults    0      0

Hdc1 was ntfs, and I tried to mount it with read/write access, along with hdd1, but only was able to read, not write.

So, I decided to format hdc1 to ext3, and mount it that way. It mounts, and I can read it, but not write to it.

If you look at my fstab, you will see the last line is commented out. I tried this, but it didn't work either.

My login name is taylorm. I added 'taylorm' user to group 'ntfs' when I tried to mount hdc1 and hdc2 as ntfs. I then added taylorm to ext3 group- still with no success. I also added taylorm to 'root' with the same results.

Using 'sudo nautilus' I tried to change the folder owner to 'taylorm', and when I exit back to terminal, this is what I get:
> taylorm@ubuntu-AMD:~$ sudo nautilus
Password:

(nautilus:1424): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(nautilus:1424): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 

** (nautilus:1424): CRITICAL **: nautilus_file_unref: assertion `NAUTILUS_IS_FILE (file)' failed

Any help would be great.

Matt

---

### Post by bubi1980 on 2006-09-22
hi, I dont know if this help you , but a had an inaccessible hard drive and i just used this: [http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)
I got this link from here: [http://ubuntuforums.org/showthread.php?t=254413&highlight=disk+manager](http://ubuntuforums.org/showthread.php?t=254413&highlight=disk+manager)

I hope it will help you

---

### Post by mod187 on 2006-09-22
Quote taken from [http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

> Now I need to give it the proper permissions. Let's just assume, for this example, that my username is marie.
sudo chown -R marie:marie /storage
sudo chmod -R 755 /storage

OK. I typed
sudo chown -R taylorm:taylorm /media/VOL_2
Then
sudo chmod -R 755 /media/VOL_2 and got
> taylorm@ubuntu-AMD:~$ sudo chmod -r 755 /media/VOL_2
chmod: cannot access `755': No such file or directory


I then tried
$ cd /media
and
$ sudo chmod -r 755 /VOL_2
with the same errors.

---

### Post by mod187 on 2006-09-22
OK. I just found that my problem was '-R', NOT '-r'

Sometimes we all spend too much time looking at the big picture, instead of the little details.

Thanks for the reply. It works now.

M

---

### Post by bubi1980 on 2006-09-22
no problemo:)

---

