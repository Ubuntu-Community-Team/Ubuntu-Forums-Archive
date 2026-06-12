---
title: "Wii Backup Fusion help... fails to read my disk to make backups :("
date: 2012-05-06
forum: Gaming &amp; Leisure
---

### Post by ijason on 2012-05-06
greetings.

first, i am aware this may be a sensitive subject, i don't know how the forum stands on software to make backup copies of personally owned games for private use. please do not contribute any comments about software pirating in any way, i am not interested in any information about that. i am trying to use Wii Backup Fusion to make legitimate copies of software i have purchased. 

i am so far unsuccessful at trying to use Wii Backup Fusion on both my laptop and desktop. both running ubuntu. the default location for the dvd drive in the program's configuration is "/cdrom". when i load any disk into my computer nothing ever gets mounted to that location... so obviously when the program looks there for a disk, it sees nothing. 

my computer actually uses "/dev/sr0" for the location of my dvd drive, i have tried putting THAT path into the field for the program, but it still errors out. when i put a standard movie into my computer, i can mount the disk via "sudo mount /dev/sr0 /media/temp" and it will happily mount the disk to the temp folder. when i try this with a wii game it doesn't work. on my laptop (which is older, and may not be able to read dual layer disks) i get the error message "no medium found on sr0". when i try to mount the wii disk on the desktop (which is newer and can read dual layer) i get the error message "unknown device"

i would ASSUME that "unknown device" is a better error message, and that it means the computer is actually able to see that there is a disk, but can't do anything with it. presumably this is where Wii Backup Fusion comes into play, but i'll be darned if i can get WBF to aknowledge there is a disk in my computer. 

any advice would be greatly appreciated :)

---

