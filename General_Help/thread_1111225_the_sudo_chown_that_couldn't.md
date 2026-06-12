---
title: "the sudo chown that couldn't"
date: 2009-03-30
forum: General Help
---

### Post by LakesProse on 2009-03-30
Hi, sorry, couldn't really find some sort of past thread about this.

So I've a NTFS partition (say /dev/sda1) mounted on /ntfs_partition
Now when mounted, it's owner and group is root.
I tried using both sudo chown and sudo chgrp to have it assigned a new user/group. [sudo chown -Rv NewUser /ntfs_partition] and [sudo chgrp -Rv NewUser /ntfs_partition] and I tried different variations on those commands. And in every case, the system would *confirm* that ownership was changed to NewUser but when I would go back and ask with [ls -la] about it, it would still list as both owner and group.

Furthermore, the NTFS partition was automounted in fstab and had, in it's option coloumn, something like guid=046. I erased that, remounted it and still, same problem. If the problem doesn't stem in fstab, I don't know what it is !

---

### Post by unutbu on 2009-03-30
You can never use sudo chown on an NTFS filesystem. 
The owner and group of all files and directories are set at mount-time on NTFS filesystems. 

To set the owner and group using /etc/fstab, the options you need are ```
uid=1000,gid=1000
``` if NewUser has UID=1000 and GID=1000. (Note the option name to set the group is gid, not guid).

---

### Post by coffeecat on 2009-03-30
Just to add: NTFS, being a microsoft filesystem, doesn't support Unix/Linux permissions. By the magic of the ntfs-3g driver, all folders and files on a mounted NTFS partition are owned by root (for some perfectly good reason I can't remember) - right-click on a file in an NTFS partition and look at Properties > Permissions. **But they are accessible read/write by ordinary users.** You don't have to chown anything.

In fact my fstab entry couldn't be easier:

```
/dev/sdb1    /media/Data    ntfs-3g        defaults    0 0
```It's automounted at boot time, and 'just works'. Never had any problems with it.

---

### Post by LakesProse on 2009-03-30
Okay, unubtu, I'll try the gid and uid options in fstab, thanks.
And thanks coffeecat, but virtualbox has been giving me some problems with the ntfs partition.

---

### Post by coffeecat on 2009-03-31
> **LakesProse said:**
> And thanks coffeecat, but virtualbox has been giving me some problems with the ntfs partition.

Ah, you didn't say you were using VirtualBox in your first post. That's an entirely different matter. Are you running Windows as the host and running Ubuntu as a guest OS? If so, try this:

Install guest additions in Ubuntu (if you haven't already).
Create a folder for sharing in Windows and set up a shared folder in Ubuntu.
Add an entry to the Ubuntu /etc/fstab to mount the shared folder at bootup. This will be of the form:

```
sharename        mountpoint       vboxsf     options    0 0
```I can help you with the details if you need.

Lastly, in Windows, create a shortcut to the NTFS partition in the shared folder.

I can't guarantee this will work (my experience with VirtualBox is using MacOS as a host), but if all goes well, when you open the shared folder in Ubuntu, you should see the link to the NTFS partition which, hopefully, you should be able to navigate into. That way, Ubuntu only has to deal with the vboxsf filesystems (drivers included with guest additions) and Windows deals with the NTFS filesystem.

---

### Post by LakesProse on 2009-04-08
A little late to reply but better late than never ?
In any case, it was VirtualBox hosted on Ubuntu and guest OS was Windows XP except that Windows XP had trouble writing on another partition where NTFS-wrapped data was.

The suid and guid in /etc/fstab did the trick.
Thanks all for help :)

---

