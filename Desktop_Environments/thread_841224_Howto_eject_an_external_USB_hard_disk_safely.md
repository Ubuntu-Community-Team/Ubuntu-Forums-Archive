---
title: "Howto eject an external USB hard disk safely"
date: 2008-06-26
forum: Desktop Environments
---

### Post by jis on 2008-06-26
If I eject an external USB hard disk partition in Thunar / Xubuntu 8.04 I get error box: 'Failed to eject "320G Volume". An unknown error occured.' (I have only one partition in the disk.) The partition is umounted anyway. But I am not satisfied with that, if I want to detach the drive. I want (1) the drive's internal cache to be committed  and (2) the disk also stopped. Maybe it would be good to (3) detach the usb disk from linux system even so that its item disappears in from Thunar – like what happens with regular USB pen flash drives when ejected in Thunar – so that you don't accidentally use the drive before unplugging the USB cable. You can do that. 

Suppose the partitions in the disk are umounted already e.g. by command "umount /media/mountpoint". Then you could do this in root shell (to which you can get by command "sudo -s" end exit from by "exit"):

– run "fdisk -l" to figure out the name of the drive; I use sdb in this example.
– 1) "sdparm --command=sync /dev/sdb" to sync the cache
– 2) "sdparm --command=stop /dev/sdb" to stop the disk
– 3) "echo 1 >/sys/block/sdb/device/delete" to make drivers to forget the disk

Exit the root shell by "exit" and finally you can unplug the USB cord. I hope there'll be some practical implementation for this in Xubuntu.

---

### Post by jis on 2008-06-27
I tried to make a script to automate detaching a removable drive:
> 
#!/bin/bash
#
# Give the device name, e.g. sdb, as the only argument $1.
# You may use 'sudo fdisk -l' to get the name of the disk.
# This script unmounts partitions of the disk, syncs disk's
# internal cache, stops disk and removes the volume icon(s)
# from file manager and desktop.

# Don't accept empty $1
set -o nounset
# Exit on error
set -o errexit

umount_partitions() { local dev="$1"; mount | cut -d' ' -f1 | while read par; do case "$par" in "$dev"*) umount "$par" ;; esac; done; }
umount_partitions /dev/$1

# Detaches the device $1 from linux
echo Trying to sync and stop disc /dev/$1\; need to do it as superuser.
sudo sdparm --command=sync /dev/$1
sudo sdparm --command=stop /dev/$1
sudo sh -c 'echo 1 >/sys/block/$1/device/delete' goodbye $1


---

### Post by jis on 2008-06-28
Please note the fixed script in the previous message.

Is there a good way to make the script work without need to give a password?

---

### Post by ansicplusplus on 2008-08-08
Hi,
as far as I know there is no way to make your script work without password. Direct calls to hardware (as sdparm) require root privileges because not every user (linux is a multiuser(!) os) should play with your hardware unrestricted. Of course there is the setuid/setgid mechanism which allows programs to run with the permissions of the owner rather than the permissions of the user running them. However its usage for scripts is really dangerous. Everyone who gets a chance to modify your script can add any command which will then be run with root privileges (f.e. rm -rf / ). Therefore several distributions ignore setuid/setgid when used for scripts.
I have not checked on ubuntu, but as they disabled several dangerous stuff I would be shocked if they allowed this one.
Yours, ansicplusplus

---

### Post by jis on 2008-08-17
Suppose user has physical access to computer so he can unplug an USB device. Why not give him privilege to eject the device from file system before that?

---

