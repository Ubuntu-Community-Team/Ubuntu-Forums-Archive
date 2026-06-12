---
title: "Debian 8 won't boot if external USB drives unplugged"
date: 2016-11-01
forum: Debian
---

### Post by stpatryck on 2016-11-01
Hello folks,


I have 4 external USB 3.0 hard drives plugged in, but if I unplug any of the drives, the system boots to command line interface.  I've included the contents of my /etc/fstab file below.


Is there any way I can get my system to boot without editing my /etc/fstab file every time I unplug a drive?




# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=086e3a28-8ea7-43f9-b33c-1240b0cc327d /               ext4   noatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=114c6d91-ab20-405e-94d3-e52e63eeaae5 none            swap    sw              0       0
/dev/sr0        /media/cdrom0   udf,iso9660 user,noauto     0       0
#
#
#/dev/sdc1: LABEL="Seagate 2TB" UUID="A2DA435FDA432EBB" TYPE="ntfs" PARTUUID="5af55c19-01"
UUID=9500f755-74b4-4d41-88b7-425c446b399e  /media/seagate-2tb  ext4   defaults 0  0
#
#
#/dev/sdb3: LABEL="WDC 500GB" UUID="64D2A3DDD2A3B1AA" TYPE="ntfs" PARTUUID="6be56dac-03"
UUID=64D2A3DDD2A3B1AA   /media/wdc-500gb      ntfs-3g defaults,locale=en_US.utf8 0 0
#
#
#/dev/sdd1: LABEL="TOSHIBA 2TB" UUID="72543E4C543E12F9" TYPE="ntfs" PARTUUID="74650274-01"
UUID=72543E4C543E12F9   /media/toshiba-2tb    ntfs-3g defaults,locale=en_US.utf8 0 0  
#
#
#/dev/sde1: LABEL="TOSHIBA_1TB_1" UUID="DA702DB6702D9A71" TYPE="ntfs" PARTUUID="c5962e45-01"
UUID=DA702DB6702D9A71   /media/toshiba-1tb-1  ntfs-3g defaults,locale=en_US.utf8 0 0 
#
#
#/dev/sdf1: LABEL="TOSHIBA_1TB_2" UUID="30963F81963F469E" TYPE="ntfs" PARTUUID="fdadbe28-01"
UUID=30963F81963F469E   /media/toshiba-1tb-2  ntfs-3g defaults,locale=en_US.utf8 0 0 
#
#
#/dev/sdg1: LABEL="My Passport" UUID="4E1AEA7B1AEA6007" TYPE="ntfs" PARTUUID="e59e27ed-01"
UUID=4E1AEA7B1AEA6007   /media/mypassport     ntfs-3g defaults,locale=en_US.utf8 0 0

---

