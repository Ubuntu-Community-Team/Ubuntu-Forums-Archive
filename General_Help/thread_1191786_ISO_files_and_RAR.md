---
title: "ISO files and RAR"
date: 2009-06-19
forum: General Help
---

### Post by georgedarkstar on 2009-06-19
Hi I'm new to the forum and really am trying to get up to speed on computer stuff.
I have lived in outback Australia where there is not a lot of access to or info on computer programs and stuff.
Continually trying new programs and experimenting by downloading programs from torrent sites.
The result is viruses and things happen I dont understand.
What I am now trying to get info on is ISO files and virtual disks etc.
I have programs that I have to un RAR and others that have to be mounted on virtual disk drives.
How do I do it or where can I get info on this stuff?
I need a mentor as this is getting really frustrating.
Can anybody assist please?
Thanks.
George

---

### Post by prem1er on 2009-06-19
Are you running a windows machine or linux machine?  Rar files are simply archived directories, like zip files.  If you are using a linux machine all you need to do is open terminal and move to location of the .rar file.  Then simply run this command.

```
unrar e (file.rar)
```

in order to extract the files into your current directory.

An iso file is a cd image file. In linux all you have to do in order to use an .iso file is simply mount the image. Run these commands.

```
mkdir /mnt/iso
```
```
mount -o loop -t iso9660 (file.iso) /mnt/iso
```

---

