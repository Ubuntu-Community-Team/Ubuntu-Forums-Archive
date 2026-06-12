---
title: "Automount of windows partitions (NTFS)"
date: 2008-10-28
forum: Desktop Environments
---

### Post by svenskmand on 2008-10-28
Hello everybody,

i've installed ubuntu (again) on a machine and needs to automount the windows partitions, I know i can to it by changing the fstab file but its a real pain to do this especially because each and every time i need to change it i don't remember how it sat it up the last time.

I Ubuntu i can easily manually mount the partitions by just clicking on them in Start -> Places -> [Partition name], but i have a lot of symbolic links into these partitions, and I don't want to manually mount the partitions every time.

Then i want to hear if/where i can ask Ubuntu to automatically mount the volume, without having to completely configure it through fstab (here i have to choose permissions uuid and so on, a real pain).

Best regards.

---

### Post by theduffman on 2008-10-28
sudo pico /etc/fastab
/dev/sda1    /media/sda1 ntfs  defaults 0    0
/dev/sda2    /media/sda2 ntfs  defaults 0    0

or whatever your partitions are named.. dont forget to make the mount points
save/exit

sudo mount -a

---

