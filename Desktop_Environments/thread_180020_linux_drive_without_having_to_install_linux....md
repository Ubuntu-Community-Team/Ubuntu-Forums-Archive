---
title: "linux drive without having to install linux..."
date: 2006-05-21
forum: Desktop Environments
---

### Post by i++ on 2006-05-21
Hi, I have 3 Hard-drives first one, with win xp install and no partitions, second one running ubuntu 5.10 (main os woo!) and a third, that has fedora on at the moment, but i dont use it and i want to format it, and just use it as a hard-drive to store files on, as my main ubuntu install is only 10 gb. How can i format it so that its a linux partition, but doesnt have a linux install, and make it automatically mount on each boot?

any help would be amazing, 

thanks, i++

---

### Post by ajgreeny on 2006-05-21
Why not use gparted or qtparted and delete the current partition(s) on the fedora drive (hdc?), then format the whole drive in fat32 to use as a storage drive for both winXP and ubuntu.
Then make a new folder in /media called whatever you wish (storage?), and finally add this line to your /etc/fstab:-
/dev/hdc1 /media/storage vfat umask=000 0 0
I think you shoud find that the fat32 drive is mounted automatically when you boot and will be both read and write from both OS's.

---

### Post by i++ on 2006-05-21
amazing :) i love the ubuntu forum community! thanks so much !:D

---

### Post by i++ on 2006-05-21
I tried to format using gparted and i get the following error...

Error while creating /dev/hdd1

Be aware that the failure to apply this operation could affect other operations on the list.

is that because i dont have su/root power? how can i run gparted as root?

---

### Post by ajgreeny on 2006-05-21
When I try to run either gparted or qtparted, the system asks me for my password so I am then doing things as root.  Does this not happen to you?
You must have the partition you are trying to delete unmounted at the time.  Then I can not see any reason why it wouldn't delete.  Then try to make and format the new partition as fat32.  Should all work, but if not get back again and I'm sure someone will help you out further.

---

### Post by i++ on 2006-05-21
Thanks for your replies, i've got it sorted now. booted into windows (ouch! lol) and formatted the partition using PM8, the did

sudo gedit /etc/fstab

added the line..

/dev/hdd1       /media/data     ext3    defaults,errors=remount-ro 0       1

now it mounts on startup :)

thanks for your help!

---

