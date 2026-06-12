---
title: "Dropping caches causing Ubuntu to hang on shutdown?"
date: 2015-08-04
forum: Desktop Environments
---

### Post by Jake_Lester on 2015-08-04
BACKGROUND:
So I'm testing some new diagnostic software which runs in Ubuntu (Passmark's BurnInTest). We iPXE-boot machines, the diag runs automatically, then Ubuntu is installed to the HDD. When testing memory, the diag software is programmed to not eat up all of the RAM, as it supposes there is a swap partition and doesn't want its data swap'd. So I decided to disable swap anyhow, but that was still 'passing' computers with known bad RAM sticks. Then I decided to sync RAM and drop all caches from memory, in the hopes that this program will be able to test as much RAM as possible. That seems to do the best job of failing bad RAM, but there seems to be a catch. (If this is a stupid way to do things, please tell me I'm being stupid.)

PROBLEM:
When I drop caches, Ubuntu stalls on shutdown. I can sync RAM and disable swap and it will shutdown a-ok, but if I drop caches, it hangs. It will first hang right after
***ModemManager[1390]: <info> ModemManager is shut down***

Though sometimes it says:
***ModemManager[1390]: <warn> Could not acquire the 'org.freedesktop.ModemManager1' service name***

...but I have a hunch modemmanager has nothing to do with the hangup. Because if I let it sit there, a few more messages usually pop up that say something akin to:

***<INFO>: task {various tasks} blocked for more than 120 seconds.***

Once those all fail, it throws a couple squashfs errors (unable to read page, unable to read fragment cache entry). I have to guess this is due to some network timeout... not too sure about squashfs errors though. Finally, it gets snagged once again after ***Deactivating swap...   [OK]***. That's as far as it gets before I lose patience and pull the plug.

It seems to happen on any hardware we throw at it. ***shutdown -v -h now*** gives no further information, and produces the same problem.

THINGS I'VE TRIED:
appending ***noapic nolapic acpi=off*** to the boot kernel args
removing the modemmanager1.service file
freeing dentries and inodes, along with pagecache
shutdown -r 0
shutdown -h 0
init 0
init 6



So, how would I even go about diagnosing this issue? Since it's a live boot, I can't exactly look at logs after a hard reset. Is it possible to drop into a terminal once the shutdown process has gotten this far? How the heck could dropping caches even cause this sort of issue? Thank you for any sort of insight you can throw my way!

---

