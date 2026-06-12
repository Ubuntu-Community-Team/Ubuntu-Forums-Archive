---
title: "ntfs file copying"
date: 2006-04-25
forum: Desktop Environments
---

### Post by spartan777 on 2006-04-25
i know i need root to read ntfs files, and that writing to ntfs with linux is very dangerous.

what i can't do is copy the files (mp3's, txt's, etc.) to my desktop in ubuntu. that only requires reading the file, so why can't i simply copy and paste? how do i copy my files from the old windows partition to the shiny new ubuntu one? thanks in advance.

---

### Post by Sutekh on 2006-04-25
You dont need root to read (and copy) your files on the NTFS partition,  all you need to do is change the way it is mounted.

Do you know the device node of your NTFS partition, ie /dev/sda1?
If you use```
sudo fdisk -l
```you can determine the location

Once you know the location (I'll assume /dev/sda1 as an exmaple) you can use this command to unmount it from wherever it is currently
```
sudo umount /dev/sda1
```
and this command to mount it with the ability to read and copy and execute your files.
```
sudo mount /dev/sda1 /media/windows -t ntfs -o nls=utf8,umask=0222
```
The folder /media/windows must be created prior to this command too

You can also make this a permanent, by making a change to your /etc/fstab, to include a line like this
```
/dev/sda1   /media/windows   ntfs   nls=utf8,umask=0222   0   0
```

---

### Post by harishg on 2006-04-25
Also when you move the files make sure to change the chmod of every file you want to edit.

---

### Post by spartan777 on 2006-04-25
i began fooling around again, and realized that since each file is (in the way i'm doing this ntfs thing) requiring root privileges, i need root in whatever folder i'm pasting the file into. i'm going to try your way though. i'm not sure how to use, or what chmod is. those root scripts are so handy though.

oh, and the ntfs partition is hda1, i'm migrating the old windows xp files into the ubuntu partition for my family. windows won't even start at this point.

*edit*
i tryed your way, and it works brilliantly, so thanks. i only wish i knew what chmod is. i'll probably look it up though, seems important. thanks.

*edited edit* i looked up chmod, but it looks like i'd rather stick to gui stuff, and the command line for things i do very often or can't in the gui. thanks though.

---

### Post by harishg on 2006-04-26
you can do it another way.Right click on file and in permission change permission to execute.It does not need to be from root.

---

### Post by Ramses de Norre on 2006-04-26
If you moved all the files into one folder do this in terminal: ```
chmod -R 775 /path/to/folder
``` and you'll be able to read/write/execute them all.
If it gives an error about permissions denied you'll need to execute this first: ```
sudo chown -R username /path/to/folder
``` to make yourself owner of the files.

---

