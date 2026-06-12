---
title: "Performance problems and hdparm questions.."
date: 2006-08-07
forum: Desktop Environments
---

### Post by richardq on 2006-08-07
I've been having problems with slow application launch times and now with certain programs just slowing down randomly. The only way I've been able to cut the launch times down is by removing fonts from my system (surely that can't be right). But still certain programs, like firefox, or synaptic will run fine 60% of the time and other times they will slow right down.

While it has been bearable, it's still a bit of pain. I'm also concerned about my hd settings. I have two physical drives on my system. The first drive (sda) holds my existing XP installation as well as my root and swap partitions for Ubuntu. The second drive (hdb) holds another XP data partition and my home partition for linux.

I'm not sure what the hdparm settings should be but both drives indicate 16-bit IO and only the hdb drive lists dma as being on. Is 16-bit the correct setting? The drives are fairly new (less than 2 yrs old) 160GB western digital drives. And why can't I enable dma for the sda drive? This is the drive that holds all my apps etc, so this might affect performance no?

Here is a shell output of my query of both drives along with the error I get when I try to enable dma on the sda drive. If anybody can shed some light on this, I'd greatly appreciate it.

```
richard@ubuntu:~$ sudo hdparm /dev/sda

/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 19457/255/63, sectors = 312581808, start = 0

richard@ubuntu:~$ sudo hdparm /dev/hdb

/dev/hdb:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 19457/255/63, sectors = 312581808, start = 0

richard@ubuntu:~$ sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
richard@ubuntu:~$
```

---

### Post by vampiric_blade on 2006-08-08
edit your /etc/hdparm.conf file.  The file gives you plenty of info on how to enable/disable things.  Enabling 32bit io is done with the -c1
option in command line, or you can just add this to the end of your hdparm.conf (replacing your proper device names of course).

/dev/hdc {
        dma = on
        io32_support = 1
}

/dev/hda {
        io32_support = 1
        write_cache = on
        dma = on
}

hdc is my dvd; hda is my hdd.

Alternatively, you could command line:
hdparm -d1 -c1 /dev/hda

***edit***

I have no clue why you can't enable dma on your one drive...

---

