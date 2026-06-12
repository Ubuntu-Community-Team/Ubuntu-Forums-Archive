---
title: "Script for users to mount and umount floppy in Xubuntu"
date: 2007-03-06
forum: Desktop Environments
---

### Post by fabioleitao on 2007-03-06
I think this might be a commom problem for most users.

I know I am not a newbie to Linux but everyone in my family are and they've asked me how to open a floopy disk in the gui environment.

I know I can open if with **sudo mount /dev/fd0 /media/floopy** and then navigate with Thunar (remember I was in Xubuntu) but I would not want to give admin privileges to regular users.

I've decided to write a bash script to automate the process and later set an icon shortcut with it. It was intended to use in Xubuntu, but if you adapt it to execut your favorite GUI (Konqueror in Kubuntu or Nautilus in Ubuntu) it should work just fine.

First I've setup the mounting places to make sure it would work propperly, so if you **sudo vi /etc/fstab** (or with your favorite editor) you must have a line that says something similar to: **```
/dev/fd0 /media/floppy0 vfat,msdos,ext2,hfsplus rw,noauto,users,dev,sync,dirsync 0 0
```** and comment with **#** any other floppy reference.

That would mean that the system would not assume there was a floppy, but when attempting to mount, it would try to use those file systems (vfat,msdos,ext2,hfsplus), it would me accessable for users as with read and write permissions and it would disable the write back (wich is slower, but it forces the floppy to write imediatelly if any byte changes).

 Than I've followed to the script it self with **sudo vi /usr/local/bin/floppy.sh** and after a few debuging cycles it ended up like this:
```
#!/bin/bash
FLCACHE=/tmp/floppym
FLMOUNT=/media/floppy
if ! [ -w $FLCACHE ]; then
        echo 0 > $FLCACHE
fi
FLSTATE=`cat $FLCACHE`
case $FLSTATE in
        1) 
        umount $FLMOUNT
        echo 0 > $FLCACHE
        rm $FLCACHE
        killall Thunar
        exit 33
        ;;
        0) 
        pmount $FLMOUNT
        ERR=`echo $?`
        if [ $ERR == "0" ] ; then
                echo 1 > $FLCACHE
                Thunar $FLMOUNT &
                exit 44
        else 
                echo 0 > $FLCACHE
                exit 45
        fi
        ;;
        *) 
        pmount $FLMOUNT
        ERR=`echo $?`
        if [ $ERR == "0" ] ; then
                echo 1 > $FLCACHE
                Thunar $FLMOUNT &
                exit 55
        else 
                echo 0 > $FLCACHE
                exit 56
        fi
        ;;
esac
exit 0
```

Due to the limitations of the floppy drives, which do not have means to detect if a disk is inserted or not (unlike a CDROM or USB drive) there are a few steps to check and note the current state.

I had to assume you have only one floppy disk and it is the /dev/fd0, but it should be easy to adjust if necessary to your reallity.

I had to assume there was no disk mounted prior to the first script call, but other than that, basically, it mounts the floppy to /media/floppy (the usual place) is there is a floppy to mount and does nothing if there is nothing to do and umount if it is mounted there for you to be able to remove.

The sync and dirsync should protect your data if you eject before you umount, but it's better if you remember to umount while the disk is inserted.

Change the script to be executable with **sudo chmod 755 /usr/local/bin/floppy.sh**

Now, any user can call the **floppy.sh** command from the shell Terminal.

To blend in with the GUI (remember I was at Xubuntu) I've set an icon from /usr/share/icons/human/scalable/devices/gnome-dev-floppy.svg to call the floppy.sh command and placed at the menu and quick launch.

I will not detail here how to blend it here but I am open to comments and critics.

---

