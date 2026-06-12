---
title: "Disappeared NTFS Drive"
date: 2012-12-21
forum: Desktop Environments
---

### Post by barabas1 on 2012-12-21
Hi,

i'm a nub (^_^) and i use Xubuntu in dual boot with Windows Xp 32 bit.

I have a problem since I installed ntfs-config and ntfs-3g. I properly configured ntfs-config to mount at startup the Windows partition (NTFS). Anyway after reboot I cannot see the windows drive anymore in file manager. Even if i say to the desktop manager to show the removable drives on desktop it doesn't come up.

I tried removing ntfs-config and nothing changed. So I executed the following commands in the terminal

```
sudo blkid
```

and I get

```
/dev/sda1: UUID="140C7ED70C7EB37A" TYPE="ntfs" 
/dev/sda3: UUID="0d000752-81a0-4b08-89f2-6268e65cb2bc" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="b7db6c43-7801-4864-b838-990f3b8ed153" TYPE="swap" 
```

then I digit

```
cat /etc/fstab
```

and this is what i get

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sda3 :
UUID=0d000752-81a0-4b08-89f2-6268e65cb2bc	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda1 :
UUID=140C7ED70C7EB37A	/media/afc/140C7ED70C7EB37A	ntfs-3g	defaults,nosuid,nodev,locale=en_US.UTF-8	0	0
/dev/fd0	/media/floppy0	auto	rw,user,noauto,exec,utf8	0	0
UUID=82b1fc7e-56d2-4b03-9379-aa5772600b54	none	swap	sw	0	0

#UUID=34025582-ff5e-493c-8052-5bb50f70e1eb	none	swap	sw	0	0

```

I looked for a solution on forum but i did not find it.

Can someone help me to fix this?
Thanks a lot!

---

### Post by coffeecat on 2012-12-21
> **barabas1 said:**
> 
I have a problem since I installed ntfs-config

You are not alone - many do! :wink: I suggest you read what it says under "Automatic Configuration" here:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

In fact, you might find that whole page useful.

> **barabas1 said:**
> I tried removing ntfs-config and nothing changed.

I'm glad to hear you've removed ntfs-config, but the reason that nothing changed is that ntfs-config is a configuration application. You will need to reconfigure /etc/fstab manually. So...

This is the relevant line from your /etc/fstab:

> **barabas1 said:**
> ```

#Entry for /dev/sda1 :
UUID=140C7ED70C7EB37A	/media/afc/140C7ED70C7EB37A	ntfs-3g	defaults,nosuid,nodev,locale=en_US.UTF-8	0	0
```

I'm a bit puzzled by the mountpoint for your ntfs partition - that's not a mountpoint I would expect from ntfs-config. Post the output of these commands and then I can suggest an edit to that line and possibly a different mountpoint.

```
ls -l /media
ls -l /media/afc
```

Questions: does "afc" mean anything to you? Is it your Ubuntu account name?

---

### Post by barabas1 on 2012-12-21
Thank you so much! :)

Yes, afc is my account name.

I executed the code you told me and I got

```
drwxr-x---+ 3 root root 4096 Dec 20 10:24 afc
lrwxrwxrwx  1 root root    7 Dec  5 13:39 floppy -> floppy0
drwxr-xr-x  2 root root 4096 Dec  5 13:39 floppy0
```

and for the second command

```
drwxrwxrwx 1 root root 16384 Dec 19 16:09 140C7ED70C7EB37A
```


ehmm I also read the page you suggest, but I did not understand how to solve my specific problem.. (nub boy speaking here ^_^).
Do you have any solution?

---

### Post by coffeecat on 2012-12-21
> **barabas1 said:**
> 
Yes, afc is my account name.

Yes, I thought so. With effect from 12.10 (are you running 12.10?) if you mount partitions by means of the file manager, they are mounted on /media/<yourusername>/<mountpoint>. In earlier versions of Ubuntu, they were mounted on /media/<mountpoint>. I suspect that you had the partition already mounted from the file manager when you ran ntfs-config and it got itself confused. For /etc/fstab entries I prefer to use /media/<mountpoint> and leave /media/<yourusername>/<mountpoint> for the filemanager.

So, first create a mountpoint. From the terminal:

```
sudo mkdir /media/Windows
```

You can substitute almost any string you want instead of "Windows". If you do choose a different mountpoint name, avoid spaces - they simply add complexity you don't need.

You now need to edit /etc/fstab manually. Do do this, from a terminal:

```
gksu gedit /etc/fstab
```

Take care - this is a system file and you have root privileges with that command. Double-check everything.

Edit this line:

```
UUID=140C7ED70C7EB37A	/media/afc/140C7ED70C7EB37A	ntfs-3g	defaults,nosuid,nodev,locale=en_US.UTF-8	0	0
```

So that it looks like this:

```
UUID=140C7ED70C7EB37A	/media/Windows	ntfs-3g	defaults,windows_names,locale=en_US.utf8	0	0
```

Change /media/Windows if you chose a different mountpoint name. Are you in the USA? If not, you might want to change the locale option. Details in the wiki link, but if you need help, post back.

Now save and close the text editor. There's a bug with gedit which causes it to open a second empty document and then complain that it is unsaved when you try to close it. So long as you have saved your edited /etc/fstab, simply ignore the message and close.

Now, from a terminal:

```
sudo umount /media/afc/140C7ED70C7EB37A
sudo mount -a
```

Or, instead of those two commands, simply reboot.

Does that work?

I suggest you also read the first two sections of the wiki page I linked, and take note about use of the file manager versus /etc/fstab and concerns about mounting your Windows C: partition. The advice it gives about mounting your Windows C: partition read-only I agree with (partly because I wrote it! :)). If you do want read-only access to your C: partition, post back and I can suggest a different set of mount options. (They're in the wiki page anyway.)

---

### Post by barabas1 on 2012-12-21
> Yes, I thought so. With effect from 12.10 (are you running 12.10?) if you mount partitions by means of the file manager, they are mounted on /media/<yourusername>/<mountpoint>. In earlier versions of Ubuntu, they were mounted on /media/<mountpoint>. I suspect that you had the partition already mounted from the file manager when you ran ntfs-config and it got itself confused. For /etc/fstab entries I prefer to use /media/<mountpoint> and leave /media/<yourusername>/<mountpoint> for the filemanager.

ok, I have Xubuntu 12.10. And yes I firstly mounted with tunar the Windows drive and later on I installed ntfs-config (which is now uninstalled).

I did everything else that you said (except for opening the fstab with this command ```
gksudo leafpad /etc/fstab
``` because ```
gksu gedit /etc/fstab
``` did not work).

I executed the unmount commands and also rebooted, but I still can't see the drive in Thunar...

---

### Post by LewisTM on 2012-12-21
If I may, I think the OP has had access to his NTFS drive all along in /media/afc/...

The problem he mentions is that all of a sudden, the drive is no longer on the desktop and in Thunar's side pane. That's a Xubuntu-specific behavior. When you specify that a drive is to be mounted at boot in /etc/fstab, it becomes an "internal" drive (as in "part of the system") and is not shown as user mountable on the desktop and in Thunar. It's still reachable in /media/... and you might want to bookmark it.

Barabas1: You could make the drive appear where you expect by adding [FONT="Courier New"]user[/FONT] to your ntfs-3g parameters in fstab. Or you could unmount everything, erase the mount point and the fstab entries, and simply add this command as a Startup Application.
```
gvfs-mount -d /dev/sda1
```
Also, I'd recommend the new [Thunar 1.6]("http://www.webupd8.org/2012/11/install-thunar-with-tabs-support-in.html") which presents drives in a more intuitive way.

Cheers!

---

### Post by barabas1 on 2012-12-21
WOW :)

> When you specify that a drive is to be mounted at boot in /etc/fstab, it becomes an "internal" drive (as in "part of the system") and is not shown as user mountable on the desktop and in Thunar. It's still reachable in /media/... and you might want to bookmark it.
Yes, in media i see it!

> Barabas1: You could make the drive appear where you expect by adding user to your ntfs-3g parameters in fstab.
Ok i would go for this solution, but would you please explain me how (don't forget I'm a nub ^_^).

---

### Post by LewisTM on 2012-12-21
Your fstab line should be changed to this
> UUID=140C7ED70C7EB37A	/media/afc/140C7ED70C7EB37A	ntfs-3g	**user**,nosuid,nodev,locale=en_US.UTF-8	0	0
Then reboot.

---

### Post by coffeecat on 2012-12-21
> **barabas1 said:**
> ok, I have Xubuntu 12.10.

@barabas1, my apologies for missing that you were running Xubuntu.

> **LewisTM said:**
> Your fstab line should be changed to this

Then reboot.

@LewisTM, we could discuss which mount options to add until the end of time (considering today's date! :)), but I would earnestly suggest that the OP include "windows_names" as well. Without that mount option I've managed to save a file to NTFS with an "illegal" character in the filename on more than one occasion. Ubuntu doesn't mind at all, but Windows certainly does, and I've wasted a lot of time untangling this before I realised what the problem is.

---

### Post by barabas1 on 2012-12-21
Thanks a lot to the both of you! :)

So i guess i solved the problem combining your suggestions. This is what i did:

```
sudo mkdir /media/Windows
```

and then changed the line in fstab in

```
UUID=140C7ED70C7EB37A	/media/Windows	ntfs-3g	user,nosuid,nodev,locale=en_US.UTF-8	0	0
```

Merry Xmas and thanks again! ):P

---

### Post by LewisTM on 2012-12-21
So I just tested the effect of the "user" switch on an NTFS thumb drive and it did NOT work. Sorry :(

It works for other filesystems. It seems that ntfs-3g cannot be used for mounting as a user and thus won't show as user mountable by Xubuntu.

The only solution to get the old desktop behavior is to mount with gvfs-mount. It gives you no mount option, will mount in /media/afc/<UUID or LABEL> but should meet most demands.

---

### Post by barabas1 on 2012-12-21
> **LewisTM said:**
> So I just tested the effect of the "user" switch on an NTFS thumb drive and it did NOT work. Sorry :(

It works for other filesystems. It seems that ntfs-3g cannot be used for mounting as a user and thus won't show as user mountable by Xubuntu.

The only solution to get the old desktop behavior is to mount with gvfs-mount. It gives you no mount option, will mount in /media/afc/<UUID or LABEL> but should meet most demands.

LewisTM Your solution with user is now working for me...

---

### Post by LewisTM on 2012-12-21
Well I'll be damned! I think the reason it didn't work for me was that I used /mnt as the mount point, for testing purposes. It works if you put the mount point inside /media, as you did.

Glad to have helped! Please mark as SOLVED using the thread tools.

---

