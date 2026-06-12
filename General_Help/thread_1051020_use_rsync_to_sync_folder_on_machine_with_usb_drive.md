---
title: "use rsync to sync folder on machine with usb drive"
date: 2009-01-26
forum: General Help
---

### Post by e24ohm on 2009-01-26
Forum,
Is is possible to use rsync to since a folde/files on my desktop with my usb drive? If so how do i do this? I am very new to linux, and i want to migrate over 100% from you know what.

If anyone can give suggestions or tips on how to use rsync, or if you know of a better way on how to do this, please assist me...

thank you.
E

---

### Post by scandido on 2009-01-26
If you open a terminal, type "man rsync", and then scroll down a bit you'll see some usage examples for rsync. The simplest usage would be if you only wanted to sync in one direction. For example, if you wanted to make the contents of a folder on your thumb drive identical to the contents of a folder in your home folder, 

rsync -av --delete /home/username/SourceFolder/ /media/thumbdrive/DestinationFolder/

The other direction would be 

rsync -av --delete /media/thumbdrive/DestinationFolder/ /home/username/SourceFolder/ 

Please note that the trailing slashes on the paths are important. You could set up these scripts to run from a launcher on your panel. 

If you want to prevent newer files from being overwritten, you can use the -u flag in the command. I think running these two commands subsequently will probably accomplish the task you require

rsync -auv /home/username/SourceFolder/ /media/thumbdrive/DestinationFolder/
rsync -auv /media/thumbdrive/DestinationFolder/ /home/username/SourceFolder/ 

but, will not delete any files so if you remove a file from one folder you'll have to remove it manually from the other before the next sync if you want it to disappear.

This is just an educated guess so please test this carefully before using it on your actual files. Good luck.

---

### Post by scandido on 2009-01-26
Also, please note that rsync is not the ideal tool for this task. A more suitable program, for example, would be "unison" which is available from the Ubuntu package manager. 

[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)

Good luck.

---

