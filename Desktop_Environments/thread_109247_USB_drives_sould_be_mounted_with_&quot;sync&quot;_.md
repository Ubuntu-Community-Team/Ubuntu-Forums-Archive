---
title: "USB drives sould be mounted with &quot;sync&quot; option"
date: 2005-12-28
forum: Desktop Environments
---

### Post by Bou on 2005-12-28
Being quite a newbie in Linux, I discovered this mounting option only yesterday.

I have been having all sorts of problems with USB MP3 players because the songs weren't being copied when Nautilus was telling me they were, resulting in unproper unmounting of the drive and half-copied files.

Now with -sync- option enabled, when I copy a given number of files I know that the progress bar will stay there for a while, but when it's done I will be able to unmount the drive without worries. I think this option should be enabled by default for USB drives, what do you think? Should I send a bug?

---

### Post by megamania on 2005-12-28
I wouldn't call it a bug, unless when you unmount the usb device it actually*is* unmounted with your files "half-copied".

Usually, when you unmount a device, it is not unmounted until the buffer is emptied. It may take a few seconds, depending on the amount of data to be written, until it is unmounted (i.e. the device icon disappears).

Sounds to me like you unplug the usb stick right after *clicking* on "unmount", which doesn't imply that the device has already been unmounted. It's a mistake that I made in the past as well... :-(

---

### Post by Bou on 2005-12-28
Well I'm pretty sure that I've always unglugged the devices (except for my first days with Linux) AFTER the device icon dissappeared. Some times I've unmounted it, watched the icon dissappear and even after that I saw the "copying files" message on the MP3 screen, and it lasted a good while. Which would mean that the icon dissappearing doesn't imply that the data transfer has finished or the device has actually been unmounted.

Anyway, sync would only have advantages, I think. Don't you agree?

---

### Post by megamania on 2005-12-28
Well, if things are the way you're saying (and I have no reason to doubt about it) then it _is_ a bug. But you have to be absolutely sure before reporting the bug.

I've had no problems so far (except for when I unplugged the memory stick immediately after clicking on "unmount"), so it would be interesting if other people using usb sticks reported their experiences.

Regarding the advantages of the sync option, I personally don't see any _dis_advantages, but some say that flushing the buffer every once in a while not only is more efficient, but makes the memory stick last longer (they have a life-cycle of a limited number of writes, and writing a full block of data or a single byte counts as "one write" anyway, or so they say :-) ).

---

### Post by Bou on 2005-12-28
[QUOTE=megamania]Well, if things are the way you're saying (and I have no reason to doubt about it) then it _is_ a bug. But you have to be absolutely sure before reporting the bug.[/QUOTE]

I'm not, I'm quite sure but not absolutely. I would appreciate other users reporting their experiences too.

---

### Post by PtS on 2005-12-29
I've got the same problem.
The first time I noticed something was wrong was when my tracks on my USB could start in one track and then change into another one. First I thought it was amaroK but all tracks were perfect on the hard-drive. I've noticed the USB stick says that there's a transmission a long while after the device icon disappeared. I've unplugged the device hoping that it would work even though the device was busy. Then I got the error that says "eject:unable to find or open device for: `/dev/sda1'".
If this sync option is helping could you tell me how to use it and make it standard for USB devices?

---

### Post by psusi on 2005-12-29
The disadvantages to the sync option are:

1) Slows down writes to the disk
2) Causes more writes to the disk, which can wear out flash drives faster

As long as you correctly unmount the volume before removing it, it should be fine as that forces a sync.

---

### Post by PtS on 2005-12-29
> As long as you correctly unmount the volume before removing it, it should be fine as that forces a sync.

My problem is that it doesn't get unmounted correctly. After I've unmounted it it keeps going and when i remove it maybe 10 minutes later or so I get the error "eject:unable to find or open device for: `/dev/sda1'".

---

### Post by Bou on 2005-12-29
[QUOTE=PtS]my tracks on my USB could start in one track and then change into another one. First I thought it was amaroK but all tracks were perfect on the hard-drive. I've noticed the USB stick says that there's a transmission a long while after the device icon disappeared.[/QUOTE]

Yup, that's exactly what happened to me. I'll show you my /etc/fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       /home           reiserfs defaults        0       2
/dev/hdb6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1	/media/usbdisk	auto	user,noauto,sync 0	0

The last line deals with the USB device. For it to work you must specify where to mount the drive (/media/usbdisk in my case) and create the directory. At least that's how I did it, if someone has a better method and posts it I'll be grateful.

psusi, how do you know if the drive is done with the copying if it doesn't have a screen? Gnome certainly won't tell you.

---

### Post by transactionlogfiller on 2005-12-29
Do a search, I'm sure there is another thread discussing this topic.

I always unmount my device from the command line with 'sudo umount /media/usbdisk' as this waits until it has finished before giving the command prompt back. If I right click the desktop icon it pretends to have unmounted it straight away.

Incidentally, I'm not sure why I have to be root run umount from a terminal when I can do it in gnome as a normal user.

---

### Post by PtS on 2005-12-29
I tested sync options for my USB device. When I found myself waiting for a 20-minute-transmission for only one directory (music album size), I thought that i couldn't have it that way, so I changed my /etc/fstab back.
Luckily my USB device has a display telling me if there's a transmission so I wait for it to be ready before I start the next transmission.
For those who hasn't got a display on their USB device I really think there should be something done. And I would prefer knowing how much time the transmission will take.

---

### Post by psusi on 2005-12-29
Oh, if the icon vanishes right away then that IS a bug.  It should not go awy until the data has been written.

---

### Post by reedlaw on 2005-12-30
This bug has been bothering me too.  I have had many problems with files being only partially transfered to USB drives.  Sometimes I was already in class when I discovered the files I thought I had were not there.  The current behaviour in Breezy is the files are transfered very quickly to the drive.  The copying files dialog barely even displays except for the on the longest files.  Then, when there is no copying files display I unmount the drive using nautilus.  The drive icon goes away and if I pull out the drive at this point I get the error "eject:unable to find or open device for: `/dev/sda1'".  This is very un-userfriendly behavior and I'm having a hard time explaining it to all my Ubuntu converts.

The other problem I have mentioned before is the hidden trash folder that gets created *on* the USB drive itself.  Why shouldn't the trash go into the usual /home/user/.Trash folder?  By putting the hidden .Trash-user file on the USB disk, many users feel as if their deleting of files does nothing to free up disk space and it also leaves behind the files they thought they were deleting but can actually still be read in Windows.

---

### Post by Bou on 2005-12-30
so, how exactly should we report it?

I've reported a couple of bugs so far, but I'm not sure if I've done it right or they have reached the right person to fix it.

---

### Post by ufa on 2006-02-01
do NOT use sync with ur usk keys if they are formatted with vfat:

[http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html](http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html)

U will reduce the lifetime of the device thousands of time

---

