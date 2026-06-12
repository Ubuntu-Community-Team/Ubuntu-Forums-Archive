---
title: "Suspend on jaunty (Desktop)"
date: 2009-06-23
forum: General Help
---

### Post by killero24 on 2009-06-23
Hello my first post here, im not a newbie, yet im unable to configure my machine properly for suspend

i have a intel dp35dp as my mobo, and my video hard is a radeon x1650 pro running with radeonhd from git, with dri and dual head, also all my partitions are luks (swap, tmp, root)

/etc/initramfs-tools/conf.d/resume
has the uuid for the /dev/mapper/swap partition as shown on /dev/disk/by-uuid

/etc/default/acpi-support
i've tried with:
SAVE_VBE_STATE=false and true
POST_VIDEO=false and true
USE_DPMS=false and true

from the pm-suspend logs it suspend well but machine just doesnt wake up, can ssh to it or anything

i tried enableing drm debug, but after the suspend nothing else is shown, so machine didnt wake up at all

anyone has a clue about what im doing wrong or is just a problem with the radeonhd+luks?

---

### Post by synapsys on 2009-06-23
[http://en.wikipedia.org/wiki/TuxOnIce](http://en.wikipedia.org/wiki/TuxOnIce)

---

### Post by killero24 on 2009-06-25
.

---

### Post by killero24 on 2009-06-25
thanks for the info, i added the patch and recompiled the 2.6.28-13 kernel
it seems to hibernate well, but when resuming it just doesnt resume
it starts normally

my grub kernel line is:
kernel          /vmlinuz-2.6.28-13-generic root=/dev/mapper/rootfs resume=swap:/dev/mapper/swap ro quiet splash

and i modified the /usr/share/initramfs-tools/init

maybe_break premount
[ "$quiet" != "y" ] && log_begin_msg "Running /scripts/init-premount"
run_scripts /scripts/init-premount
[ "$quiet" != "y" ] && log_end_msg

# TuxOnIce
echo 1 > /sys/power/tuxonice/do_resume

maybe_break mount
log_begin_msg "Mounting root file system..."
. /scripts/${BOOT}
parse_numeric ${ROOT}
mountroot
log_end_msg

once the pc is restarted the swap is corrupted, so i assume it has the saved data
so i just create a new swap above the /dev/mapper/swap to avoid data loss in the future

btw
more /proc/meminfo
MemTotal:        4052248 kB
MemFree:         3457084 kB
SwapTotal:       4537204 kB
SwapFree:        4537204 kB
Dirty:                60 kB

so if you would point me in the right direction would be much appreciated

---

