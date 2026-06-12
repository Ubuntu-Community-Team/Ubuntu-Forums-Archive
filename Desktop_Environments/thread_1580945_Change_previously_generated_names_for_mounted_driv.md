---
title: "Change previously generated names for mounted drives"
date: 2010-09-24
forum: Desktop Environments
---

### Post by mightymouse2045 on 2010-09-24
Hi,

This has been asked and answered all over the place but not to my satisfaction or I cannot find the relevant help in doing it.

Basically I have changed the default mount names for my windows partitions in Ubuntu. They were /media/data, /media/data_,/media/system reserved, etc 

They are now /media/C,D,E,F

I have rebooted etc after the changes and when I look in Gnome places or in Nautilis the OLD names still show up.

HOWEVER when I run Nautilis as the root user all the CORRECT NEW names appear.

ALSO - if I create a BRAND NEW user account and login as that all the OLD names show up??!? WTF

So this is something to do with ROOT access or whatever that is not allowing the names to be updated somehow?!?!?

As I use these disks in windows (obviously) I DONT want to change their labels. and basically this SHOULDN'T be the solution everyone is suggesting!

Root can generate the new names automatically based on the mount point in FSTAB why can't other users - and HOW to do do it MANUALLY?

---

### Post by gzarkadas on 2010-09-24
The cleanest solution if you want to see your windows disks by drive letter is to make 4 directories under /mnt (ie /mnt/C , mnt/D, mnt/E, mnt/F) and modify your entries to /etc/fstab to mount them there. This way you avoid overlaps with the gvfs code that automounts media in /media (and uses their label for that).

If you want the users to be able to mount the disks, specify the _user_ or _users_ options to the related fstab line. Type `man fstab' in a terminal to see info about the options.

If you want to see the disks in nautilus' "Places" bar, modify it using the menu `Bookmarks|Modify Bookmarks...' (or press Ctrl+B).

---

### Post by mightymouse2045 on 2010-09-26
> **gzarkadas said:**
> The cleanest solution if you want to see your windows disks by drive letter is to make 4 directories under /mnt (ie /mnt/C , mnt/D, mnt/E, mnt/F) and modify your entries to /etc/fstab to mount them there. This way you avoid overlaps with the gvfs code that automounts media in /media (and uses their label for that).

If you want the users to be able to mount the disks, specify the _user_ or _users_ options to the related fstab line. Type `man fstab' in a terminal to see info about the options.

If you want to see the disks in nautilus' "Places" bar, modify it using the menu `Bookmarks|Modify Bookmarks...' (or press Ctrl+B).

It really just irks me that root even though it has previously mounted these drives automatically before with the auto generated names, after changing the mount points to folders I created root mounts them under the new names, but my normal user account still mounts them under the auto generated names and that is what shows up on the desktop and in places. Why does root correctly display the changed names but my user account doesn't. I cannot find any info on this anywhere.

Yes your solution will work and that is what I have done - but it's not the answer I was looking for :P 

That said thanks for the reply man :)

Cheers!

---

### Post by mightymouse2045 on 2010-09-26
Love your signature

---

### Post by Morbius1 on 2010-09-26
> Basically I have changed the default mount names for my windows  partitions in Ubuntu. They were /media/data, /media/data_,/media/system  reserved, etc 
Changed them where? Do you mean you changed their labels or do you mean you changed the mountpoints in fstab?
If you post the output of the following commands maybe we can figure this out:
```
cat /etc/fstab
``````
sudo blkid -c /dev/null
```

---

### Post by gzarkadas on 2010-09-27
> **mightymouse2045 said:**
> Love your signature Thanks :).

Now, about your problem, what puzzles me is that since (I assume) your windows partitions are in a disk always connected to the computer (most probably an internal IDE/SATA disk) if you mount them through /etc/fstab then they should not show in Nautilus places. All partitions in my system that are mounted from /etc/fstab do not show in Nautilus.

Do you specify the `user' or `users' or `noauto' options for these mounts? If yes, turning them off (that is deleting them from the corresponding lines in /etc/fstab) should fix this. If not, then:

1. Try first to much them with UUID; run the blkid command suggested by Morbius1 to find them.
2. Try to make HAL to hint Gnome to not mount non-removable media. There should be in your system a file /etc/hal/preferences.fdi with this block commented out by xml comments (<!-- ... -->):
```

<!--
  <device>
    <match key="storage.hotpluggable" bool="false">
      <match key="storage.removable" bool="false">
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      </match>
    </match>
  </device>
-->

```Remove the comments (ie the first and last line shown here) and reboot. I don't know if it will work, but from what I have searched around, seems that the way to go is through HAL. Finding documentation for other commands in not such an easy task; start by looking at [http://www.freedesktop.org/wiki/Software/hal](http://www.freedesktop.org/wiki/Software/hal).

---

