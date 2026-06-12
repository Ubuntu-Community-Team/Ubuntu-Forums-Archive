---
title: "Deleted files still taking up memory on usb flash stick 2gb"
date: 2009-04-13
forum: General Help
---

### Post by Toshikazu on 2009-04-13
Hi

I deleted files on my usb flash disk on ubuntu/gnome. I opened to flash disk on windows and the files are gone, but they are still taking up memory. I my flash disk is unusable. All of the hidden + non hidden files together total only 10mb, but the drive says its 90% full. How do i fix it?

thank you

---

### Post by SteveDee on 2009-04-13
> **Toshikazu said:**
> Hi

I deleted files on my usb flash disk on ubuntu/gnome. I opened to flash disk on windows and the files are gone, but they are still taking up memory. I my flash disk is unusable. All of the hidden + non hidden files together total only 10mb, but the drive says its 90% full. How do i fix it?

thank you

If you simply delete USB stick files in Ubuntu, the files go into the trash can on the USB stick. But if you hold the shift key down and hit delete they are permanently deleted.

---

### Post by iris-n on 2009-04-13
When you delete files in a removable media in ubuntu, they go to a local trash can, normally .Trash-$UID.

This folder is viewable under windows (and under ubuntu if you set show hidden files), and you can just delete it to regain your disk space. Don't worry, it will be recreated automatically when you need it.

But, that's not the best way. Ubuntu usually asks if you want to empty the trash can when you unmount the media. If you moved a lot of files and unmounted it just after, it doesn't. You can also just go to the trash can and empty manually. If your media is mounted, its trash will be emptied too.

---

### Post by Toshikazu on 2009-04-13
There are no files in the .trash folder. But I deleted the whole folder using the shift thing you said and the disk is still nearly full. I think i deleted them already from trash, but the problem is still there.


I have literally deleted all the files including the hidden trash files but they are still there. Ive done this both on ubuntu and on windows. :(

---

### Post by iris-n on 2009-04-13
There is something strange going on. Can you run this command in a terminal and paste the output?

```
ls -Ra /media
```

This will show every file that are in your usb stick so, don't do it if you have anything confidential.

---

### Post by Toshikazu on 2009-04-14
I have permenantly deleted all files on it, including the ones that where in the trash.

```

% ls -Ra

.:
.  ..

```

But there is still 1.6GB used on it :O

I have no idea now

---

### Post by askreet on 2009-04-14
Where are you getting a report of 1.6G used?

Output of:

```
df -h
```

Please :)

---

### Post by Toshikazu on 2009-04-14
```

/dev/sdb1             1.9G  1.7G  294M  85% /media/disk

```

---

### Post by Penguin Guy on 2009-04-14
Are you new to Ubuntu?

Edit:
> **Toshikazu said:**
> ```

/dev/sdb1             1.9G  1.7G  294M  85% /media/disk

```
It does appear to be using up 85% of the space; now try:
```
cd /dev/sdb1
file *
cd .Trash-1000
file *
```
And post back output.

---

### Post by Garrovick on 2009-04-14
I'm having the same exact problem.  Puting Ubuntu created files on my 2gb flash drive. The files just stay there, not shown, but still reported as being on the stick and taking up space.

Since I was just using it to transfer files from my Ubuntu desktop to my XP netbook.  My solution was simply to format it using Windows each time I transfered files.

To me, delete means delete, not hide in some hidden folder.

I'm sure there is a simple solution, but right now, this problem is on my "This doesn't work right" list.

---

### Post by timcredible on 2009-04-14
plug your usb drive in, then Places->Computer, then File->Empty Trash, then right-click on your flash drive icon on your desktop and Unmount the drive.  Don't forget, things like deleting the .Trash folder doesn't actually get done unless you unmount the drive before unpluggin it.  see if that clears out the space on the flash drive.

---

### Post by Toshikazu on 2009-04-14
I have perminently deleted everything on there so when i do file * 

*: ERROR: cannot open `*' (No such file or directory)

And i have deleted the trash folder too.

---

### Post by iris-n on 2009-04-14
I've never seen something like it. If you please, give me some more info so that I can reproduce this bug.

You had a empty flash drive, copied some files from windows to it, moved them to ubuntu, and then deleted them?

They occupied most of the flash drive? It is formated as ntfs or vfat? It was already formated on windows or you formated it through ubuntu?

Meanwhile, if you just want your problem solved, you can do as Garrovick said, format the pen drive again. I'd suggest formatting it through gparted, as he said that formatting it in windows didn't solve the issue.

gparted is not installed by default on ubuntu. So, ```
sudo apt-get install gparted
```

and if it is ntfs, you'll need ntfsprogs: ```
sudo apt-get install ntfsprogs
```

Best of luck,

Iris

---

### Post by abloss01 on 2009-06-07
I tested the following scenarios on a FAT32 flash drive

Common steps:
    1. Copy some files in WinXP to the flash drive
    2. Plug the flash drive to Ubuntu

Case A:
    3A. Delete the files in (1) from the flash drive while still in Ubuntu using Nautilus by selecting the files and pressing the 'Delete' key
    4A. Manually unmount the flash drive from Ubuntu and answer yes when asked to throw away Trash content
    5A. Once the drive is unmounted, unplug it
    ==> the space is properly reclaimed in this instance and the flash drive is ready for the next use

Case B:
    3B. Delete the files in (1) from the flash drive while still in Ubuntu using Nautilus by selecting the files and pressing the 'Delete' key
    4B. Check the trash, the files deleted in 3B are there.  Empty the trash.
    5B. Unplug the drive
    ==> the space is properly reclaimed in this instance and the flash drive is ready for the next use

Case C (a variation of B):
    3C. Delete the files in (1) from the flash drive while still in Ubuntu using Nautilus by selecting the files and pressing the 'Delete' key
    4C. Without unmounting the drive, unplug it
    5C. DO NOT touch any of the hidden Trash files/directories, continue to use the flash drive with the remaining space
    6C. Plug the flash drive to Ubuntu again
    7C. Check the trash, the files deleted in 3C are still there.  Empty the trash.
    8C. Unplug the drive
    ==> the space is properly reclaimed in this instance and the flash drive is ready for the next use

Case D:
    3D. Delete the files in (1) from the flash drive while still in Ubuntu using Nautilus by selecting the files and pressing the 'Shift' + 'Delete' keys
    4D. Without unmounting the drive, unplug it
    ==> the space is reclaimed, however, for some reason, the flash drive is put into read-only mode and is pretty much useless.  The only way I can fix it is by reformatting it !!!

It looks to me that Case A presents the cleanest option and Case B is most intuitive and easy to do.  And unfortunately, it seems to me that there is no easy 'unplug and have the space reclaimed' like in WinXP.  Happy to hear if anyone knows of such a solution.

---

### Post by reignaldo on 2009-07-10
quando eu tento deletar os itens da lixeira permanente, ela começa a preparar para deletar os itens da lixeira e vai crecendo infinitos arquivos ....

---

### Post by Marlonsm on 2009-07-10
Have you tried backing up the files on the pendrive and formatting it on GParted? (If you don't have GParted, you can get it on Add/Remove)

---

### Post by Gizenshya on 2009-07-10
weird, I say it is good that you posted this, to make people aware of it... but I'd have formatted as soon as I noticed a discrepancy.

fire up gparted, or in win right-click and format it to the FS of your choice and you're all set

---

### Post by tdietz87 on 2009-07-10
i just boot up windows, right click usb drive, click format (quick format) deletes everything and works for me evertime  whenever i delete anything from external devices in ubuntu it says its still full

---

### Post by JOHNNYG713 on 2009-07-10
If nothing else works.......................................................Get a big hammer !:guitar::lolflag:

---

