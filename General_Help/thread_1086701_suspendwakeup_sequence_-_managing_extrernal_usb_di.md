---
title: "suspend/wakeup sequence - managing extrernal usb disks"
date: 2009-03-04
forum: General Help
---

### Post by yxlbaz on 2009-03-04
Hardy - apm module loaded on advice to make suspend work

Suspend works fine and the system comes back as expected except that my external usb hard drive apears to be empty.  I can fix it with a umount <mount-point> and mount -a.  Unmounts failed device and remounts it again.

I was trying to find the scripts that do the suspend/wakeup business so that I can add the unmount and mount before and after automatically and avoid possible filesystem damage.  

I've looked in /etc/apm and /etc/acpi and tried sending text to a log from some of these scripts but I have not yet found a likely one that seems to do anything.  (/etc/acpi/sleep.sh /etc/acpi/sleepbtn.sh /etc/apm/scripts.d/alsa)

My disk is now mounted from fstab.  I had the same problem before when it was discovered and mounted automatically as a removable disk on reboot. I can see the cause, I think, where I would not expect a disk device that loses power during a suspend to be active on resume and power-up.

I hope to get to a better solution than manually unmounting and remounting though.

Any ideas?

Thanks

---

### Post by heindsight on 2009-03-04
Have a look in your /var/log/syslog after resuming from suspend. I suspect that you'll see messages about usb hubs losing power or being reset.

Have a look at this: [http://www.mjmwired.net/kernel/Documentation/usb/persist.txt](http://www.mjmwired.net/kernel/Documentation/usb/persist.txt)
The solution mentioned there is to enable CONFIG_USB_PERSIST in the kernel. This option is enabled by default in the ubuntu kernel (at least on my machine running kernel 2.6.22-23-generic on hardy), but you have to specifically enable it for each individual device by doing:
```
echo 1 | sudo tee /sys/bus/usb/devices/.../power/persist
```
where ... should be replaced by the device's ID. You may have to do a bit of digging around in /sys/bus/usb/devices to find the correct path for your device. Looking at the output of
```
lsusb
```
may help.

I must warn you, I've never actually used this approach, so I don't know how well it works. I usually just unmount my usb disks before suspending the machine...

---

### Post by heindsight on 2009-03-04
If you want to try to automatically unmount your usb disk on suspend and remount it on resume, you can put a script to do that in /etc/pm/sleep.d (since hardy this is where suspend/resume scripts should go).

If your disk is mounted from fstab, you could perhaps try something like:
```

#!/bin/sh

case $1 in
    hibernate|suspend)
        umount <mountpoint>;;
    thaw|resume)
        mount <mountpoint>;;
esac

```
Of course you should replace <mountpoint> with your actual mount point.

You should keep in mind though, that this will not work if there are any open files on the disk - umount will fail because the file system is busy. You could maybe use the -l option to do a lazy unmount, but I'm not sure that will work in this case - I haven't tried it, I just unmount manually, I tend to feel it's safer (although it does mean I always have to remember to unmount).

EDIT:
if you want to use this approach you may want to read the pm-suspend manual:
```
man pm-suspend
```

---

### Post by yxlbaz on 2009-03-05
Thanks Heindsight for that.

I'm trying this code in /etc/pm/sleep.d for now.  My filesystems are labelled MaxPort and MaxPort2 -
________________________________________
case $1 in
    hibernate|suspend)
        umount /media/MaxPort /media/MaxPort2  || exit 1 ;;
        rm /media/MaxPort /media/MaxPort2
    thaw|resume)
                ;;
esac
____________________________________________

I don't include a mount because I have removed the fstab entries.  I prefer to leave as much as possible as it was before.  I had noticed that the filesystems are remounted automatically after a suspend if there is no fstab entry, which makes sense.

The mount points need to be removed because whatever remounts the filesystems on resume does not delete old ones but makes new ones with an underscore appended to their names.  This confuses software (and me)

I've done a few trials with different setups and this seems OK now so I'm hoping.

Cheers

---

