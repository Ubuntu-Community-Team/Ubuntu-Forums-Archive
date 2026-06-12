---
title: "Ubuntu 8.04 runs super slow.."
date: 2009-01-28
forum: General Help
---

### Post by Maikis on 2009-01-28
I basicly tried everything.. First i had ubuntu 8.10 thought it was slow, now using 8.04 and its exactly the same.. My pc isn't weak at all, windows ran perfect on this computer.. I don't use compiz , also tried that "blocking Ipv6" i found on google..


Memory: 1019mb
Processor: intel pentium 4 CPU 2.4ghz
Graphic card: ATI Technologies Inc R350 AH [Radeon 9800]

Every suggestion is welcome...

Thanks!

---

### Post by Tamlynmac on 2009-01-28
> Maikis
Graphic card: ATI Technologies Inc R350 AH [Radeon 9800]

Which video driver are you using for your ATI card? If your still in 8.04, you may wish to check Envy and install the best driver. That solved many a speed problem with ATI & NVIDIA cards.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I also wonder, what's running after startup and how much CPU & memory is being used?

system/administration/system monitor

On the Resources Tab - what's your CPU & memory usage?

On the Processes Tab - What is running that may be using excessive amounts of either CPU or memory?

---

### Post by Maikis on 2009-01-29
> **Tamlynmac said:**
> Which video driver are you using for your ATI card? If your still in 8.04, you may wish to check Envy and install the best driver. That solved many a speed problem with ATI & NVIDIA cards.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I also wonder, what's running after startup and how much CPU & memory is being used?

system/administration/system monitor

On the Resources Tab - what's your CPU & memory usage?

On the Processes Tab - What is running that may be using excessive amounts of either CPU or memory?
Thanks for your reply..

I already had envy installed. And that didn't made any diffrence.

My CPU is peaking from 20% -> 50% , my memory is on 27.8%..
Those other 3 stats (don't know the name in english) are: 0.33 0.51 0.30

Thanks.

---

### Post by Tamlynmac on 2009-01-29
Is your CPU peaking while ide? If so:

system/administration/system monitor
On the** Processes Tab** - What is running, that may be using excessive amounts of either CPU or memory.

If your CPU is peaking between 20% - 50% in idle, a process is using a significant amount of your recourses. Look under the %CPU column & Process Name column to identify.

---

### Post by Maikis on 2009-01-29
10% on an idle. The only > 0% i saw was the Gnome-System monitor.. Nothing else had higher cpu then 0%..

---

### Post by jimmah6786 on 2009-01-29
> **Maikis said:**
> 10% on an idle. The only > 0% i saw was the Gnome-System monitor.. Nothing else had higher cpu then 0%..

I noticed that your RAM was 1019MB not 1024, does this mean that your graphics card is sharing? If so maybe allow it to share at least 32MB, see if your desktop-effects is turned on and only has 5MB to work with.

When you installed Ubuntu did you make a SWAP size of around the same size as your RAM? There could be some paging/swaping going on...

Try these commands and let us know the outputs:
```
free -mt
```
Shows us physical memory
```
df -Th
```
Show us logical memory
```
top
```
shows us CPU utilization
```
wmstat
```
Shows us Virtual Memory/Paging/SWAP information


Remember mb = megabits, MB = megabytes(8 megabits)

---

### Post by Maikis on 2009-01-29
Thank you for your reply. Here are all the outputs:

```

maikel@maikel-desktop:~$ free -mt
             total       used       free     shared    buffers     cached
Mem:          1010        818        192          0         53        377
-/+ buffers/cache:        386        624
Swap:         2957          0       2957
Total:        3968        818       3150
maikel@maikel-desktop:~$ df -Th
Bestandssystm-type    Grtte   Gebr Besch Geb% Aangekoppeld op
/dev/sdb1     ext3     72G  6,1G   62G  10% /
varrun       tmpfs    506M  104K  506M   1% /var/run
varlock      tmpfs    506M     0  506M   0% /var/lock
udev         tmpfs    506M   68K  506M   1% /dev
devshm       tmpfs    506M   48K  506M   1% /dev/shm
lrm          tmpfs    506M   38M  468M   8% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon
fuse.gvfs-fuse-daemon     72G  6,1G   62G  10% /home/maikel/.gvfs
/dev/sdc1     vfat    252M  146M  106M  58% /media/disk
maikel@maikel-desktop:~$ top

top - 21:52:26 up  4:05,  3 users,  load average: 0.24, 0.21, 0.19
Tasks: 115 total,   2 running, 112 sleeping,   0 stopped,   1 zombie
Cpu(s):  1.0%us,  0.3%sy,  0.0%ni, 98.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1035116k total,   838132k used,   196984k free,    54792k buffers
Swap:  3028212k total,        0k used,  3028212k free,   387160k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5158 root      20   0  238m  77m  11m S  1.3  7.7   9:25.73 Xorg               
 8070 maikel    20   0 21792  14m 5728 S  0.7  1.4   0:18.84 compiz.real        
 9589 maikel    20   0 78404  20m  11m R  0.7  2.0   0:00.48 gnome-terminal     
    1 root      20   0  2844 1688  544 S  0.0  0.2   0:01.30 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.16 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 kblockd/0          
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  121 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  155 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
  156 root      20   0     0    0    0 S  0.0  0.0   0:00.24 pdflush            
  157 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kswapd0   

```

---

### Post by jimmah6786 on 2009-01-30
Try Turning off Desktop-Effects. Let me know if that improves the performance at all.
-Jim

---

### Post by Maikis on 2009-01-31
> **jimmah6786 said:**
> Try Turning off Desktop-Effects. Let me know if that improves the performance at all.
-Jim

Makes no diffrence removing compiz / ...

---

### Post by jimmah6786 on 2009-02-03
Are you aware of the 3 users using your computer? Are you logged in as root or maikel? You are not using any of your SWAP so that is good, no paging going on.

Lets try to disable some processes that are not needed. System --> Preferences --> Session  see if there is anything  you do not need, such as Bluetooth or Evolution alarm(for now), etc...

**Any one else going to help Maikis out??**

---

