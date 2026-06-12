---
title: "RAM cache for firefox with slow ssd?"
date: 2009-05-25
forum: General Help
---

### Post by alanwalterthomas on 2009-05-25
I have an acer aspire one with a slow 16 GB SSD formatted as JFS. It works well enough except when I'm browsing. I load a page, & I usually have to wait a few seconds before I do anything at all with the computer (scroll, click on a link, open apps menu to open another program, type, ANYTHING but move the mouse). I suspect it may be because firefox is cacheing everything. I would like some cache so that I don't have to download the whole page if I click the back button, but I also don't care for offline storage of websites. Is there a way to make firefox touch the hard drive as little as possible, like using ram for chche during my browsing session? Thanks,

---

### Post by alanwalterthomas on 2009-06-09
I found this & it helped:

[http://swik.net/Ubuntu/Only+Ubuntu/Firefox+cache+in+ramdisk+(tmpfs)/clhgn](http://swik.net/Ubuntu/Only+Ubuntu/Firefox+cache+in+ramdisk+(tmpfs)/clhgn)

sudo mkdir /media/ramdisk

sudo mount -t tmpfs -o size=64M,nr_inodes=10k,mode=0777 tmpfs /media/ramdisk

Type about:config in Firefox's URL bar.
Find/Create browser.cache.disk.parent_directory in the page that appears.
Set its string value to /media/ramdisk/

gksudo gedit /etc/fstab

Add the line

tmpfs /media/ramdisk tmpfs size=64M,nr_inodes=10k,mode=777 0 0

& That's all.

---

### Post by dcstar on 2009-06-09
> **alanwalterthomas said:**
> I have an acer aspire one with a slow 16 GB SSD formatted as JFS. It works well enough except when I'm browsing. I load a page, & I usually have to wait a few seconds before I do anything at all with the computer (scroll, click on a link, open apps menu to open another program, type, ANYTHING but move the mouse). I suspect it may be because firefox is cacheing everything. I would like some cache so that I don't have to download the whole page if I click the back button, but I also don't care for offline storage of websites. Is there a way to make firefox touch the hard drive as little as possible, like using ram for chche during my browsing session? Thanks,

Yes, just set a new Memory Cache Integer value in **about:config** to a lot more than default (I have mine set to 250000, but I have 4GB of RAM so 250MB of cache is no problem for me):

```
browser.cache.memory.capacity
```

You can check what is actually being used by putting this in your Firefox:
```
about:cache
```

This is a lot simpler than stuffing around wasting RAM on Ramdisks, this memory will be released to the rest of your system when Firefox closes.

---

