---
title: "HOWO backup and restore linux or window$ partitions or folders"
date: 2009-01-07
forum: General Help
---

### Post by Adrian Nania on 2009-01-07
:-k   A great choice for backup and restore is "partimage". Even better, one can use "tar". With tar, you have total control of what to backup, what to restore, and where. Here are a few scripts I am using to backup/restore linux or windows  partitions. _**You must change the relative path where you whant to save/restore something and the partition/directory name. Once you saved and changed the script locally, do not forget to make it executable.**_ By using --update switch for tar command, you can incrementally backup only modified files. By using the script on a window$ partition, the activation key is automatically saved and restored. One small annoyance with windows partitions: after restoration, you will get a junk file "notepad.ini" placed inside startup folder for any local user. Just delete this weirdo and everything else is OK.

_**[COLOR="Blue"]To backup partition sda1 run this script as root:[/COLOR]**_
```

#!/bin/bash
# sudo /home/work/src/root-sda1-to-bak
# created by Adrian Nania 20081228

rm -rf /home/bak/linux/root-sda1-to-bak.log
clear
echo Please wait ...
echo
time {
cd /home/bak/linux
rm -rf ./sda1.log ./sda1.tar
cd /home/disks/sda1
tar     --create \
        --atime-preserve \
        --absolute-name \
        --block-number \
        --check-links \
        --show-omitted-dirs \
        --verbose --verbose \
        --index-file=/home/bak/linux/sda1.log \
        --file=/home/bak/linux/sda1.tar \
        ./*
chown -R adi:adi /home/bak/linux
} >/home/bak/linux/root-sda1-to-bak.log 2>&1
echo
echo root-sda1-to-bak END
echo
echo check the following Error messages -if any- to ensure no critical errors occured:
echo
grep error /home/bak/linux/sda1.log
grep Error /home/bak/linux/sda1.log
grep error /home/bak/linux/root-sda1-to-bak.log
grep Error /home/bak/linux/root-sda1-to-bak.log
rm -rf /home/bak/linux/*.log

```

_**[COLOR="Blue"]To restore partition sda1 run this script as root:[/COLOR]**_
```

#!/bin/bash
# sudo /home/work/src/root-sda1-from-bak
# created by Adrian Nania 20081228

rm -rf /home/bak/linux/root-sda1-from-bak.log
clear
echo Please wait ...
echo
time {
cd /home/bak/linux
rm -rf ./hda1.log
cd /home/disks/sda1
rm -rf ./*
tar     --extract \
        --atime-preserve \
        --absolute-name \
        --block-number \
        --check-links \
        --show-omitted-dirs \
        --verbose --verbose \
        --index-file=/home/bak/linux/sda1.log \
        --file=/home/bak/linux/sda1.tar
} >/home/bak/linux/root-sda1-from-bak.log 2>&1
echo
echo root-sda1-from-bak END
echo
echo check the following Error messages -if any- to ensure no critical errors occured:
echo
grep error /home/bak/linux/sda1.log
grep Error /home/bak/linux/sda1.log
grep error /home/bak/linux/root-sda1-from-bak.log
grep Error /home/bak/linux/root-sda1-from-bak.log
rm -rf /home/bak/linux/*.log

```

_**[COLOR="Blue"]To backup a (ntfs) window$ partition run this script as root:[/COLOR]**_
```

#!/bin/bash
# sudo /home/work/src/root-WinXP-to-bak
# created by Adrian Nania 20081228

rm -rf /home/bak/WinXP/root-WinXP-to-bak.log
clear
echo Please wait ...
echo
time {
cd /home/bak/WinXP
rm -rf ./WinXP.log ./WinXP.tar
cd /home/disks/WinXP
tar     --create \
        --atime-preserve \
        --absolute-name \
        --block-number \
        --check-links \
        --show-omitted-dirs \
        --verbose --verbose \
        --index-file=/home/bak/WinXP/WinXP.log \
        --file=/home/bak/WinXP/WinXP.tar \
        ./*
chown -R adi:adi /home/bak/WinXP
} >/home/bak/WinXP/root-WinXP-to-bak.log 2>&1
echo
echo root-WinXP-to-bak END
echo
echo check the following Error messages -if any- to ensure no critical errors occured:
echo
grep error /home/bak/WinXP/WinXP.log
grep Error /home/bak/WinXP/WinXP.log
grep error /home/bak/WinXP/root-WinXP-to-bak.log
grep Error /home/bak/WinXP/root-WinXP-to-bak.log
rm -rf /home/bak/WinXP/*.log

```

_**[COLOR="Blue"]To restore a (ntfs) window$ partition run this script as root:[/COLOR]**_
```

#!/bin/bash
# sudo /home/work/src/root-WinXP-from-bak
# created by Adrian Nania 20081228

rm -rf /home/bak/WinXP/root-WinXP-from-bak.log
umount /dev/sdb1
apt-get install -y ntfsprogs
mkntfs -f /dev/sdb1
mount -a
chown -R adi:adi /home/bak/WinXP
clear
echo Please wait ...
echo
time {
cd /home/bak/WinXP
rm -rf ./*.log
cd /home/disks/WinXP
tar     --extract \
        --atime-preserve \
        --absolute-name \
        --block-number \
        --check-links \
        --show-omitted-dirs \
        --verbose --verbose \
        --index-file=/home/bak/WinXP/hda1.log \
        --file=/home/bak/WinXP/WinXP-i7-clean-20081228.tar
} >/home/bak/WinXP/root-WinXP-from-bak.log 2>&1
echo
echo root-WinXP-to-bak END
echo
echo check the following Error messages -if any- to ensure no critical errors occured:
echo
grep error /home/bak/WinXP/WinXP.log
grep Error /home/bak/WinXP/WinXP.log
grep error /home/bak/WinXP/root-WinXP-to-bak.log
grep Error /home/bak/WinXP/root-WinXP-to-bak.log
rm -rf /home/bak/WinXP/*.log

```

---

### Post by PoPpiLLs on 2009-10-01
Your script still does the backup but i get this error when I first run it

time: cannot run {: No such file or directory
Command exited with non-zero status 127
0.00user 0.00system 0:00.00elapsed 0%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+71minor)pagefaults 0swaps

---

### Post by Adrian Nania on 2011-03-03
Try to change the script extension to *.sh
I think the "time { }" wrap does not work sometimes

---

