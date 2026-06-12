---
title: "Hard Drive Light Constanyl Flashing"
date: 2009-01-04
forum: General Help
---

### Post by jlabomb on 2009-01-04
I just noticed my hard drive light is constantly flashing and I can hear the drive working. I have looked up some info about it and I believe it is because my swap partition is not being used. When I check the system monitor it shows the swap at 0. I can not seem to find a fix for this that works, if someone else can help thanks.

Here is my blkid

/dev/sda1: UUID="bebaae0d-fab1-4f2a-a8b5-c0687fc9775f" TYPE="ext3" 
/dev/sda5: UUID="56843930-2e38-4c96-869f-640d4c3450b0" TYPE="swap" 
/dev/sdb1: UUID="aa414d62-6b87-46d3-95b9-85bfde5dbf73" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 


and my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bebaae0d-fab1-4f2a-a8b5-c0687fc9775f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=56843930-2e38-4c96-869f-640d4c3450b0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/dev/sda3 /home ext3 nodev,nosuid,relatime 0 2

---

### Post by adult swim on 2009-01-04
> # /dev/sda5
UUID=56843930-2e38-4c96-869f-640d4c3450b0 none swap sw 0 0
it looks like your swap is set up right.  if anything, you would have hard drive activity from the swap being used, not from a lack of swap.  do you have a tracker or something similar enabled?
EDIT: go to a terminal and run the command ```
top
``` and see which processes are up at the top

---

### Post by jlabomb on 2009-01-04
Well what you said made sense so I thought about the recent changes I had made. I have put in a TV Tuner and installed some myth stuff and upon removing it the light has stopped flashing constantly. Nothing was using much processor but I will paste what I found anyway. Thanks again.


james@james-desktop:~$ top

top - 22:32:05 up 5 min,  2 users,  load average: 0.63, 1.02, 0.51
Tasks: 141 total,   1 running, 140 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.5%us,  0.3%sy,  0.0%ni, 96.9%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   2056068k total,   841044k used,  1215024k free,   121700k buffers
Swap:  6040400k total,        0k used,  6040400k free,   331116k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5817 root      20   0  135m  33m  12m S    3  1.7   0:12.52 Xorg               
 6453 james     20   0  294m  30m  13m S    2  1.5   0:01.12 gnome-terminal     
 5363 root      20   0 56752 1764 1168 S    1  0.1   0:00.02 nmbd               
 6326 james     20   0  259m  34m  16m S    1  1.7   0:05.24 compiz.real        
 6336 james     20   0  302m  25m  14m S    1  1.3   0:03.58 gnome-panel        
 6475 james     20   0 19100 1360  992 R    1  0.1   0:00.88 top                
    1 root      20   0  5232 2024  616 S    0  0.1   0:00.92 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.02 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper

---

