---
title: "Ubuntu screwed me over - how to force it to access NTFS drive?"
date: 2008-12-28
forum: General Help
---

### Post by SupremeMoFo on 2008-12-28
Hi all! I tried a Ubuntu liveCD thinking oh, you know, can't hurt, it's just a liveCD, it won't touch anything!

WRONG. Windows won't boot any more. Hangs at black XP loading screen, force reboot, try for safe mode - hangs at loading a particular .dll file, reboot, try "boot with last known safe configuration", it takes an eternity to reach the "Welcome" screen then blue screens, complaining about some rogue process and that it's performed a memory dump. Thank you so much liveCD.

Whatever. I'll wipe it and put a Vista/Ubuntu dualboot on it now BUT I want the remainder of the files I don't have backed up off it.

Ubuntu (live) won't read the harddrive, saying logfile indicates unclean shutdown. It then says something about if using Windows, disconnect the external drives... well Windows won't boot and it's not an external drive. 

It then says I can use the force option by putting this in the command line: 
"mount -t ntfs-3g /dev/sda2 /media/disk -o force"
So I tried that but the console says "mount: only root can do that".

Now what? Thanks for any help...

---

### Post by ju2wheels on 2008-12-28
I think the following is what you are looking for:

```

sudo mount.ntfs-3g -o force /dev/sda2 /media/cdrom0

```

You should replace /dev/sda2 with whatever the partition number is for your Windows partition. I used /media/cdrom0 there as the mount point is always there and theres no need to create an additional folder but you could put it anywhere you would like.

Run the following to list all your partitions:

```

sudo fdisk -l

```

---

### Post by SupremeMoFo on 2008-12-28
Found the answer [http://ubuntuforums.org/showthread.php?t=1022330&highlight=unclean+shutdown](http://ubuntuforums.org/showthread.php?t=1022330&highlight=unclean+shutdown)
GG me for not searching first, although initially I didn't know what to search for.

*edit* thank you anyway!

---

### Post by psycho5 on 2008-12-28
just put sudo infront of that line "mount -t ntfs-3g /dev/sda2 /media/disk -o force"

when you open terminal using the live cd it says how to switch to root, or when you hit alt+ctrl+f1 


on a seperate note, the live cd has nothing to do with your windows crashing, the blue screen means that something wrong with your RAM.

---

### Post by hyper_ch on 2008-12-28
the live cd won't touch your harddisk - unless you tell it to... so I'd first ask what did you in the live session?

---

### Post by 3rdalbum on 2008-12-28
Put "sudo" before that command. You might need to create the directory "/media/disk" first by typing this command:

```

sudo mkdir /media/disk
sudo chmod a+rw /media/disk

```

I know it doesn't seem like coincidence to you, but there really is no way that Ubuntu would touch your hard disk's existing files just by running the live CD. By default, Ubuntu doesn't even know what a .dll file is, so it wouldn't do anything to them.

---

