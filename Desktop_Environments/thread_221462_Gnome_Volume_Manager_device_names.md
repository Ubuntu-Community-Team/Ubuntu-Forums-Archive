---
title: "Gnome Volume Manager device names"
date: 2006-07-23
forum: Desktop Environments
---

### Post by GNUbieNZ on 2006-07-23
Hi,

Im using Dapper running Gnome Volume Manager as normal.  I have two optical drives (one dvd reader and one writer). When gnome volume manager mounts my dvds, the mount points are /media/dvdrecorder (for the dvd reader!!!) and /media/dvdrecorder-1 (for writer).

I was wondering if I could change the mount points to more logical names.  I know I can make a static entry in /etc/fstab but that kinda defeats the purpose of gvm.

Just being picky, but it would be nice if I could change it!!

Thanks
Dave

---

### Post by joft on 2006-07-25
Hi,

I don't know if there is a GUI-way of doing this and I don't know if it works for cd/dvd/readers/writers, since I used the following solution to mount an external harddisk on the same mount point:

file /etc/hal/fdi/policy/harddisk.fdi

```

<?xml version="1.0" encoding="ISO-8859-1"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">

    <device>
        <match key="block.is_volume" bool="true">
            <match key="volume.fsusage" string="filesystem">
                <match key="volume.uuid" string="430D-82CF">
                    <merge key="volume.policy.desired_mount_point" type="string">usb120a</merge>
                </match>
            </match>
        </match>
    </device>
</deviceinfo>

```

As you might see you can configure HAL with "matching" statments, which decide if a "merge" happens. In my example I look for the property block.is_volume=true and if the property volume.uuid is 430D-82CF. If all matches are true, a bit of information is "merged" into the configuration. That information says, what the "desired mount point" is. [Later I found out that this isn't neccessary for harddisks, since GMV uses the label of the filesystems on the harddisks for mount point names.]

The problem with dvd/rw's now is, that you can't "match" for volume.uuid for example, since you want all dvds being insert on a specific mount point and not just one with a special uuid.

So you have to search for other criteria to match on. And as I said - I don't know if there is something appropriate - but perhaps this post gives you a starting point for further research.

---

### Post by slyboots on 2006-08-25
Hello.
I have some problem....
My mouted HDD is mounted on Desktop. I have 2 volumes. The first is mounted like the same in fstab.(/media/hda1), with the name [COLOR="Red"]**hda1**[/COLOR]. The next voleme was with the name **[COLOR="Red"]hda5[/COLOR]**(/media/hda5). 
Now is his name changed to _PNG, but in the fstab is all correctly. But i dont know how, or why, but now is the name thats on the Desktop [COLOR="Red"]**_PNG**[/COLOR]. I will change it to the name like before (hda5). 

How cann i make it? :o

---

### Post by jackn on 2006-08-25
> **GNUbieNZ said:**
> 
I have two optical drives (one dvd reader and one writer)...

I was wondering if I could change the mount points to more logical names.  

Hi, Dave.

Have been studying thotplugging and wondering about it for a while. Not much luck yet. 
But, your question puts me in mind of a makeshift workaround, if that will suit you.

How about symbolic links to the desired mountpoints?

```

sudo rmdir /media/old/mount/point
ln -s /new/mount/point /media/old/mount/point
```
It is necessary to first remove the old mountpoint, or it won't work. The symbolic link then restores it.
The new mountpoint need not be under /media.

Have experimented with my hotpluggable MP3 Player, and the result of the above maneuver is having the filesystem at *both* mountpoints, the /media/old/one and the /new/mountpoint. 
Don't know if that should bother anyone.

In addition, following this procedure, I can only remove the device with a 'umount' command - a 'pmount' doesn't work:

```
sudo umount /dev/your/device /either/mountpoint
```

And, while it *will* unmount the device, it spits out an error message claiming that /dev/your/device is not mounted.

BTW: Do you unmount your DVD player before removing the DVD? I guess you must, as the rack is probably locked until you do. Do you use 'pumount'? I unmount the MP3 Player, although there's no physical barrier to removal. It is necessary, though, isn't it?! I use 'pumount'.

Finally, as you say, going the /etc/fstab way overrules the hotpluggability. 
I *have*, however, also tried to add an /etc/fstab entry. My purpose was not to revert to ordinary 'mount'. I was hoping to take advantage of the use of 'pmount' in the 'pmount-hal' procedure on which hotplugging is based.
I was wondering whether, as 'man pmount' says, 'pmount' will just default to the fstab entry. 
It didn't work, no mounting at all occurred. Apparently, the 'pmount' used in hotplugging is somehow constrained. 

Would love some feedback.

Jackn

---

