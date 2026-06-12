---
title: "Trouble mounting possibley damaged windows partition"
date: 2009-02-23
forum: General Help
---

### Post by DaRockwilder on 2009-02-23
Im using ubuntu 8.10 wit gnome enviornment. I am dual booting wit win xp media center edition and my windows wouldnt boot up i think due to a virus and for some reason i cant use the gui in ubuntu to mount my C: drive.
it tells me i need to force mount which being new to linux i will most likely need some help doing, these are the error messages if someone could let me know whats happenin or point me in the right direction thatd be awesome.
I attached pictures of the error messages hopefully they will help somehow****

---

### Post by caljohnsmith on 2009-02-23
How about opening a terminal (Applications > Accessories > Terminal) and do:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
```
If the ntfsfix command completes successfully, then try:
```
sudo mkdir /media/Windows
sudo mount /dev/sda1 /media/Windows && nautilus /media/Windows &
```
Let me know how that goes.

---

### Post by jbrown96 on 2009-02-23
First, create a folder to mount your windows directory. I recommend mounting in your home folder, but you can change it to wherever, it's up to you. 
```
mkdir /home/$USER/windows
```
Find your Windows partition
```
sudo fdisk -l
``` The partition should be labeled as NTFS or identify by the size. Remember the name and number (i.e. /dev/sda2, /dev/sdb1, etc.)
try to force mount
```
sudo mount /dev/sda2 /home/$USER/windows -o force
``` change /dev/sda2 to what you found in the last step.

---

### Post by DaRockwilder on 2009-02-23
nice thanks guys, I have my windows folder mounted now in the filesystem/mnt

thanks a lot

---

