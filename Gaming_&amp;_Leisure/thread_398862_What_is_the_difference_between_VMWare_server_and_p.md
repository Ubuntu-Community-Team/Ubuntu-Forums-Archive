---
title: "What is the difference between VMWare server and player?"
date: 2007-04-01
forum: Gaming &amp; Leisure
---

### Post by Jarn on 2007-04-01
The title says it all...

---

### Post by yabbadabbadont on 2007-04-01
The best way to compare them would probably be to read the FAQs for the two products.  Short answer, player only lets you, wait for it...., play (run) virtual machines that already exist.  Server is closer to workstation in functionality in that it can create VMs, save and restore snapshots, etc.

[http://www.vmware.com/products/server/faqs.html](http://www.vmware.com/products/server/faqs.html)
[http://www.vmware.com/products/player/faqs.html](http://www.vmware.com/products/player/faqs.html)

---

### Post by Jarn on 2007-04-01
So if I just wanted to use it to run a few Windows programs, not doing anything fancy, Player would but what I would want to use?

---

### Post by yabbadabbadont on 2007-04-01
Only if you already have a VMware virtual machine that has Windows installed on it handy.  Otherwise, you will need to create one and install windows in it.  That is easier with vmware-server.  You can do it which vmware-player too, but you have to use qemu to create the VM first.  There are howtos in the forums for both methods.

---

### Post by Jarn on 2007-04-01
I was looking at the tutorials for them and it seems like all of them need a Windows disk to create an ISO except for one, but people said that that method could cause problems with licensing. Is there a way to create a Windows ISO from a Windows partition? My computer came with Windows installed on it and no Windows disk, only a recovery disk that accessed a recovery partition on my harddrive.

---

### Post by yabbadabbadont on 2007-04-01
I think there are howtos floating around, either here, or on the vmware forums, on how to use vmware-server to run your already installed instance of windows.  It involves setting up a new hardware profile in windows though, so it is not to be undertaken lightly.  If you've already got windows installed, your best bet (for games at least) is to just dual boot.  For other windows programs, you can see if they will work using WINE.  [http://www.winehq.org/](http://www.winehq.org/)  Check the WINE appdb to see if your programs have been reported to work with WINE.

---

### Post by Jarn on 2007-04-01
The games I want to run work fine in Wine. Other things that I want to run, however, do not.

---

### Post by yabbadabbadont on 2007-04-01
Sounds like it's dual boot time for you then.  ;)

---

### Post by Jarn on 2007-04-01
> **yabbadabbadont said:**
> Sounds like it's dual boot time for you then.  ;)

*sigh* Curse you, computer vendors and your lack of Windows disks!

Thanks for your help.

---

### Post by yabbadabbadont on 2007-04-01
I'm just sorry I didn't have a better answer.  Just out of curiosity, which programs were you wanting to run?

---

### Post by Jarn on 2007-04-01
EAC for one. I can get it to run semi-decently in Wine, but not well enough that I'd trust it. iTunes, for another. The appdb lists it as not running in Wine.

---

### Post by cor2y on 2007-04-01
there is a tutorial to clone your whole windows partition into a vmware image.
But depending on how huge it is its might not be practical.
VMWare Server ;  [http://www.howtoforge.com/vmware_converter_windows_linux](http://www.howtoforge.com/vmware_converter_windows_linux) 
VMWare Player : [http://johnbokma.com/mexit/2005/10/26/vmware-player-windows-xp.html](http://johnbokma.com/mexit/2005/10/26/vmware-player-windows-xp.html)

---

### Post by Jarn on 2007-04-01
That isn't practical. :/

---

### Post by yabbadabbadont on 2007-04-02
> **Jarn said:**
> EAC for one. I can get it to run semi-decently in Wine, but not well enough that I'd trust it. iTunes, for another. The appdb lists it as not running in Wine.

I always liked EAC when I used windows, best ripper out there.  In linux though, I use the command line app abcde.  It uses cdparanoia to do the actual ripping, then it encodes and tags the resulting wav files into whichever format you like.  It can encode to multiple formats at the same time too.  I use it to encode to flac (lossless) format and also have it create lower quality mp3 files to be used in my truck and on my portable player.

---

