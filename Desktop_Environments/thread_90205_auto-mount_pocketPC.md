---
title: "auto-mount pocketPC"
date: 2005-11-14
forum: Desktop Environments
---

### Post by kumpf on 2005-11-14
Hi there,

  Simple question.  Is there any good way to automatically mount my PocketPC when it is plugged into the USB port?  I don't really care about sync'ing, just about retrieving files.  I change things around to my USB ports quite often so I imagine adding a line to "fstab" probably would work ok for the PocketPC, but then try to mount other USB devices incorrectly.

1. Just as a sanity check, could someone post the mount command you would run if your device was connected to "/dev/ttyUSBx"

2. Is there any simple way to auto-mount the PocketPC on plug in, after making sure that the device is in fact a pocketPC?


thanks so much.

---

### Post by earobinson on 2005-11-14
1. that depends on the file system being used by the device

2. I searched for "auto mount usb" and i found lots of answers to this, auto mounting a usb key should be the same as your device. (cut and paste dont seem to be working so i can not cut the exact link if you are unable to find any helpfull links tell me and i will type out the whole link)

---

### Post by kumpf on 2005-11-14
I did some looking around, and here is the deal:

1. run "dccm" to start listening for pocketPC connections.
2. put the pocket pc in the cradle with power on, then run
  "sudo synce-serial-start"  to establish a connection.
3. you can now navigate the pocketPC using the "synce-p*" commands.
  this allows  you to "cp" and "ls" and "mv" etc.
4. to view existing programs on the pocketPC, type "synce-list-programs"
5. to install a new program on the pocketPC from a .cab file, run "synce-install-cab <cabfile.cab>"

Hope that helps some people.  the commands are a little wordy and simple navigation can be a bit of a pain, but you should be able to access all of your data. :)


Anyone know of a nice gui to navigate the files on a pocketPC?

---

### Post by madjo on 2005-11-14
[QUOTE=kumpf]Anyone know of a nice gui to navigate the files on a pocketPC?[/QUOTE]
I haven't tried it yet, but perhaps through synce-multisync? or synce-kde?

---

### Post by kumpf on 2005-11-14
hmm.. the PocketPC seems to connect most times, but if the connection drops it usually takes a minute or so, and a pull-out/put-in of the device in the cradle, before the connection can be made again.

All I want to do is read it like a USB drive of some sort... just to transfer files easily.  Anyone know of a way to mount it directly.  Everything I've seen about mounting a PDA doesn't seem to cover this.  There are configuration flags and device drivers and all kinds of scripts/programs to sync it with a mail program, but what about generic file transfers?  I've tried mounting /dev/ttyUSB0, since that is where it is located.  But ttyUSB0 is not a block device and so it seems as though I can't mount it directly.  any suggestions?

 :)

Thanks!

---

### Post by baron_samedi on 2006-09-08
> **kumpf said:**
> All I want to do is read it like a USB drive of some sort... just to transfer files easily.

Darn... I have exactly the same problem. Too bad nobody seems to have come up with a way to do it.

---

### Post by eudemus on 2007-04-23
I also need this, as I want to be able to use Unison to sync my PDA 2GB SD card (which has literally everything I work on on it) to my desktop as a regular backup.
Unison needs a mounted directory path.
Anyone any further on this?

---

### Post by Steve H on 2007-04-25
Have a look at [_this thread_]("http://ubuntuforums.org/showthread.php?t=30936&highlight=pocketpc+evolution"). It has a section about synce-trayicon, that seems to work as you want it to.

---

### Post by eudemus on 2007-07-02
This didn't really do the trick for me.
But using synce and synceFS plus Unison I managed to mount the device as a filesystem and be able to read and write to it in tne normal way, including using Unison to folder sync with a replica on my desktop machine.

The tricky bit I'm struggling with somewhat is how to get it to mount *automatically* when I plug it in, and umount *automatically* when disconnected.

I'm aware this will be done using udev scripts, but I have no idea how to use them. Can anyone help, who konws a little about udev?

Thanks
Eudemus

---

### Post by eudemus on 2007-07-02
[http://ubuntuforums.org/showthread.php?t=444387](http://ubuntuforums.org/showthread.php?t=444387)
Here's the HOWTO I posted about mounting a PocketPC device as a drive and syncing data.

---

