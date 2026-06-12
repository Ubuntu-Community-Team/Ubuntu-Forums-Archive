---
title: "How to make Ubuntu 17.10 faster?"
date: 2017-11-19
forum: Desktop Environments
---

### Post by favetella on 2017-11-19
Hi to all,

I'm an Ubuntu user since 2006. I've been installing all the new releases (and always from scratch in order to avoid surprises).
However, for some reasons I've been stuck to Ubuntu 16.04 and recently I installed 17.10 from scratch, but I did got some bad surprises.

[LIST=1]
[*]the system seems to be quite heavier sometimes; 
[*]despite at the beginning the RAM consumption is acceptable, it happens that as much as I use the system, the various softwares may hang and all the installed RAM is consumed; 
[*]I found no preinstalled tool to set the system up and disable unnecessary services or graphic effects; 
[*]Thunderbird is no more working properly with yahoo account (IMAP is ok, but SMTP fails). Maybe it's not Ubuntu related, but it happens now with Ubuntu 17.10 and it did not happened till few days ago till I've been using Ubuntu 16.04 
[/LIST]
A first consideration I may do is that sadly my laptop is getting too old for Ubuntu (see attached HardInfo report). Actually I'm not sure it is too old (at least I do hope so) since I do think there's something that can be adjusted to make it work fine as always. I mean, during my typical working day I have running at the same time:

[LIST]
[*]Thudnerbird 
[*]2 LibreOffice Writer documents 
[*]Firefox with 10 or 15 open tabs 
[*]sometime I may use Gimp to make some very basic image manipulation and close Gimp as soon as I just finish them 
[/LIST]

Now that I'm writing the RAM consumption is at above 90% of 2.9GB since I've been opening all the softwares as described above. Maybe it's just the normal consumption of the current version of all those softwares, despite I do think there's something wrong since the system may hang even when using Writer with just one document open (is that Ubuntu or LibreOffice related?!?).

So, after all such premises, what I hope I could do is trying to make the system lighter. I propose the following steps and hope you could help me with those or maybe you may want to suggest something different:
[LIST=1]
[*]disable any visual desktop effect (how to do that?) 
[*]run a command to flush RAM (how to do that)? 
[*]eventually choose a lighter version of all the kind of software I'm currently using (graphic manager, browser, office suite, email client, ...) 
[/LIST]

Thank you so much for your support.
Regards.

PD: something I've never understood is why I have 4GB installed RAM and actually less than 3GB (exactly 2.9GB are available). The graphic card may occupy some RAM, but how to really be sure about that?

---

### Post by vasa1 on 2017-11-19
If you don't have *inxi* installed, please install it from the software center or by using *apt-get*. If it isn't available you may need to enable the Universe repository first and then update your system). After that, run```
inxi -Fxzc0
```and post the output here. The output may help people guide you better.

The pdf file is a bit too much information but it does show your system is accessing swap.

You could also run```
top -n 1 -o %MEM
```and post that output here.

You mentioned having LibreOffice Writer open. Do you find things more responsive if you close it?

---

### Post by favetella on 2017-11-21
Hi, thanks for your reply. Here you are:

```
inxi -Fxzc0
System:    Host: mano Kernel: 4.13.0-17-generic x86_64 bits: 64 gcc: 7.2.0
           Desktop: Gnome 3.26.1 (Gtk 3.22.25-0ubuntu0.1) Distro: Ubuntu 17.10
Machine:   Device: laptop System: Acer product: Aspire 5735 v: 0100 serial: N/A
           Mobo: Acer model: CathedralPeak v: Rev serial: N/A BIOS: Phoenix v: V1.07 date: 08/27/2008
Battery    BAT0: charge: 57.3 Wh 100.0% condition: 57.3/57.7 Wh (99%) model: SANYO AS07A31 status: Full
CPU:       Dual core Intel Pentium Dual T3200 (-MCP-) arch: Conroe rev.13 cache: 1024 KB
           flags: (lm nx sse sse2 sse3 ssse3) bmips: 7980
           clock speeds: max: 2000 MHz 1: 1995 MHz 2: 1995 MHz
Graphics:  Card: Intel Mobile 4 Series Integrated Graphics Controller bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.5 ) driver: i915 Resolution: 1366x768@59.97hz
           OpenGL: renderer: Mesa DRI Mobile Intel GM45 Express version: 2.1 Mesa 17.2.2 Direct Render: Yes
Audio:     Card Intel 82801I (ICH9 Family) HD Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.13.0-17-generic
Network:   Card-1: Marvell 88E8071 PCI-E Gigabit Ethernet Controller
           driver: sky2 v: 1.30 port: 2000 bus-ID: 02:00.0
           IF: enp2s0 state: down mac: <filter>
           Card-2: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) driver: ath9k bus-ID: 03:00.0
           IF: wlp3s0 state: up mac: <filter>
Drives:    HDD Total Size: 1000.2GB (3.2% used)
           ID-1: /dev/sda model: ST1000LM024_HN size: 1000.2GB
Partition: ID-1: / size: 366G used: 23G (7%) fs: ext4 dev: /dev/sda2
           ID-2: swap-1 size: 8.00GB used: 0.18GB (2%) fs: swap dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 52.0C mobo: 52.0C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 196 Uptime: 1:06 Memory: 2054.6/2934.4MB Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.121) inxi: 2.3.37

```

then

```
top -n 1 -o %MEM

top - 17:29:55 up  1:07,  1 user,  load average: 1,31, 1,60, 1,59
Tasks: 195 total,   3 running, 192 sleeping,   0 stopped,   0 zombie
%Cpu(s): 37,4 us,  6,4 sy,  0,1 ni, 50,3 id,  5,4 wa,  0,0 hi,  0,4 si,  0,0 st
KiB Mem :  3004800 total,    96256 free,  2139528 used,   769016 buff/cache
KiB Swap:  7811068 total,  7639548 free,   171520 used.   696944 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                   
 3048 manolo    20   0 2985860 440784  99784 S   5,9 14,7   7:31.20 firefox                                                                   
 3155 manolo    20   0 2414004 320504  56172 S   0,0 10,7   2:12.40 Web Content                                                               
 3790 manolo    20   0 1326628 310700 121544 S   0,0 10,3   0:23.62 soffice.bin                                                               
 3105 manolo    20   0 2438984 296820  90064 R  17,6  9,9   3:11.84 Web Content                                                               
 3157 manolo    20   0 2560732 287616  74996 S   0,0  9,6   1:58.63 Web Content                                                               
 4317 manolo    20   0 2335428 254724 108288 S  23,5  8,5   0:10.87 thunderbird                                                               
 1025 manolo    20   0 3427384 232256  26356 S   5,9  7,7   6:32.14 gnome-shell                                                               
 3163 manolo    20   0 2601932 192428  67520 S   5,9  6,4   5:59.61 Web Content                                                               
  835 manolo    20   0  493496  72744  55612 S  11,8  2,4   8:04.79 Xorg                                                                      
 1277 manolo    20   0  989688  65236   7076 S   0,0  2,2   0:08.75 gnome-software                                                            
 3755 manolo    20   0  856200  49024  35388 S   0,0  1,6   0:02.03 nautilus                                                                  
 1288 manolo    20   0 1256992  26772  15028 S   0,0  0,9   0:01.93 nautilus-deskto                                                           
 1711 manolo    20   0  820328  25704  17044 S   0,0  0,9   0:01.41 gnome-terminal-                                                           
 1166 root      20   0  452700  22776   1716 S   0,0  0,8   0:02.63 packagekitd                                                               
 2316 manolo    20   0  688656  22632  10932 S   5,9  0,8   2:26.75 gnome-system-mo                                                           
  777 debian-+  20   0   87364  17244   3140 R   0,0  0,6   0:05.88 tor                                                                       
 1083 manolo     9 -11 2749680   7820   5700 S   0,0  0,3   0:01.94 pulseaudio                                                                
  662 root      20   0  859764   7464      0 S   0,0  0,2   0:25.28 snapd                                                                     
 1671 manolo    20   0  885856   6892   1312 S   0,0  0,2   0:00.14 deja-dup-monito                                                           
 1352 manolo    20   0  886616   6648      0 S   0,0  0,2   0:00.17 evolution-calen                                                           
 1436 manolo    20   0  616988   6316   1728 S   0,0  0,2   0:00.20 update-notifier                                                           
 1102 manolo    20   0 1326032   6244   4516 S   0,0  0,2   0:00.24 evolution-sourc                                                           
 1367 manolo    20   0  867628   6156      0 S   0,0  0,2   0:00.14 evolution-calen                                                           
 1211 manolo    20   0  696836   6040   2780 S   0,0  0,2   0:00.51 gsd-color                                                                 
 1228 manolo    20   0  821812   6020   3524 S   0,0  0,2   0:00.26 gsd-media-keys                                                            
 3772 manolo    20   0  152144   5820   4696 S   0,0  0,2   0:00.02 oosplash                                                                  
 1213 manolo    20   0  374528   5660   2340 S   0,0  0,2   0:00.18 gsd-clipboard                                                             
 1196 manolo    20   0  523484   5644   2312 S   0,0  0,2   0:00.23 gsd-xsettings                                                             
 1229 manolo    20   0  526964   5616   2436 S   0,0  0,2   0:00.19 gsd-keyboard                                                              
 1193 manolo    20   0  459340   5556   2284 S   0,0  0,2   0:00.19 gsd-wacom                                                                 
 1209 manolo    20   0  450688   5292   2244 S   0,0  0,2   0:00.17 gsd-a11y-keyboa                     

```

---

### Post by speartip on 2017-11-22
Your specs are very similar to mine. And Gnome performs like treacle. I did wonder if it was my Intel integrated graphics card. But after 2 years tweaking & messing, I've given up on Gnome-Shell.
Xubuntu & KDE Neon on the other hand are Blazingly fast, & have now become my Distros of choice.

---

### Post by favetella on 2017-11-22
Dear speartip, 
First of all, thank you so much for your reply and for your suggestion. Actually I did not know about Neon and it really sounds interesting against Kubuntu considering the few comparison videos I've been watching to make my choice. What is really appealing to me about Neon is that it is less resource consuming than Kubuntu. However it seems that it misses some important features for me, such as KDE Connect and Driver Manager, at least this is what is shown here although the video is something dated: [https://www.youtube.com/watch?v=MDZS1bM8atU](https://www.youtube.com/watch?v=MDZS1bM8atU)
Could I install those feature anyway on Neon too?

Besides that, I've been using Kubuntu for a while but then I went back to Ubuntu since Plasma was quite buggy at that time (it was the 2011). Is it still so buggy as it was in the past?

Thanks for sharing your opinions.
BR

---

### Post by vasa1 on 2017-11-22
I'd venture to opine that most software is buggy to some extent ;)

With that said, I've been using Kubuntu 16.04 with the kubuntu-backports ppa enabled and that works pretty decently. KDE Connect works for me. I haven't tried Driver Manager and so can't say anything about it. My system has an i3 processor with integrated graphics.

---

### Post by speartip on 2017-11-23
@favetella.
Driver manager & connect work fine on Neon. If you want stability go for Neon's LTS version which runs plasma 5.8.8.
The initial install is very minimalistic, & you need to install the software that you want. I find Synaptic best for that. But it uses Ubuntu's repos, based on 16.04, so anything you can install in Ubuntu or derivatives you can install in Neon. I also disable some of the Desktop Effects, it adds a massive boost to speed.

---

### Post by favetella on 2017-11-24
@speartip ***how to disable desktop effects***? It's just what I'm hardly trying to do on Ubuntu 17.10.
However I just found out that the default graphic manager is Wayland that's why I've made some basic test with X and the situation seems to be better.

---

### Post by favetella on 2017-11-24
After giving a deeper look at KDE Neon and Kubuntu, I'm still not sure about what should I install among them. This is what it sounds relevant for me.

**KDE NEON**
PROS: it seems to be lighter than Kubuntu + it contains less preinstalled software which will let me install myself what I really need;
CONS: I'm not sure I may feel comfortable knowing I'm not using the latest release and the latest versions of all the software I need + I'm quite confused when I need to choose which ISO i should download one I decide the release I wish (see the following screenshot)
 [ATTACH=CONFIG]277653[/ATTACH]
The PROS/CONS for me regarding KUBUNTU are the opposite of those listed above for in KDE NEON, so I'll try Kubuntu and let's see what happens.

---

### Post by favetella on 2017-11-25
Hi to all,

dear** speartip,**  thank you so much for reminding me of alternatives to Ubuntu, such as Kubuntu which I'm writing from!As you said, it works incredibly faster than Ubuntu 17.10 (or should we say Ubuntu became incredibly slower than usual?!?) and I think I'll use it from now on, after 11 years being a passionate Ubuntu user :)

Regards.

---

### Post by litlesam on 2017-11-26
Not really sure what's happening. Been using 17.10 ubuntu-gnome from the development stages with no issues. Cloned my HD the other night and installed Ubuntu 17.10 and it was slow, jerky and unusable to say the least. I thought it would be the same now ubuntu is gnome, boy I was wrong.
Glad you are happy with Kubuntu and glad I had a backup to replace whatever it was on there.

---

### Post by speartip on 2017-11-26
Your welcome. Just remember though that having the latest software on the latest edition, doesn't necessarily mean better or more stable. The LTS versions are there for a reason. They have been tested more thoroughly and are less likely to give you any problems.

---

### Post by favetella on 2017-11-28
Yes, you're right also taking into account that latest software may mostly provide benefits on latest hardware, which is not the case of my almost 10 years old laptop...

---

