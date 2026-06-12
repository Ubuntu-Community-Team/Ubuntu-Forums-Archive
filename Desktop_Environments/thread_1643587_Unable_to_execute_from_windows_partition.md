---
title: "Unable to execute from windows partition"
date: 2010-12-12
forum: Desktop Environments
---

### Post by burdebc on 2010-12-12
I am dual booting XP and Kubuntu 10.10 from separate hard drives and I can't execute .exe files from my XP drive.  I also have an internal data drive that I can execute .exe files from fine.  When I try to go into the properties for the file to mark it executable I am unable to do so.  I have ran "sudo nautilus" to mark the files executable and that doesn't work either.  I even changed /dev/sdb1 to be owned by myself instead of root, and that doesn't help.  When I used "sudo nautilus" I also got error messages in my terminal when I tried to do anything (which I copied and attached to this post).  Any help would be greatly appreciated in this matter.

---

### Post by burdebc on 2011-03-04
This issue cleared up when I upgraded my computer and reinstalled everything, but please post any solutions if you have them anyway since others may need the help.

---

### Post by Zorael on 2011-03-04
(**sudo nautilus** is *always* a bad idea. Even if it does work it will wreak havoc with permissions and ownership in your home directory, and thus break other stuff. So make a good habit of keeping to **gksudo** for graphical programs.)


NTFS doesn't speak in terms of executable or not, as Windows goes by file extension instead. If you rename a text file to .exe, Windows will consider it executable (though it will obviously crash immediately). So to be able to give executable permissions to files on NTFS partitions in linux (and other UNIX-like operating systems), when mounting it you decide what **file mask** and **directory mask** (or **umask** combined) to apply to all files and directories in it. Unless specified manually in **/etc/fstab** or when mounting it yourself, it assumes some defaults defined someplace I don't know about.

These masks are basically your normal file permissions, so a file that can be read by all, written to by all and executed by all would be **rwxrwxrwx**. Only these masks are in octal and work *backwards*, so instead of such **rwxrwxrwx** files having a mod of **777**, they have **000**. Files having **rwxr-xr-x** "should" have **755**, but in this case they have **022**. The same applies for directories, and directories that cannot be executed cannot be entered.

My NTFS mounts look like this (again, in **/etc/fstab**);
```
# <file system>				<mount point>	<type>	<options> <dump> <pass>

/dev/mapper/isw_dhgifcega_vertex7	/main           ntfs    defaults,**umask=007**,uid=1000,gid=1000 0 0
UUID=1286AD9186AD75BF 			/storage        ntfs    defaults,**umask=007**,uid=1000,gid=1000 0 0
/dev/mapper/isw_dhgifcega_vertex2	/w7             ntfs    defaults,**umask=007**,uid=1000,gid=1000 0 0
```
**umask** is, as mentioned above, file mask and directory mask combined. You can split it into **fmask** and **dmask** for more fine-grained control.

So a **umask** of **007** translates to a mod of **770**, or **rwxrwx---** for all files and directories. My user and my group can read, write to and execute all files and directories on those partitions. Other users cannot access them at all.

As another example;
```
/dev/mapper/isw_dhgifcega_vertex2	/w7             ntfs    defaults,**fmask=044**,**dmask=055**,uid=1000,gid=1000 0 0
```
With these masks, my user has full permissions, while my group and other users can only read files, and read+execute directories.

---

### Post by burdebc on 2011-04-03
I stumbled across the solution I used when I tried to get my non linux drives to mount at startup.  I edited /etc/fstab to include entries to mount the drives at startup.  Here is some material that will explain the particulars of editing /etc/fstab:

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

The second one holds the solution to this specific problem in the VFAT/NTFS section.  Since ownership and permissions are set at mounting with VFAT and NTFS drives I had to use the uid option.  This sets the owner of the drive.  I set the owner of the drives to my username instead of letting it default to root and the problem was solved.  Below is the entries I made to /etc/fstab:

UUID=C204016F040167AD    /media/C204016F040167AD    ntfs-3g    defaults,locale=en_US.UTF-8,uid=burdebc        0    0
UUID="FBAE-335E"    /media/My-Book    vfat    defaults,uid=burdebc    0    1

---

