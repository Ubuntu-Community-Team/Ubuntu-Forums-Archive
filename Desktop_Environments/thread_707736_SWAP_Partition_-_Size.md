---
title: "SWAP Partition - Size"
date: 2008-02-25
forum: Desktop Environments
---

### Post by Geffers on 2008-02-25
I am running Gutsy on two older machines.

One is an AMD 350Mhz K6 with 384MB RAM

My Fstab shows SWAP as follows;

# /dev/hda3
UUID=9b306afe-a729-41e9-b53a-ac3a08160531 none    swap    sw              0       0
# /dev/hda5
UUID=5c56b7f0-d2de-4ede-a049-27e05c8c7422 none     swap    sw              0       0

These are 760MB in a logical partition and 
972MB in a primary partition.

I think I ended up with 2 SWAPs due to a second installation and I didn't knowingly choose between a Logical and Primary.

I have 1.5GB space left on my Linux partition but on occasions this machine virtually grinds to a halt.

I mainly use this machine for email, newsgroups, web browsing and as a print server so it is not heavy usage but before confining it to the recycle centre I want to eliminate some possibilities.

Is my SWAP set up ideal, I've not much idea whether this is good or bad.

Also, I don't often have too many programs running at the same time but is there a way to check memory and free up if required?

Geffers

---

### Post by bernied on 2008-02-25
A couple of thoughts...

Two swaps on separate partitions on the same disk is not very efficient - if it is swapping a lot, then it will skip between these two partitions a lot. So if they are physically far apart, that's lots of travel for the heads (if that makes any sense). Better to have one larger one, or better still is two on different disks.

I've read that you should:
- put the swap in the middle of the disk to minimise average distance travelled to get there
- put the swap on the outside edge of the disk because it spins faster - but I've no idea how this translates, is it the beginning, or the end?
- not have more than double your RAM as swap

If you are running standard ubuntu, you'd probably benefit most from using a much more lightweight install - like xubuntu which uses xfce instead of gnome desktop. There are also many lightweight window managers out there.

Some terminal commands that might give more insight:
```
top
```If you use '>' while it's running, it will sort by memory usage instead of cpu usage. (Hit 'q' to quit.)
```
cat /proc/swaps
```
```
cat /proc/meminfo
```Post results here if you need help interpreting.

---

### Post by Geffers on 2008-02-26
> **bernied said:**
> A couple of thoughts...

If you are running standard ubuntu, you'd probably benefit most from using a much more lightweight install - like xubuntu which uses xfce instead of gnome desktop. There are also many lightweight window managers out there.

Some terminal commands that might give more insight:
```
top
```If you use '>' while it's running, it will sort by memory usage instead of cpu usage. (Hit 'q' to quit.)
```
cat /proc/swaps
```
```
cat /proc/meminfo
```Post results here if you need help interpreting.

Tried Xubuntu on another machine and quite impressed, just ended up putting similar setups on two machines when I upgraded from Feisty to Gutsy.

Interesting terminal commands, here is the output;

geoff@challenger:~$ top

top - 17:02:19 up 32 min,  3 users,  load average: 0.80, 1.29, 1.63
Tasks: 109 total,   3 running, 106 sleeping,   0 stopped,   0 zombie
Cpu(s): 86.0%us, 11.6%sy,  0.0%ni,  2.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    320768k total,   284360k used,    36408k free,    20304k buffers
Swap:  1775100k total,   140204k used,  1634896k free,   115660k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6128 geoff     15   0  157m  48m  19m S  4.6 15.3   2:57.37 firefox-bin        
 5105 root      16   0  102m  24m 5376 R 50.8  7.9   6:04.49 Xorg               
 5435 geoff     18   0 67940  22m  11m S  0.0  7.0   0:11.31 deskbar-applet     
 6889 geoff     15   0 39336  18m  14m S 25.4  6.0   2:49.35 gnome-system-mo    
 5912 geoff     16   0 68952  16m 9452 R  2.3  5.2   0:11.10 gnome-terminal     
 5321 geoff     18   0 49056  15m  10m S  0.0  5.1   0:38.35 gnome-panel        
 5325 geoff     18   0 77532  11m  10m S  0.0  3.7   0:06.84 nautilus           
 5432 geoff     15   0 42496  10m 8544 S  0.0  3.5   0:01.65 mixer_applet2      
 5367 geoff     18   0 33536  10m 9668 S  0.0  3.4   0:01.92 update-notifier    
 5460 geoff     15   0 59432  10m 8164 S  0.0  3.4   0:18.71 python             
 6013 geoff     15   0 29312  10m 7324 S  0.0  3.3   0:02.04 notification-da    
 5429 geoff     15   0 32548 9768 8304 S  0.0  3.0   0:01.09 fast-user-switc    
 5319 geoff     15   0 18452 9504 7384 S  0.0  3.0   0:50.56 metacity           
 5937 geoff     18   0 60072 9196 6888 S  0.0  2.9   0:16.12 python             
 5390 geoff     15   0 40008 8316 7660 S  0.0  2.6   0:01.52 nm-applet          
 5364 geoff     15   0 71332 7748 7184 S  0.0  2.4   0:00.86 trashapplet        
 5300 geoff     25   0 38988 7288 6844 S  0.0  2.3   0:03.37 gnome-settings-    
geoff@challenger:~$ cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/hda3                               partition       996020  140204  -1
/dev/hda5                               partition       779080  0       -2
geoff@challenger:~$ cat /proc/meminfo
MemTotal:       320768 kB
MemFree:         37924 kB
Buffers:         20360 kB
Cached:         115924 kB
SwapCached:      30436 kB
Active:         188900 kB
Inactive:        69668 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       320768 kB
LowFree:         37924 kB
SwapTotal:     1775100 kB
SwapFree:      1634896 kB
Dirty:              56 kB
Writeback:           0 kB
AnonPages:      104164 kB
Mapped:          44048 kB
Slab:            14704 kB
SReclaimable:     7316 kB
SUnreclaim:       7388 kB
PageTables:       2184 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   1935484 kB
Committed_AS:   630476 kB
VmallocTotal:   704504 kB
VmallocUsed:      4384 kB
VmallocChunk:   699996 kB
geoff@challenger:~$ 

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

It does look as though memory is being used up, I only had the HPLIP Toolbox and Xsane running as well as a command window to get these readings and Firefox to post the message.

Geffers

---

### Post by bernied on 2008-02-26
If you do want to try xubuntu on that machine, you don't have to reinstall. If disk space is not a real issue then you can just install the xubuntu-desktop package, then restart X (logout and Ctrl-Alt-Backspace), then choose xfce from the login sessions menu. You will still have your gnome, but xfce might run a little faster. You can see from the top output that those gnome apps are a bit hungry. Between them,  deskbar-applet, gnome-system-mo, gnome-terminal, gnome-panel, and nautilus are using about 30% of your RAM.

Also note from this:> geoff@challenger:~$ cat /proc/swaps
Filename Type Size Used Priority
/dev/hda3 partition 996020 140204 -1
/dev/hda5 partition 779080 0 -2that only the larger swap partition (hda3) was being used.

---

### Post by Geffers on 2008-02-26
> **bernied said:**
> If you do want to try xubuntu on that machine, you don't have to reinstall. If disk space is not a real issue then you can just install the xubuntu-desktop package, then restart X (logout and Ctrl-Alt-Backspace), then choose xfce from the login sessions menu. You will still have your gnome, but xfce might run a little faster. You can see from the top output that those gnome apps are a bit hungry. Between them,  deskbar-applet, gnome-system-mo, gnome-terminal, gnome-panel, and nautilus are using about 30% of your RAM.

Also note from this:that only the larger swap partition (hda3) was being used.

Thanks, I'll try the xfce desktop.

Re my second swap not being used, how would I disable it or does it matter as it is not being used.

Geffers

---

### Post by bernied on 2008-02-27
> **Geffers said:**
> Re my second swap not being used, how would I disable it ... 
Just comment out the entry in the /etc/fstab file, like this:
```
# /dev/hda5
# UUID=5c56b7f0-d2de-4ede-a049-27e05c8c7422 none swap sw 0 0
```This wil only take effect next time you reboot, to stop using it immediately you can:
```
$ sudo swapoff /dev/hda5
```
> **Geffers said:**
> .. or does it matter as it is not being used.It probably doesn't matter, it is set as having a lower priority, and the first swap partition is very large compared to your RAM, so the second one will probably never get used.

---

### Post by Geffers on 2008-02-28
> **bernied said:**
> Just comment out the entry in the /etc/fstab file, like this:
```
# /dev/hda5
# UUID=5c56b7f0-d2de-4ede-a049-27e05c8c7422 none swap sw 0 0
```This wil only take effect next time you reboot, to stop using it immediately you can:
```
$ sudo swapoff /dev/hda5
```
It probably doesn't matter, it is set as having a lower priority, and the first swap partition is very large compared to your RAM, so the second one will probably never get used.

Thanks.

Geffers

---

