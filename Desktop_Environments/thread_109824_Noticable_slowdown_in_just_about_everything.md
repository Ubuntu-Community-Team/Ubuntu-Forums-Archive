---
title: "Noticable slowdown in just about everything"
date: 2005-12-29
forum: Desktop Environments
---

### Post by chimera on 2005-12-29
I recently noticed my system has gotten a lot slower(recently as in the last few hours); most of the applications (nautilus, firefox, openoffice, gnome system monitor to name a few) take about 2 times longer to start than they did before, and when I click a nemu button it takes atleast a second to open. Also, pages in firefox are loading as if I was on dialup.

I HATE (insert whatever is causing all these problems here)!!!!!!!!11

So...yeah, I could use some help, I'm completely clueless about what went wrong.

---

### Post by GeneralZod on 2005-12-29
Run

```

top

```

from the command-line and see if any process(es) are hogging your CPU.

The "X.X% id" (percentage of CPU that is not being used) entry should have a relatively high percentage if you are not doing anything.

---

### Post by chimera on 2005-12-29
I'm running Folding@Home, which takes up all the free CPU cycles, but I've been running it before this started.

---

### Post by chimera on 2005-12-29
bump

---

### Post by chimera on 2005-12-29
Another thing I noticed, I only get around 200FPS in glxgears, I used to get around 6000 before.

---

### Post by GeneralZod on 2005-12-29
[QUOTE=chimera]Another thing I noticed, I only get around 200FPS in glxgears, I used to get around 6000 before.[/QUOTE]

Were you running f@h when you got 6000? glxgears also runs at a low priority, so running it with f@h slows it down.

---

### Post by chimera on 2005-12-29
I tried turning off F@H and running glxgears, and I got 6000+ again, but everything else is still ssssslllllooooowwwww:(

---

### Post by Zwack on 2005-12-29
Stupid questions...

What does top say the top processes are?

What is your uptime?

What is the output from free?  Do you have any free memory, are you using a large portion of your swap space?

Do you notice lots of disk activity?

Z.

---

### Post by varunus on 2005-12-29
Strangely, I had this problem happen once after a reboot.  Everything just seemed so much slower, and top revealed nothing.  I rebooted, and this time tried a different kernel (386 instead of 686); the problem was solved.  I never found out what the issue was; there was an update to the 686 kernel, and after i updated, the problem was solved.  Maybe you should try reinstalling all the linux-image packages you have installed in synaptic?

---

### Post by chimera on 2005-12-29
[QUOTE=varunus]Strangely, I had this problem happen once after a reboot.  Everything just seemed so much slower, and top revealed nothing.  I rebooted, and this time tried a different kernel (386 instead of 686); the problem was solved.  I never found out what the issue was; there was an update to the 686 kernel, and after i updated, the problem was solved.  Maybe you should try reinstalling all the linux-image packages you have installed in synaptic?[/QUOTE]

I haven't installed any other kernels besides that update I got the first time I booted in Ubuntu.


Zwack:
top:
Fahcore_82.exe (99,3%) (this only takes up FREE cpu cycles, so it doesn't have any effect of the performance)
Xorg(0.4%)
gnome-terminal(0.3%)

uptime: 01:07:56 up 2 days,  4:51,  4 users,  load average: 1.06, 1.11, 1.05
(it's been up for weeks without anything slowing down before)

free:

             total       used       free     shared    buffers     cached
Mem:       1035888     997376      38512          0     127992     617340
-/+ buffers/cache:     252044     783844
Swap:      2473968      12544    2461424

disk activity: not much, I have a very quiet case and I can only hear the disk when I'm copying/moving something large.

---

### Post by Zwack on 2005-12-29
[QUOTE=chimera]

Zwack:
top:
Fahcore_82.exe (99,3%) (this only takes up FREE cpu cycles, so it doesn't have any effect of the performance)
Xorg(0.4%)
gnome-terminal(0.3%)

uptime: 01:07:56 up 2 days,  4:51,  4 users,  load average: 1.06, 1.11, 1.05
(it's been up for weeks without anything slowing down before)

free:

             total       used       free     shared    buffers     cached
Mem:       1035888     997376      38512          0     127992     617340
-/+ buffers/cache:     252044     783844
Swap:      2473968      12544    2461424

disk activity: not much, I have a very quiet case and I can only hear the disk when I'm copying/moving something large.[/QUOTE]

As far as performance goes you have three things to worry about... CPU, Disk and Memory.

OK so it's got free memory, and it's probably not I/O wait as you don't think the disks are busy...

There are  a couple of pointers there though...  Your load average is over 1 and I'm assuming that you have a single CPU...  A load average of over 1 means that you are pushing your computer harder than it can actually handle. 

Ideally this should read 1.0 1.0 1.0 which means that your computer is perfectly sized...  The fact that it isn't implies that you are trying to push it harder than you can.

As a comparison I see the following...
```
 20:17:22 up 3 days, 11:11,  1 user,  load average: 0.09, 0.10, 0.10
```

The fact that Folding at home is taking up 99.3% of your CPU cycles makes me think that this is your culprit.

I would like to call BS on the "only takes up FREE cycles" though.

In order to know that your machine is genuinely idle this would have to pop into memory, check what was going on and pop out again.  I suspect it's just running with a very low priority.  Even low priority programs get CPU time.  Worse the computer has to switch between runnable processes.  This is called Context switching as it takes all of the information for the program back onto the CPU after saving all of the old information.

How about posting the output of vmstat 5 5

It should look something like this...
```

~$ vmstat 5 5
procs -----------memory---------- ---swap-- -----io---- --system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in    cs us sy id wa
 0  0  12532   8552  25344 247436    0    0    64    26  112    28  6  0 93  1
 0  0  12532   7932  25348 248028    0    0   118    17 1183   282  1  0 98  0
 0  0  12532   7684  25360 248384    0    0    72     6 1150   264  1  1 98  1
 0  0  12532   6692  25364 249288    0    0   181     6 1198   317  2  0 98  0
 0  0  12532   5948  25364 250092    0    0   161    10 1234   419  2  0 98  0

```

Note that the column that says CPU id is in the 90s and I've still got 200-400 Context switches every five seconds.

Then try stopping folding at home and running vmstat 5 5 again and posting that.

Z.

---

### Post by chimera on 2005-12-30
before stopping it:

procs -----------memory---------- ---swap-- -----io---- --system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in    cs us sy id wa
 4  0  12544  41728 239848 409492    0    0    16    42  175     4 91  2  7  0
 1  0  12544  41720 239852 409492    0    0     0    37 1129   955 99  1  0  0
 1  0  12544  41720 239860 409492    0    0     0     6 1086   854 98  2  0  0
 1  0  12544  41720 239864 409492    0    0     0    10 1087   855 99  1  0  0
 1  0  12544  41720 239872 409492    0    0     0    14 1157   997 99  1  0  0

after stopping it:

chimera@HOMEPC:~$ vmstat 5 5
```
chimera@HOMEPC:~$ vmstat 5 5
procs -----------memory---------- ---swap-- -----io---- --system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in    cs us sy id wa
 2  0  12544  44156 239928 409520    0    0    16    42  175     5 91  2  7  0
 0  0  12544  44164 239932 409520    0    0     0    41 1099   879  0  1 99  0
 0  0  12544  44164 239936 409520    0    0     0   114 1105   880  0  1 99  0
 0  0  12544  44164 239940 409520    0    0     0    10 1103   892  1  1 98  0
 0  0  12544  44164 239948 409520    0    0     0    10 1091   878  0  1 99  0

```

---

### Post by chimera on 2005-12-30
Oh and btw, everything is just as slow even after I've killed Folding@Home.

---

### Post by chimera on 2005-12-30
Today I opened my case to clean it, and I noticed there is infact more disk activity than I expected(I didn't hear it before because of the case I guess), I could hear the disk work when I opened firefox, and when pages were loading, as well as just at random times, even if I'm not doing anything. Is that normal?(abd yes, I've turned off F@H for now)

---

### Post by Zwack on 2005-12-30
[QUOTE=chimera]before stopping it:

```
procs -----------memory---------- ---swap-- -----io---- --system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in    cs us sy id wa
 4  0  12544  41728 239848 409492    0    0    16    42  175     4 91  2  7  0
 1  0  12544  41720 239852 409492    0    0     0    37 1129   955 99  1  0  0
 1  0  12544  41720 239860 409492    0    0     0     6 1086   854 98  2  0  0
 1  0  12544  41720 239864 409492    0    0     0    10 1087   855 99  1  0  0
 1  0  12544  41720 239872 409492    0    0     0    14 1157   997 99  1  0  0
```

after stopping it:

chimera@HOMEPC:~$ vmstat 5 5
```
chimera@HOMEPC:~$ vmstat 5 5
procs -----------memory---------- ---swap-- -----io---- --system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in    cs us sy id wa
 2  0  12544  44156 239928 409520    0    0    16    42  175     5 91  2  7  0
 0  0  12544  44164 239932 409520    0    0     0    41 1099   879  0  1 99  0
 0  0  12544  44164 239936 409520    0    0     0   114 1105   880  0  1 99  0
 0  0  12544  44164 239940 409520    0    0     0    10 1103   892  1  1 98  0
 0  0  12544  44164 239948 409520    0    0     0    10 1091   878  0  1 99  0

```[/QUOTE]

Thanks for the info... You can see that you're going from 0 Idle to 98/99% idle... what we expected to see.  The run queue (first column has dropped to 0).  You don't appear to be swapping before or after...  The column that confuses me is the bo.  I would expect to see that drop to close to 0.  On my system running firefox and vmstat I see it at between 5 and 14.  On your system the first two real entries (the top line is cumulative since boot) we see 41 and 114.  Something is causing I/O.  Have you started any additional services recently?  Installed any new software or upgraded any old software? I don't like saying this, but does a reboot fix the slowness?

Do you have sar installed?  If so does sar -D give any clues as to wht is busy?

What does top show as the busiest process now?

I hope that this helps,
Z.

---

### Post by chimera on 2005-12-30
Top now shows xorg, firefox and gnome-terminal.

I don't even know what sar is.

I'll try rebooting now and see how it works.

---

### Post by chimera on 2005-12-30
Well, I rebooted and it didn't fix anything.

---

### Post by Zwack on 2005-12-30
sar (atsar is available on Synaptic) is a system resource monitoring tool.  

Once it's installed it can give general performance information... Disk usage, CPU, memory usage...

I must admit that so far I can't see any reason for your system to seem slower suddenly.

Have you checked for rootkits?  That might be a good next step.

Z.

---

### Post by chimera on 2005-12-30
What's a rootkit?

(I'm really new to all of this)

---

### Post by nbcthreat on 2005-12-30
Chimera, what does hdparm say?

```
sudo hdparm -i /dev/hda
```

Also, try running folding with nice. That's helped me get a more responsive system while folding.

```
nice ./FAH5*
```

---

### Post by nbcthreat on 2005-12-30
Also, do a system update. There was a kernel update recently. When we're bugshooting, it's good to make sure you've got the most up-to-date system so we're not catching bugs that have already been squashed.

---

### Post by chimera on 2005-12-30
chimera@HOMEPC:~$ sudo hdparm -i /dev/hda

/dev/hda:

 Model=Maxtor 6L300R0, FwRev=BAH41E00, SerialNo=L6048DCH
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=16384kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma6
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: (null):

 * signifies the current active mode



about the rootkits, I did some googling and I sort of got the idea what it's all about. I installed chkrootkit and it didn't find anything. As for the update, I already have it.

---

### Post by robertobaggio2k on 2005-12-30
i have the same problem my system seems to be really slow the last couple of days....the usual things i have runnign r firefox gaim, music and amsn at times, n in the background a gdesklet for hd space, when i boot the computer runs fine after abit using it it starts lagging so bad that i cant even move the mouse cursor and the red light on the pc goes insane...wat should i do?

---

### Post by chimera on 2005-12-30
you shoudl start a new thread, because if you read my post more carefully, I don't have any mouse lag or anything similar;)

---

### Post by Zwack on 2005-12-30
Greetings Chimera,

Based on the vmstat results without Folding at home running I can't see any CPU or memory issues...

That leaves I/O, but your disk looks like it should be o.k. to me...

sar would help confirm that.

I asked about rootkits because if one is installed then your machine would be doing extra (possibly hidden) work and that could explain the slow down.

Can you try one last set of commands before I give up?

try

sync ; sync ; sync ; vmstat 5 5

And see if the bo column remains in low numbers (under 15) 

My work system shows 6 2 2 10 (I moved the mouse on the last one) for the last four sets.

If that is low then I don't see anything wrong.  I understand you have a perception that it is running slow even with Folding at home turned off.  Unfortunately we don't have any symptoms to work with.

The output of 
cat /proc/cpuinfo
might also help (I know bogomips isn't a real number but it might give us a clue).

BTW Robertobaggio it sounds like you are swapping.  I would check memory usage if I were you. 

Z.

---

### Post by robertobaggio2k on 2005-12-30
sorry to join ur thread dude....and i checked my memory usage and its pretty high when i do free -m it shows like 250 n used 246....dat means its just a ram problem? its kinda weird cuz this never happened the first days after installation

---

### Post by Zwack on 2005-12-30
More importantly try vmstat 5 5

If the swap columns (si and so) are above 0 then you are swapping.  That means you don't have enough memory for what you are doing.  My guess is that when you first started you were doing less and now you're using more memory (bigger buddy lists maybe?)... If it's swapping badly you need more memory. 

top 
and then
O
and then
N
 should list your processes by memory usage.

I see X.org at around 25%, firefox at 17% and everything else less than 5%.

If you see something else at the top of that list you might want to see what you can do to reduce it's memory usage.

Z.

---

### Post by robertobaggio2k on 2005-12-30
this is what i got with vmstat 5 5
> umberto@ubuntu:~$ vmstat 5 5
procs -----------memory---------- ---swap-- -----io---- --system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in    cs us sy id wa
 2  0 353596   5148   2036  38780   35  181   185   208 1154   823  9  2 82  6
 0  0 353592   4936   2044  38780    0    0     0    62 1193   927  9  1 90  0
 0  0 353592   5024   2052  38780    0    0     0     6 1104   685  2  1 97  0
 1  0 353592   3660   2060  38780    0    0     0     3 1092   594  6  1 93  0
 0  0 355144   4008   2068  38732    6  311     6   321 1156   724  8  1 80 12


---

### Post by Zwack on 2005-12-30
[QUOTE=robertobaggio2k]this is what i got with vmstat 5 5[/QUOTE]

The last line shows you swapping quite heavily...

311 pages swapped out and 6 swapped in.

You're using a fair bit of virtual memory (the swpd column) but you have some free.

I would seriously look at what processes are using memory using top

type 
top
then when the screen appears press O and then N and enter

It will list processes by memory usage.

How much memory do you have?

Z.

---

### Post by chimera on 2005-12-30
[QUOTE=Zwack]Greetings Chimera,

Based on the vmstat results without Folding at home running I can't see any CPU or memory issues...

That leaves I/O, but your disk looks like it should be o.k. to me...

sar would help confirm that.

I asked about rootkits because if one is installed then your machine would be doing extra (possibly hidden) work and that could explain the slow down.

Can you try one last set of commands before I give up?

try

sync ; sync ; sync ; vmstat 5 5

And see if the bo column remains in low numbers (under 15) 

My work system shows 6 2 2 10 (I moved the mouse on the last one) for the last four sets.

If that is low then I don't see anything wrong.  I understand you have a perception that it is running slow even with Folding at home turned off.  Unfortunately we don't have any symptoms to work with.

The output of 
cat /proc/cpuinfo
might also help (I know bogomips isn't a real number but it might give us a clue).

BTW Robertobaggio it sounds like you are swapping.  I would check memory usage if I were you. 

Z.[/QUOTE]

```

chimera@HOMEPC:~$ sync
chimera@HOMEPC:~$ sync
chimera@HOMEPC:~$ sync
chimera@HOMEPC:~$ vmstat 5 5
procs -----------memory---------- ---swap-- -----io---- --system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in    cs us sy id wa
 0  0   8640 301876  69640 463420    0    0    35    29 1187   579 21  5 73  1
 0  0   8640 301876  69656 463420    0    0     0    16 1140   440  0  1 99  0
 0  0   8640 301876  69672 463424    0    0     0    14 1287   789  7  2 91  0
 0  0   8640 301736  69692 463548    0    0    10    62 1259   830 28  2 69  1
 0  0   8640 301612  69712 463548    0    0     0    39 1103   421  5  1 93  0
chimera@HOMEPC:~$

```

```

chimera@HOMEPC:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping        : 1
cpu MHz         : 3842.030
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pni monitor ds_cpl cid xtpr
bogomips        : 7618.56

```

---

### Post by Zwack on 2005-12-30
Comparing the ratio of clock speed to bogomips on your system to that on mine (2.8GHz not overclocked) I get almost the same value (to within 1 10,000th) so your processor seems to be running fine.

You've stated that when you're not running folding at home you get the same glxgears results that you used to, you're not having any memory issues, your system seems to be outputting a bit more than mine, but I don't know that that is an issue.  Your system is idle most of the time (when not running Folding at home) and you're not getting any mouse lag.

What actual symptoms are you seeing?  You have a perception that it is running slower but I can't see a reason why...  Is there anything other than a perception that you can point to?

Are any of the log files growing inordinately?  look in /var/log...

Anyone got any good ideas?

Z.

---

### Post by chimera on 2005-12-30
As I said, internet pages take longer to load, firefox and nautilus take longer to start, 3d games take longer to start(although framerates are almost the same as they were before once it's done loading)

---

### Post by Zwack on 2005-12-30
Games taking longer to start and apps taking longer to load sounds like disk contention.

Go into synaptic and install atsar (It might be in Universal)...

Then later on run sar -D and have a look to see which disk partitions are busiest and how busy they are.  I can't find anything I can specifically point to at the moment though.  

It sounds like something is running in the background running through your hard drive.

Z.

---

### Post by chimera on 2005-12-30
```

chimera@HOMEPC:~$ sar -D
open /var/log/atsar/atsa31: No such file or directory
chimera@HOMEPC:~$ sar
open /var/log/atsar/atsa31: No such file or directory
chimera@HOMEPC:~$

```

I installed the atsat package in synaptic...

---

### Post by Omnios on 2005-12-30
This may help a little in that this has been observe red on a lot of machines and even the dreaded winXP. If you leave your computer running for a long period of time as a desktop it will slow down. If I remember correctly it has something to do with memory caching and possibly memory leaks piling up. I have noticed the same thing when I leave my computer running for days without a reboot the reboot solves the problem by cleaning out the caching now if only we has a easy button for that lol.

---

### Post by Zwack on 2005-12-31
Chimera, Check that you have a directory /var/log/atsar and wait a few hours and try again.  Sar doesn't write immediatley, it does it every ten minutes...

Hopefully we'll be able to get a bit of information from it.

Z.

---

