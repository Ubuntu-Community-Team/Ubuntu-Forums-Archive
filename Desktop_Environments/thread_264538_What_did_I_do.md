---
title: "What did I do ???"
date: 2006-09-24
forum: Desktop Environments
---

### Post by banko on 2006-09-24
Hey guys,


I purchased a new computer yesterday for the front room. The specs are:

Pentium 4 HT processor
512 MB RAM
200 G SATA Hard Drive
DVD Burner
and onboard everything you can think of

Not my usual "build from scratch", but I was feeling lazy and $300 dollars seemed like to good of a deal.

First thing I did was a standard install of Ubuntu dapper, with the default settings and partitioning.  Everything installed fast and worked perfectly.  Then it was time to install the essentials:

build-essentials gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs gxine libxine-main1 libxine-extracodecs ogle ogle-gui flashplugin-nonfree sun-java5-bin sun-java5-plugin

OK, system as you can see its the normal base installation plus essential media crap.  Then I got the bright idea that I was going to install a p2p network and decent jukebox, so my wife would be happy and leave me alone:

amarok amarok-engines gtk-gnutella

Everything appeared normal, I downloaded a few songs then made way for my wife to get her music.  Came back a couple hours later and gnome has become EXTREMELY slow at opening programs.... However, once the applications are open they run normally.  My internet connection is still extremely fast, but waiting for firefox to open, is a stress test in itself.

So after looking at my swap space I noticed it was 100% in use... that's no good.  I added 1024MB swap file, and enabled it in fstab rebooted my computer.  Things were a little better.  However there is still definate lag when opening or closing programs.... actually even minamizing and maxamizing has a very noticable lag.  Remember this is with no programs running accept the one firefox window I was using....

I decided that we should uninstall amarok and gtk-gnutella and stick with the default music player, and I would find a different p2p program for her.  So I removed the apps.  And still no improvement.

Can someone please tell me how at what point I went wrong.... I have abuntu on my computer and i have yet to experience any problems like this at all.  However I also have an AMD64 and 1Gig of RAM in mine.  Is Ubuntu Gnome really this slow if you don't have a higher end computer?

---

### Post by sir_saucealot on 2006-09-24
Maybe run 'top -d 1' for a while to see what is actually happening...see what processes are using up most of the resources, and watch the memory usage (especially buffers and how much actual memory is free - both swap and main)
512 MB of RAM isn't that much, but the system should be quite usable - not as slow as you are experiencing it.

Need a bit more info...

---

### Post by banko on 2006-09-24
OK I have no programs running accept firefox which is minimized doing nothing, while i took this data..... As you can see I have a pile of swap space not being used, but when i do anything it floods fast.  

Thanks for your reply, I hope you can help me with this....  The major slowness seems to be resolved now, but there is still lag everytime i open, close, minimize, or maxamize any program.


top - 18:22:06 up  1:00,  2 users,  load average: 1.14, 0.64, 0.34
Tasks:  94 total,   1 running,  93 sleeping,   0 stopped,   0 zombie
Cpu(s): 13.0% us,  1.0% sy,  0.0% ni, 86.0% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    451300k total,   321812k used,   129488k free,     8740k buffers
Swap:  2365856k total,        0k used,  2365856k free,   172348k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4356 root      15   0 61064  36m 6304 S 10.0  8.3   5:20.67 Xorg
 6811 banko     15   0 71932  15m 9788 S  3.0  3.5   0:01.48 gnome-terminal
    1 root      16   0  1568  528  460 S  0.0  0.1   0:01.05 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.17 events/0
    5 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0
    9 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  119 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  120 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  122 root      16  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  121 root      25   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0
  709 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod
 1798 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0
 1799 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 ata_hotplug/0
 1802 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
 1803 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1
 1821 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1914 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kjournald
 2144 root      13  -4  2428  916  368 S  0.0  0.2   0:00.27 udevd
 2942 root      20   0     0    0    0 S  0.0  0.0   0:00.00 shpchpd_event
 3054 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2
 3055 root      10  -5     0    0    0 S  0.0  0.0   0:00.31 usb-storage
 3876 root      16   0  2152 1196  644 S  0.0  0.3   0:00.00 acpid
 3971 syslog    16   0  1764  672  548 S  0.0  0.1   0:00.01 syslogd
 3997 root      16   0  1684  500  412 S  0.0  0.1   0:00.01 dd
 3999 klog      17   0  2380 1304  388 S  0.0  0.3   0:00.04 klogd
 4322 root      15   0 10912 1780 1204 S  0.0  0.4   0:00.00 gdm
 4341 root      16   0 11356 2600 1952 S  0.0  0.6   0:00.01 gdm

---

### Post by banko on 2006-09-25
I decided to do a reinstall, but this time with xubuntu as it is meant for computers far lesser than this.  The system flew through the install, and again gave me a fast desktop on my first boot.  However, as soon as I installed the codecs, flash, and java the system started showing the same problems....

Windows showing a definite lag when opening, closing, minimizing and maximizing

Can someone please explain how adding multimedia codecs and support would effect the over all system performance... even when they are not being used?

---

### Post by dcstar on 2006-09-25
> **banko said:**
> I decided to do a reinstall, but this time with xubuntu as it is meant for computers far lesser than this.  The system flew through the install, and again gave me a fast desktop on my first boot.  However, as soon as I installed the codecs, flash, and java the system started showing the same problems....

Windows showing a definite lag when opening, closing, minimizing and maximizing

Can someone please explain how adding multimedia codecs and support would effect the over all system performance... even when they are not being used?

Just out of interest, what does running "glxinfo" show?

---

### Post by theturner on 2006-09-25
Have you examined the amount of memory that Firefox uses? I'd think the flash and java plugins are the root of all evil.

---

### Post by FurryNemesis on 2006-09-25
I agree with DCStar - you mention that your windows, the drawings of which are managed by your graphics card, seem slow. From the list of stuff you installed you don't seem to have any drivers on there. If it's an Nvidia then the packages are in Synaptic or follow this guide [here]("http://www.ubuntuforums.org/showthread.php?t=139264&highlight=ati") , my guess is you're still using the default Xvesa driver or something like that. If you've got an ATi, go [here]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27") and dl the drivers.

---

### Post by Lord Illidan on 2006-09-25
Don't forget DMA..

```
sudo hdparm /dev/hd*
```

EDIT : post the output of that here, please.

---

### Post by banko on 2006-09-27
Thanks for your replys and sorry for the delayed response.  ATI driver solved the issues.  However due to my strong dislike for using their closed drivers, I made the decision to do a fresh install without java or flash.  

Everything runs completely smooth as silk now.  Thanks for all your help.  I sincerly hope that AMD keeps good to their word and opens up the ATI drivers to the linux community, upon their purchase of the company.

I know this is off track, but do you guys feel AMD share holders would ever allow such a move, as opening the ATI drivers to Linux?

---

