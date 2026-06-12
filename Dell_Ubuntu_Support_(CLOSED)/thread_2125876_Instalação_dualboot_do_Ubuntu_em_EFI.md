---
title: "Instalação dualboot do Ubuntu em EFI"
date: 2013-03-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by waltercoan on 2013-03-15
Hi,

I'm trying to install ubuntu with sidelong win8. I follow this thread ([http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)) but when ubuntu install try to search my free partiton space that i "shrink" from the partition of windows, that error occours: "Ubiquity crashed with typeerror in partman_dialog(): 'nonetype' object is not subscriptable

The screen error ara attached.

Some one can help? Tks!

---

### Post by oldfred on 2013-03-15
You should use Windows Disk Tools to shrink a NTFS partition and reboot a couple of times so Windows can run its fixes on its new size. Then you should be able to use the unallocated space.

But you are trying to install 13.04. That version is in development and will not be released until 13.04 or the end of April. So it should not be your main install. 
If you want to install into a smaller 10 to 25GB partition just for testing with 12.04 or 12.10 as your main installs then that should be fine.

It also looks like it is not seeing any partitions. Is this a system with Intel RST or an UltraBook. That uses RAID and the desktop installer does not have the RAID drivers.

        HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)
Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)

---

### Post by waltercoan on 2013-03-15
Hi,

Thanks for the fast reply. Yes, my computer is an ultrabook Dell XPS 14. I've try to install ubuntu desktop 12.04 and 12.10 and the same error ocours. In your answer, you said that Desktop version dont have raid drivers, i should use server version to install?

Tks again,

---

### Post by oldfred on 2013-03-15
Everyone seems to turn Intel SRT off & remove RAID meta-data from drives. Some that do not use Windows much just install Ubuntu to SSD and do not turn SRT back on. Others seem to be able to just turn SRT back on and it works. 

The thread I posted above was one of the better as it covered the issues.

  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

 Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)
Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)



      
 Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
From some of the users that had RAID.
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

