---
title: "Questions About Accessing hda1"
date: 2006-09-08
forum: Desktop Environments
---

### Post by ryan.stults on 2006-09-08
I am running a dual boot with Ubuntu and XP.  I can get my Ubuntu files on XP because of samba, however, I am unable to get into my hda1 drive from Ubuntu.  I checked and I have all permissions set.  I don't know what else to do.  

P.S. The error message that I get says "You do not have the permissions necessary to view the contents of "hda1"."


P.P.S. hda1 is the XP partition (just in case someone missed that).

Thanks for any help

](*,) 
Without a clue for what to do? Turn to the forums for Ubuntu

---

### Post by ajgreeny on 2006-09-08
Have you mounted the windows partition?  If not you will need to either by editing your /etc/fstab file or doing it manually in the terminal.

Automount fat32 windows:-
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0

Manual mount fat32 windows:-
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000

Automount ntfs windows:-
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

Manual mount ntfs windows:-
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

In the above the automount entries are for the fstab edits and the manual entries for mounts using the terminal.

---

### Post by aysiu on 2006-09-08
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) gives you the steps to do what ajgreeny proposes.

---

