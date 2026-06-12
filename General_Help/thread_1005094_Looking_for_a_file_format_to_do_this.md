---
title: "Looking for a file format to do this"
date: 2008-12-07
forum: General Help
---

### Post by dkulchenko on 2008-12-07
Suppose I have a directory with files and folders. I'm looking for a file format, which can store files in such a way that I can "mount" the "image" in such a way that the contents of the directory merge with the contents of the "image", and can then be unmounted, returning the original directory to its previous state. The "mounting" also needs to be done instantaneously, like an ISO image mounting, not like a .tar.gz archive.

ISO files work fine, to mount it you either require fuse or administrator privileges, and I do not know of a way to merge the contents with the directory while mounting.

ZIP, GZIP, TAR, and so on do not work, because to merge the contents, it would take a while to unarchive. You also could not "unmount" it, removing the "mounted" files.

Basically, here are my requirements: can be run as a regular user, (preferably) does not require external programs, can be "mounted" and "unmounted", without leaving the files behind, like an archive, and can "mount" and "unmount" instantaneously.

Thanks in advance!

---

### Post by geirha on 2008-12-07
You can create an image with ext3 filesystem, and use it like you do an iso-image, with the exception that you can both read and write to it. It's fairly simple. First create a file with the size you want. Let's create a 10MB file, file.img, filled with zeroes.
```
$ dd if=/dev/zero of=file.img bs=10000000 count=1
1+0 records in
1+0 records out
10000000 bytes (10 MB) copied, 0,104802 s, 95,4 MB/s

```
The dd-command above reads 1 block (count=1) of size 10MB (bs=10000000) from the special device /dev/zero which will always return zeros when you read from it, and write it to the file file.img.

Next, make a filesystem (ext3 in this case) on it:
```
$ mkfs.ext3 file.img
mke2fs 1.40.8 (13-Mar-2008)
file.img is not a block special device.
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=1024 (log=0)
Fragment size=1024 (log=0)
[...many lines...]

```

And lastly, mount it
```
sudo mount -o loop file.img /mnt
```

To allow regular users to mount it, you need an entry in fstab for it. Say you save it as /usr/local/share/file.img, and want to mount it at /mnt, then the fstab entry should look something like
```
/usr/local/share/file.img /mnt ext3 loop,user,noauto 0 0
```

Now any user should be able to mount it with the command 
```

mount /mnt
# or
mount /usr/local/share/file.img

```

---

### Post by dkulchenko on 2008-12-07
Thanks! That really helped, and an ext3 file would work, but only one problem: I'm trying to find a way to do this portably, on any computer, so without at any point requiring administrator privileges (except for at creation time of the file). I'm not sure if this is possible, however. Is it?

---

