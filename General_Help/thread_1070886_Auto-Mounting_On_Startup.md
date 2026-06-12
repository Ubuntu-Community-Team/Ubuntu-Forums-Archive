---
title: "Auto-Mounting On Startup"
date: 2009-02-15
forum: General Help
---

### Post by jibjibman on 2009-02-15
Hey everyone, I have two hard drives, I was wondering how to get them to auto mount on start-up, because as of now, I have to go into places each time and double click each one for it to mount. These hard drives are in my computer, my two external ones mount every time without me doing it. Any help would be great! Thanks

Mike ;)

---

### Post by Elfy on 2009-02-15
Add them to fstab - in essence make 2 folders and then add the partitions to the fstab file

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

If they are ntfs - you can install ntfs-config which will put a tool in system tools which can be used to do that simply.

```
sudo apt-get install ntfs-config
```

---

### Post by ajgreeny on 2009-02-15
Just as a quick reference, here are some lines to add to fstab to automount partitions.  Change the partition info, obviously to your own and make directories where needed:-

Automount linux partition.  Add line to /etc/fstab:-
/dev/hdb1       /media/linux   ext3    defaults  0  1

Automount fat32 windows.  Add line to /etc/fstab:-
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0

Automount ntfs windows.  Add line to /etc/fstab:-
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

To mount manually use the following commands, again changing the partition info to your own:-

Manual mount linux:-
sudo mount /dev/hdb1       /media/linux/ -t ext3

Manual mount fat32 windows:-
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000

Manual mount ntfs windows:-
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

Mount an iso file:-
sudo  mount -o loop -t iso9660 path/to/file.iso /mount/path

---

### Post by jibjibman on 2009-02-15
How do I allow myself to create new folders? Since I'm not root it isn't letting me, and I don't know how to make new folders through terminal. Any help?

---

### Post by AlexBellisBrown on 2009-02-15
The above peoples methods are very complicated and not efficient (no offence guys..) Just install Mountmanager from the Add/remove programs, configure to mount on start up, and away you go.

---

### Post by jibjibman on 2009-02-15
Won't let me set up my two drives to automount. Weird..

---

### Post by punx45 on 2009-02-15
> **jibjibman said:**
> How do I allow myself to create new folders? Since I'm not root it isn't letting me, and I don't know how to make new folders through terminal. Any help?

its easy in terminal

if you need root powers to create it:
```
sudo mkdir <folder name>
```
 
if you dont need root, jsut leave out sudo.

---

### Post by dcstar on 2009-02-16
> **jibjibman said:**
> Hey everyone, I have two hard drives, I was wondering how to get them to auto mount on start-up, because as of now, I have to go into places each time and double click each one for it to mount. These hard drives are in my computer, my two external ones mount every time without me doing it. Any help would be great! Thanks

Mike ;)

Install the pysdm package, then System-Administration-Storage Device Manager

---

### Post by ajgreeny on 2009-02-16
> **AlexBellisBrown said:**
> The above peoples methods are very complicated and not efficient (no offence guys..) Just install Mountmanager from the Add/remove programs, configure to mount on start up, and away you go.
Mountmanager is not available for 8.04, as far as I can see.  Perhaps it's an intrepid application that has only recently appeared.  Personally, I use the Disk-Mounter applet in my panel, rather than mount partitions I seldom need at boot time, but that's just a personal preference.  I would also say that it can be very useful to have more knowledge of fstab workings, just in case things go wrong, which they occasionally do.

---

