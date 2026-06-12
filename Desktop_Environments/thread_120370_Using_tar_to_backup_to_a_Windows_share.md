---
title: "Using tar to backup to a Windows share"
date: 2006-01-21
forum: Desktop Environments
---

### Post by koolguynet on 2006-01-21
I have a Fedora box that I want to fully backup before I install Ubuntu.  I have been able to back up my Ubuntu laptop to a USB HDD using the following command:

/home/csmith# tar cvpzf /media/usbdisk/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/media /

That worked great!  Here is my problem...on my Fedora box I have a ton of data and don't have a USB HDD that is big enough.  I do, however, have a WinXP Pro box with enough room.  What I want to do is run the same command but copy the files directly to the windows share (which I can see by doing smb://computername in Gnome).  I can't seem to figure out how to do it since it has to be done through command line.  Thanks!

---

### Post by newuser111 on 2006-01-21
I'm assuming its an NTFS partition since it has windows XP, writing to NTFS from within linux is considered risky, but you could try "captive NTFS"

---

### Post by koolguynet on 2006-01-21
It is an NTFS partition but I would be writing to it over the network.  I can see and write to it from within Gnome.  I just don't know how to tell tar to copy to a shared drive on the network.

---

### Post by kpm on 2007-10-06
I know this is an old post but just incase any one else comes a cross it searching for solutions... Iin my search trying to figure out how to move one directory off a LAMP server and dump it on a Windows 2003 server file share, I found this article.  It reads like it will solve the problem listed here:
[http://chxo.com/be2/tar_backup_to_ntfs.html](http://chxo.com/be2/tar_backup_to_ntfs.html)

It didn't work for me because I am still trying to figure out why the server thinks the user doesn't have write permissions when the service user 'backup' does!!  Argh.

---

