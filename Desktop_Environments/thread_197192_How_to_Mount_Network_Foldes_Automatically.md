---
title: "How to Mount Network Foldes Automatically"
date: 2006-06-15
forum: Desktop Environments
---

### Post by utab on 2006-06-15
Dear all,

I have been using a network share pool through the below script.

export USER=username%password
smbmount //filesrv/homes /home/utab/documents/MECH_HOME -o uid=utab,gid=utab
smbmount //filesrv/pool /home/utab/documents/MECH_POOL -o uid=utab,gid=utab
export USER=username%password

The problem is that every time I reboot, I have to run this script to open the shared folders. The thing I would like to do is to automate this so that on every opening I would like it to be mounted automatically.

Ideas are appreciated.

Regards,

---

### Post by slithy on 2006-06-15
You should be able to set the mount up in your /etc/fstab file.  Not sure how to do it with samba, but I know it can be done.

---

### Post by echo $USER on 2006-06-15
you need to put the folders you want to mount in the fstab file, like this...

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read](http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read)

---

### Post by T313C0mun1s7 on 2006-06-15
I mount several shares right into my home folder from a fileserver. Here is a copy of the fstab file I am using. I have not yet figgured out how to make the mount totally automatic. Every time I boot I still have to run "sudo mount -a" then every thing works fine.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>        <type>    <options>                                <dump>    <pass>
proc        /proc            proc    defaults                                0    0
/dev/sda1    /            ext3    defaults,errors=remount-ro                        0    1
/dev/hda1    /boot            ext2    defaults                                0    2
/dev/hda2    /home            ext3    defaults                                0    2
/dev/sda5    none            swap    sw                                    0    0
/dev/hdc    /media/cdrom0        iso9660    ro,user,noauto                                0    0
#/dev/hdc    /media/cdrom0        auto    ro,user,noauto                                0    0
/dev/fd0    /media/floppy0        auto    rw,user,noauto                                0    0
//server/John    /home/john/MyDocuments    cifs    auto,credentials=/home/john/.cred,users,file_mode=0777,dir_mode=0777,uid=john,gid-john,rw,exec    0    0
//server/Public    /home/john/public    cifs    auto,credentials=/home/john/.cred,users,file_mode=0777,dir_mode=0777,uid=john,gid-john,rw,exec    0    0
//server/Tools    /home/john/tools    cifs    auto,credentials=/home/john/.cred,users,file_mode=0777,dir_mode=0777,ruid=john,gid-john,w,exec    0    0
//server/Appz    /home/john/appz        cifs    auto,credentials=/home/john/.cred,users,file_mode=0777,dir_mode=0777,uid=john,gid-john,w,exec    0    0
//server/Sites    /home/john/sites    cifs    auto,credentials=/home/john/.cred,users,file_mode=0777,dir_mode=0777,uid=john,gid-john,rw,exec    0    0
//server/Images    /home/john/images    cifs    auto,credentials=/home/john/.cred,users,file_mode=0777,dir_mode=0777,uid=john,gid-john,rw,exec    0    0
//server/Misc\040Staging    /home/john/MiscStaging    cifs    auto,credentials=/home/john/.cred,users,file_mode=0777,dir_mode=0777,uid=john,gid-john,rw,exec    0    0
//server/MP3    /home/john/MP3    cifs    auto,credentials=/home/john/.cred,users,file_mode=0777,dir_mode=0777,uid=john,gid-john,rw,exec    0    0
//server/MP3\040Staging    /home/john/MP3Staging        cifs    auto,credentials=/home/john/.cred,users,file_mode=0777,dir_mode=0777,uid=john,gid-john,rw,exec    0    0
//server/Software\040Staging    /home/john/SoftwareStaging    cifs    auto,credentials=/home/john/.cred,users,file_mode=0777,dir_mode=0777,uid=john,gid-john,rw,exec    0    0

``` 
Some notes:
The filetype should be cifs NOT smbs, smbs is depreciated and does cause some problems that using cifs resolves.
Put your user and pass in a credentials file, it is safer.
If your folders have a space in the name replace the space with "\040"

---

