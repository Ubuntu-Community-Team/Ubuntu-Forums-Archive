---
title: "SteamLibrary on ext hd"
date: 2013-10-25
forum: Gaming &amp; Leisure
---

### Post by z3r0f14m3 on 2013-10-25
I cant seem to figure out how to get this to work. Im trying to get Steam to import my library of already downloaded games that is on my ext HD. Ive found the folders and pointed at them, but I get the error saying that i need permission to execute. So I gave myself permission for the whole drive, I checked to make sure. Yet I still get the same error when trying to add the folder to my library.
Ive just started with Ubuntu so be nice :)

---

### Post by dannyboy79 on 2013-10-26
where are you steam games located, can you please issue the following command on the folder
```
ls -la /media/foldernamehere/
```
obviously /media/foldernamehere/ is an example and I want you to replace that with where your external drive is mounted and what sub-folder your games are in. we'll go from there.

---

### Post by efflandt on 2013-10-27
What file system is the partition on the external drive? If you are going to put Linux stuff on an external drive it is best to use Window Vista/7/8(?) to shrink the ntfs partition and create a Linux partition for Linux stuff (ext4, etc.). Or if flash memory stick or SD, have 1 specifically for Linux with ext2 partition. NTFS or FAT/FAT32 know nothing about *nix ownership/permissions, so permissions for all directories and/or all files depend upon mount options for that partition. That may be an issue if there are mixed non-executable files and executable scripts/binaries.

---

### Post by HikariKnight on 2013-10-30
I have all my steam games organized on an external that is permanently connected to my computer so i added it to /etc/fstab
Ofcourse it will pause the bootup if i disconnect the external though but i can run steam games on it even as its partitioned as NTFS.

If it is an external that is constantly connected then you can do like i did and make a Steam folder in /media and then add this to a new line in /etc/fstab
```
UUID=uuid_of_the_external_disk /media/Steam auto defaults 0 0
```

Synopsis:
```
UUID=uuid_of_the_external_disk = replace "uuid_of_the_external_disk" with the uuid of the external disks partition
/media/Steam = this is the location the partition will be mounted at, this folder need to exist from before!
auto = automatically detect filesystem
defaults = use default settings
0 = disable dump
0 = disable filecheck on boot
```

to get the UUID you can use
```
sudo blkid
```

An example of how it would look like(with the UUID of my Steam External)
```
UUID=D06C22236C220536 /media/Steam auto defaults 0 0
```

But keep in mind that not all games come with all the linux/windows/mac files so when you start steam on a different platform they will start replacing the currently installed version (for windows for example) with the linux version, as they are not "compatable" with eachother.
For that i have 1 Steam library on the external for games that contain the files for all platforms like the games made with the source engine, and then 1 Steam library that is platform specific.

so for me on linux i have
/media/Steam/SteamLibrary
which contains games that share the same game files across platforms
and
/media/Steam/LinuxLibrary
which contains linux games that do not share the same files as the windows version of the game

then i of course have the "WindowsLibrary" and "MacLibrary" for the windows and mac games that doesn't share files with other platforms (like Dungeon Defenders, which btw have a HORRIBLE linux port that cannot be used if you want to play with time limits on setting up defences)

hope this will help you :)

---

