---
title: "Runs VERY slow, sometimes.."
date: 2010-02-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by SGAShepp on 2010-02-04
Hello, I posted this in Dell section because I dont know where else I would post this. It is a Dell Inspiron 1000 infact.
Everything actually went very well, as far as hardware support and installation, Everything seems to be working.

However, this may seem weird but, every so often. (about every other boot) The system runs VERY slow, everything.. starting up, running apps, Not even usable its so slow, but then I'll restart the system, and boom! its very fast and very usable again.

I am new to this all but this doesn't seem to be right, just every odd boot, the whole thing is unusably slow. yet other times it is perfect. I do have swap space set up correctly.  

What could be the problem? I'll include any needed information at your request. keeping in mind i'm new haha. Thanks for the help!

---

### Post by mimens on 2010-07-10
Hello,    

I have similar problem with Ubuntu...    

I have have Ubuntu 9.10 installed on DELL e6400. Since several months my  computer has been very slow.  Looking at all kinds of forums did not help.  Re-installing it solve the problem for a week a two and after it comes to  the same. Top shows often than the xorg and metacity are using a lot of CPU. I do not have compiz. Every X-application I start is taking 100 % of the cpu. 

My mother board has been change recently - did not help neither. I just run all the hardware tests (which took more than 15h) - nothing, all the tests passed.    

Here are the specifications of my machine: 


** $ls cpu**
Architecture:          i686
CPU(s):                2
Thread(s) per core:    1
Core(s) per socket:    2
CPU socket(s):         1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 23
Stepping:              10
CPU MHz:               800.000
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              6144K

**$ cat /proc/version**
Linux version 2.6.31-22-generic (buildd@vernadsky) (gcc version 4.4.1
(Ubuntu 4.4.1-4ubuntu8) ) #60-Ubuntu SMP Thu May 27 00:22:23 UTC 2010

** $ cat /proc/meminfo**
MemTotal:        3602808 kB
MemFree:         2889004 kB
Buffers:          124672 kB
Cached:           310368 kB
SwapCached:            0 kB
Active:           319796 kB
Inactive:         312624 kB
Active(anon):     204736 kB
Inactive(anon):        8 kB
Active(file):     115060 kB
Inactive(file):   312616 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:       2748732 kB
HighFree:        2218484 kB
LowTotal:         854076 kB
LowFree:          670520 kB
SwapTotal:       9936160 kB
SwapFree:        9936160 kB
Dirty:               208 kB
Writeback:             0 kB
AnonPages:        197380 kB
Mapped:            73500 kB
Slab:              36464 kB
SReclaimable:      23968 kB
SUnreclaim:        12496 kB
PageTables:         4552 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    11737564 kB
Committed_AS:     694008 kB
VmallocTotal:     122880 kB
VmallocUsed:       50920 kB
VmallocChunk:      61428 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       28664 kB
DirectMap4M:      880640 kB

**$ lsmod**
Module                  Size  Used by
binfmt_misc             8356  1
ppdev                   6688  0
bridge                 47952  0
stp                     2272  1 bridge
bnep                   12060  2
vboxnetflt             84840  0
vboxnetadp             78344  0
vboxdrv               121160  1 vboxnetflt
snd_hda_codec_idt      59876  1
snd_hda_intel          27016  2
snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel
joydev                 10240  0
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0
snd_seq_oss            28576  0
snd_seq_midi            6464  0
snd_rawmidi            22176  1 snd_seq_midi
arc4                    1660  2
ecb                     2524  2
iptable_filter          3100  0
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
dell_wmi                2564  0
iwlagn                109084  0
iwlcore               112796  1 iwlagn
mac80211              181140  2 iwlagn,iwlcore
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
uvcvideo               59080  0
snd_seq                50224  6
snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
zaurus                  3676  0
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5
snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cdc_ether               5308  1 zaurus
usbnet                 17188  2 zaurus,cdc_ether
mii                     5212  1 usbnet
cdc_acm                16544  0
cdc_wdm                 9916  0
dell_laptop             8128  0
dcdbas                  7292  1 dell_laptop
ricoh_mmc               3676  0
sdhci_pci               7100  0
sdhci                  17504  1 sdhci_pci
led_class               4096  2 iwlcore,sdhci
psmouse                57332  0
serio_raw               5280  0
btusb                  11856  2
videodev               36736  1 uvcvideo
v4l1_compat            14336  2 uvcvideo,videodev
cfg80211               93052  3 iwlagn,iwlcore,mac80211
snd                    59204  16
snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
nvidia               9586440  30
lp                      8964  0
parport                35340  2 ppdev,lp
ohci1394               29900  0
ieee1394               86596  1 ohci1394
e1000e                121996  0
intel_agp              27676  0
agpgart                34988  2 nvidia,intel_agp
usbhid                 38208  0
video                  19380  0
output                  2780  1 video

** $ df -h**
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             220G  103G  107G  49% /
udev                  1.8G  344K  1.8G   1% /dev
none                  1.8G  304K  1.8G   1% /dev/shm
none                  1.8G   76K  1.8G   1% /var/run
none                  1.8G     0  1.8G   0% /var/lock
none                  1.8G     0  1.8G   0% /lib/init/rw




 I am a novice.. So sorry if I insult somebody not giving the proper information, or too much of it.. I would so much appreciate if somebody helps me with this.. I fight already for months without any success...  Please, please, please, help me! Mia

---

### Post by mimens on 2010-07-19
Hello,

nobodies replied so far so
a) My post is on the wrong place
b) I did not give enough explanations.

I do not know what to do about a).. I never posted anything in a forum before, so I will go for b)

Here is a bit of more diagnostic.. or history of the problem.

When I reinstall my system (now i do it on a regular basis every 1 month or so), it runs ok for about 2 weeks, and after it restarts being slow slow slow. I did not observe that it happens after any particular application installation. Actually I try to keep my computer clean from all fancy apps. After the 'good' two weeks, my laptop will be ok in the first 2-3 hours of the morning, starting to behave badly after that. If I check the cpu temperature, it will show something like 65 C. Not too low, but not too high, neither. From my previous DELL I was used to have more like 42 C (it is obvious why i remember this number), but I read in the web, that unless the cpu is 80-90 C everything should be fine. More, I tried to use fans (you know this plastic desks with fans), but it did not save me.  Every single x-application like firefox, openoffice, will go for 100 % CPU and it becomes impossible to work until the laptop is left halted for 3-4-5 hours.

So now, anybody?

Mimens

---

