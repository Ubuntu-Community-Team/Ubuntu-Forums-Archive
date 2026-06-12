---
title: "I need more space for my Linux"
date: 2009-02-18
forum: General Help
---

### Post by andreandre on 2009-02-18
Hello everyone i am new to this forums , recently i installed ubuntu to see how it was and i ended up loving it!

now i want more space to ubuntu because when i installed it i made it use only 40 gigas while windows is using something like 80 gigas

all my musics , files , pictures and videos are at windows but i want to move them to linux and to do so i need more space for linux and less space for windows , i still need windows to use some programas which arent available for Ubuntu.

how can i do this without losing data ?

here is a img that i got from gparted if it helps
[img]http://img204.imageshack.us/img204/9566/screenshotbw2.png[/img]

I have windows vista premium and ubuntu 8.10

Thanks in advance and sorry for my bad english i am brazilian =#

---

### Post by binbash on 2009-02-18
I suggest doing this with GPARTED LIVE CD.

You will resize your xp partition then ubuntu partition

---

### Post by andreandre on 2009-02-18
Where can i get it? and is it possible to lose data with this process?

---

### Post by Elfy on 2009-02-18
You need to do it from a livecd - either the buntu one or a standalone partition editor.

You need the partition to be unmounted - so the key symbol is not there - if you use the livecd - it weill use your sawap so you will need toright clcik on sd6 and trun swap off

To get the space available for use in resizing the / drive you will need to shrink the ntfs drives - then resize extended partition before you will be able ti add it to your / partition.

It is always possible to lose data - so make sure that you have suitable and proved backups

---

### Post by philinux on 2009-02-18
It will take and age to do. Like hours and there is risk of losing data. Why move the files when you can easily access them.

---

### Post by andreandre on 2009-02-18
because i dont want windows anymore in my laptop  , if wasnt for those programs i would delete it forever!

---

### Post by crokett on 2009-02-18
I've used the gparted live CD several times to resize partitions with no problems but if this is data you want to keep I'd find a way to back it up before you do the resize, just in case.

---

### Post by Mauler5858 on 2009-02-18
I see that you have an acer.  If so, one of those partitions is the acer recover partition you can take and burn those to dvd(just in case), and use gparted to blow that recovery partition away.  then you can format the space using gparted to ext3 and set its mount point like somewhere in your home directory.  that way you dont have to resize a working directory.

hope that helps

---

### Post by WaffleCode on 2009-02-18
Download a Live CD, such as Ubuntu or Knoppix. Then use a partitioning tool to change around your partitions. There is always a chance of losing data, however, so make sure to backup.

---

### Post by guywithcable on 2009-02-18
By the way, the way you have it set up is using an extended partition to encapsulate your two Linux partitions. You will have to resize your extended partition before you can resize the partition inside of it.

I recommend getting an external drive or using a shared folder on another computer to back up everything first. If you need help backing up, I've written a tutorial on how to back up and restore an entire Linux disk. I could post it if you want.

---

### Post by guywithcable on 2009-02-18
Here's that tutorial. You can copy to a backup disk, then configure your first disk how you like, then copy back and do part two and three.

How to copy your Linux installation to a different hard drive or partition and keep it working, easily. (Assuming your distro uses Grub)

Get Ready:
Get yourself a live CD and boot into it. I prefer [Ubuntu]("http://www.ubuntu.com") for things like this. It has Gparted. :)

Part One, The Copying

1. Mount both your source and destination partition.

2. Run this command from a terminal: 
```
sudo cp -afv /path/to/source/* /path/to/destination
```(Don't forget the asterisk after the source path.)

3. After the command finishes copying, shut down, remove the source drive, and boot the live CD again. (This step isn't necessary, but it makes installing Grub easier.)

Part Two, Proper Configuration

1. Mount your destination drive (or partition).

2. Run the command (using Alt+F2 or a terminal, but the terminal will be useless until you close gedit)
```
gksu gedit
```(or you can use nano if you're cool like that (or vi if you're masochistic like that)).

3. Open the file "/etc/fstab". Change the UUID or device entry with the mount point "/" to your new drive. You can find your new drive's (or partition's) UUID with this command 
```
ls -l /dev/disk/by-uuid/
```Save.

4. Open the file "/boot/grub/menu.lst". Change the UUID of the appropriate entries at the bottom of the file to the new one. Save and exit.

Part Three, Install Grub

1. Run 
```
sudo grub
```2. At the Grub prompt, run 
```
find /boot/grub/menu.lst
```This will tell you what your new drive and partition's number is. (Something like hd(0,0))

3. Type
```
root hd(0,0)
```but replace hd(0,0) with your partition's number from above.

4. Type 
```
setup hd(0)
```but replace hd(0) with your drives number from above. (Just omit the comma and the number after it.

5. Run
```
quit
```to get out of Grub.

That's it! You should now have a working copy of your source drive! You can use this to move to a different drive, partition, filesystem, etc.

---

### Post by andreandre on 2009-02-18
Thanks for the tutorial

---

### Post by Slim Odds on 2009-02-18
> **forestpixie said:**
> It is always possible to lose data - so make sure that you have suitable and proved backups

[SIZE=5]It is always possible to lose data - so make sure that you have suitable and proved backups[/SIZE]

---

