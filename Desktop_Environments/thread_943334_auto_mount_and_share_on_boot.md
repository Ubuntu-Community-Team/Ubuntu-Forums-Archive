---
title: "auto mount and share on boot"
date: 2008-10-10
forum: Desktop Environments
---

### Post by shnurui on 2008-10-10
I haven't used linux, or any version of Unix since there was only Unix.  These things I'm not finding in the Faqs or manuals.

a) Drive adressing.

How do you change a drive in linux?  in dos it is simply )drive(:  Its appearently much more and unnessicarily complicated in linux.

b) What is the base list of mount options?  Not how to put them in, just all of the mount options listed as one would look in a dictionary?

c) how does one put those mount options in, using the gui mount options interface?

d) How would one set a whole drive, say, used for music and shared programs, completely and absolutely open, not owned by any one user, but locked against remote access?

Any link to these answers would be helpful:)

Thanks,

P.S.  K.I.S.S. it for us old fogies?

---

### Post by shnurui on 2011-02-05
Still no answers?

On Fstab how do I force an on boot mount of my second drive?

/dev/sda2 ??? ??????????? ? ? ?  ??  ?

---

### Post by VCoolio on 2011-02-05
for example:
/dev/sda2 /media/disk2 ext4 user,auto 0 0
This needs /media/disk2 to exist and of course choose the right file system type. If samba is running and you shared the disk earlier, it will be shared once mounted. And read 'man fstab' and the fstab howto in the howto section of these forums.

---

### Post by ankspo71 on 2011-02-05
Hi,
A decent graphical fstab editor is called pysdm (Storage Device Manager)
[http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)
It is available in Ubuntu's repositories too, so can you find it in your favorite package manager (Synaptic or Software Center, etc)
It's not really that self explanatory though, so here's more info...

"man fstab" and "man mount" contain useful information for mounting drives.

My auto-mounted drive is setup like this in /etc/fstab:
/dev/sdb8 /media/sdb8 ext4 users 0 0 
Except I use UUIDs so the line looks like this:
UUID=ba75a98e-4b9a-40b3-8ce1-a8d13a73e9a3 /media/sdb8 ext4 users 0 0

To find the UUID to your partitions, run this command in the terminal:
```
sudo  blkid
```

If you are looking for a glossary of mount options to use in fstab, then open your terminal and paste the following command
```
man mount
```
Then when that opens the manpage for mount, scroll halfway down and see the part about:
FILESYSTEM INDEPENDENT MOUNT OPTIONS

Much more info can be found here:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Hope this helps.

---

### Post by Rhizoid on 2011-02-05
> **shnurui said:**
> Still no answers?

On Fstab how do I force an on boot mount of my second drive?

/dev/sda2 ??? ??????????? ? ? ?  ??  ?

Add it to fstab

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Or there's a GUI tool listed here:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

How are you mounting it at the moment?  If you're using something along the lines of:

```
sudo mount /dev/sda2 /{insert mount point of choice here}
```

Try this in terminal:

```
sudo blkid | grep sda2
```

Select with the mouse the UUID for /dev/sda2 and copy it, or just write it down.

Now add the mount details to /etc/fstab:

```
sudo nano /etc/fstab
```

Scroll to the end of the file and add the following code, adjusting for your system and requirements:

```
# mount /dev/sda2 on boot
UUID={insert UUID of sda2 here}    /{mount point}   ext2/3/4 (delete as appropriate)   defaults   0   0
```

Press CTRL+o and press RETURN to write the file, then CTRL+x to exit the nano editor.

To test it works:
```

sudo umount /dev/sda2
sudo mount -a
mount | grep sda2
```

If don't see an entry for sda2 something it wrong and you need to carefully check the details you put into /etc/fstab.

What you should see is something like:

```

/dev/[color=red]sda2[/color] on /mountpoint type ext4 (rw)

```

Hope that helps,

---

### Post by Rhizoid on 2011-02-05
By the way... 2 years plus waiting for a reply?  That's some patience! :D

---

