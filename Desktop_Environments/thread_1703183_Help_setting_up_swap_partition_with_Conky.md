---
title: "Help setting up swap partition with Conky"
date: 2011-03-08
forum: Desktop Environments
---

### Post by willhurley82 on 2011-03-08
I used testdisk to undelete some files and in the process accidentally moved my partitions around (swap file was sda5 now it's sda3).  Now I am getting the "no swap%" error from Conky.  This is in Conky, I've already checked the UUID's with my partitions and fstab file.  

My Conky config is linked to a lua file.  I'll post the Conky now, lua after I get a reply.



Conky:

 # Conky settings #
background no
update_interval 1

cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
#imlib_cache_size 0

temperature_unit fahrenheit

# Window specifications #

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

border_inner_margin 0
border_outer_margin 0

minimum_size 200 250
maximum_width 200

alignment tr
gap_x 35
gap_y 55

# Graphics settings #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# Text settings #
use_xft yes
xftfont caviar dreams:size=8
xftalpha 0.5

uppercase no

temperature_unit celsius


default_color FFFFFF

# Lua Load  #
lua_load ~/.lua/scripts/clock_rings.lua
lua_draw_hook_pre clock_rings

TEXT
${voffset 8}${color FF6600}${font caviar dreams:size=16}${time %A}${font}${voffset -8}${alignr 50}${color FFFFFF}${font caviar dreams:size=38}${time %e}${font}
${color FFFFFF}${voffset -30}${color FFFFFF}${font caviar dreams:size=18}${time %b}${font}${voffset -3} ${color FFFFFF}${font caviar dreams:size=20}${time %Y}${font}${color FF6600}${hr}
${voffset 140}${font caviar dreams:size=10}${alignr}HOME${font}
${font caviar dreams:size=12}${color FFFFFF}${alignr}${weather [http://weather.noaa.gov/pub/data/observations/metar/stations/](http://weather.noaa.gov/pub/data/observations/metar/stations/) LQBK temperature temperature 30} °C${font}
${image ~/.conky/new-ubuntu-logo.png -p 64,125 -s 70x20}

${color FFFFFF}${goto 25}${voffset 35}${cpu cpu0}%
${color FF6600}${goto 25}CPU
${color FFFFFF}${goto 50}${voffset 23}${memperc}%
${color FF6600}${goto 50}RAM
${color FFFFFF}${goto 75}${voffset 23}${swapperc}%
${color FF6600}${goto 75}Swap
${color FFFFFF}${goto 100}${voffset 23}${fs_used_perc /}%
${color FF6600}${goto 100}Disk
${color FFFFFF}${goto 125}${voffset 25}${downspeed wlan0}
${color FFFFFF}${goto 125}${upspeed wlan0}
${color FF6600}${goto 125}Net



${color FFFFFF}${font caviar dreams:size=8}Uptime: ${uptime_short}
${color FFFFFF}${font caviar dreams:size=8}Processes: ${processes}
${color FFFFFF}${font caviar dreams:size=8}Running: ${running_processes}


${color FF6600}${font caviar dreams:size=8}${alignr}${nodename}
${color FF6600}${font caviar dreams:size=8}${alignr}${pre_exec cat /etc/issue.net}  $machine
${color FF6600}${font caviar dreams:size=8}${alignr}Kernel: ${kernel}

---

### Post by stinkeye on 2011-03-09
In the terminal run 
```
free
```
to see if your running a swap file.

eg mine
```
glen@MavMusic:~$ free
             total       used       free     shared    buffers     cached
Mem:       2060736    1701184     359552          0      71704     843848
-/+ buffers/cache:     785632    1275104
**Swap:**      3317384          0    3317384
```

My output from **sudo blkid**
```
glen@MavMusic:~$ sudo blkid
/dev/sda1: LABEL="XP" UUID="F0D4A588D4A55220" TYPE="ntfs" 
/dev/sda2: LABEL="Storage" UUID="E0D8480AD847DE02" TYPE="ntfs" 
/dev/sdb1: LABEL="MintDebian" UUID="6c38cfee-00f5-4635-8200-88f5f611760c" TYPE="ext4" 
/dev/sdb3: LABEL="GAMES" UUID="40D0591AD059178C" TYPE="ntfs" 
/dev/sdb4: UUID="09092549-56a6-44c6-bdad-4bf4ea4a5e54" TYPE="swap" 
/dev/sdc5: UUID="95ccf46f-0825-4466-9632-3d46cfd0b2c5" TYPE="swap" 
/dev/sda5: LABEL="UBUP" UUID="9c04ea8b-889a-4b40-989a-dcb51cba0db7" TYPE="ext3" 
/dev/sdc1: UUID="c587d8ad-4f02-4545-aac7-40873bc4f392" TYPE="ext4" 
/dev/sdc3: UUID="7bb1242c-9af5-4a48-ae0d-8f653dc36418" TYPE="ext4"
```
**note: I have 2 Linux installs so is showing 2 swaps.

...and this is my entry in fstab
```
UUID=95ccf46f-0825-4466-9632-3d46cfd0b2c5 none            swap    sw              0       0
```

---

### Post by willhurley82 on 2011-03-09
My UUID's match, but here's what I got from running "free" in terminal:


             total       used       free     shared    buffers     cached
Mem:       2313964    1620460     693504          0     125696     599804
-/+ buffers/cache:     894960    1419004
Swap:            0          0          0



EDIT:  Also, here is my output for blkid:


/dev/sda1: UUID="8A3207C43207B3EB" TYPE="ntfs" 
/dev/sda2: UUID="af920f37-9cf2-48ec-8656-ebf1172faa4f" TYPE="ext4" 
/dev/sda3: UUID="8d74440b-b9d8-4c57-aebf-affd2cc4c4c8" TYPE="swap"

---

### Post by stinkeye on 2011-03-09
Try to reinitialize swap.

 ```
sudo swapoff -a
```
```
sudo mkswap -U 8d74440b-b9d8-4c57-aebf-affd2cc4c4c8 /dev/sda3
```
```
sudo swapon -a
```


Then run 
```
free -m
```
To check for swap.

---

### Post by willhurley82 on 2011-03-09
Ran the commands from terminal, here is the output from free:


             total       used       free     shared    buffers     cached
Mem:          2259       1261        998          0         50        426
-/+ buffers/cache:        784       1475
Swap:            0          0          0



Also, my other thread turned into something similar:

[http://ubuntuforums.org/showthread.php?p=10541306](http://ubuntuforums.org/showthread.php?p=10541306)

---

### Post by stinkeye on 2011-03-09
OK, that's about as much as I can help, sorry.
You'll need someone with a more thorough knowledge of swap.
Try a reboot ?????

---

### Post by dnairb on 2011-03-09
To confirm details (and have all the relevant info on one post), can you post the output of:

sudo cat /etc/fstab

sudo blkid

sudo fdisk -l

sudo cat /etc/initramfs-tools/conf.d/resume

---

### Post by willhurley82 on 2011-03-09
Tried a reboot, no changes to the loss of the "Hibernate" function in shutdown menu or fix with Conky config.  Here are my outputs for those commands.  

cat output:


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=af920f37-9cf2-48ec-8656-ebf1172faa4f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=8d74440b-b9d8-4c57-aebf-affd2cc4c4c8 none            swap    sw              0       0




blkid output:

/dev/sda1: UUID="8A3207C43207B3EB" TYPE="ntfs" 
/dev/sda2: UUID="af920f37-9cf2-48ec-8656-ebf1172faa4f" TYPE="ext4" 
/dev/sda3: UUID="8d74440b-b9d8-4c57-aebf-affd2cc4c4c8" TYPE="swap" 




fdisk output:


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x32d8b890

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8429    67700704+   7  HPFS/NTFS
/dev/sda2            8429       13260    38807552   83  Linux
/dev/sda3           13260       13372      893944   82  Linux swap / Solaris




2nd cat output:


RESUME=UUID=8d74440b-b9d8-4c57-aebf-affd2cc4c4c8

---

### Post by dnairb on 2011-03-09
Thank you.

Your /etc/fstab file has a "#" on the line relating to swap.
This needs to be edited to remove the "#"


#UUID=8d74440b-b9d8-4c57-aebf-affd2cc4c4c8 none swap sw 0 0

should read

UUID=8d74440b-b9d8-4c57-aebf-affd2cc4c4c8 none swap sw 0 0

gksudo gedit /etc/fstab

edit and save.

the fdisk out ouput should have been "fdisk -l" that's dash lower-case "ell"

---

### Post by willhurley82 on 2011-03-09
Edited the fstab file and double checked the out put of "fdisk -l".  Reposting "fdisk -l"


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x32d8b890

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8429    67700704+   7  HPFS/NTFS
/dev/sda2            8429       13260    38807552   83  Linux
/dev/sda3           13260       13372      893944   82  Linux swap / Solaris

---

### Post by dnairb on 2011-03-09
To confirm, please post cat /etc/fstab.

blkid, fstab and /etc/initramfs-tools/conf.d/resume should all show the same UUID for the swap partition.

If all looks good, try a reboot

---

### Post by willhurley82 on 2011-03-09
Okay, I went into gparted after my last post, right-clicked my swap partition, then clicked "swapon".  It turned on, no errors.  It was the inconsistency in the fstab file, which I missed earlier.  Still no "hibernate" function in shutdown though.  That's no biggie, for now.  I have to go to work, so I'll actively troubleshoot that tomorrow morning.  I'm going to leave this thread open for the hibernate issue, unless I need to mark as solved and open a new one.  Just let me know.

Conky is registering swap partition now as well.  

Dave

---

### Post by willhurley82 on 2011-03-09
Had to install hibernate via Synaptic.  Everything appears good now.  I would like to thank everyone for your support.  I'm finding that Linux is much better than Windows.  I opened over 10 different programs to get my RAM usage to skyrocket and neither constant CPU or RAM usage went up over 10% above base.  That's amazing.  And the other thing that's amazing is--YOU--the community that helps others with problems they have.  

:popcorn:

Dave

---

### Post by dnairb on 2011-03-09
Glad you got this sorted.

---

### Post by stinkeye on 2011-03-09
> **dnairb said:**
> Thank you.

Your /etc/fstab file has a "#" on the line relating to swap.
This needs to be edited to remove the "#"


#UUID=8d74440b-b9d8-4c57-aebf-affd2cc4c4c8 none swap sw 0 0

should read

UUID=8d74440b-b9d8-4c57-aebf-affd2cc4c4c8 none swap sw 0 0

gksudo gedit /etc/fstab

edit and save.

the fdisk out ouput should have been "fdisk -l" that's dash lower-case "ell"

Geez, it's always the simplest of things.
Pity I missed that one.
Could have used " I spy with my little stinkeye something beginning with #" :shock:

---

