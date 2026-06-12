---
title: "How to make Firefox faster on Ubuntu persistent live-USB?"
date: 2012-12-23
forum: Desktop Environments
---

### Post by envis on 2012-12-23
Due to admin rights problems at work :P I ended up deciding to run from my own USB key on the work computer. Its awesome that I can run my own Ubuntu desktop that remembers all my settings and programs installed ect and carry it on a USB stick and boot it on any computer. But I was finding the browser firefox kept jamming all the time on the 2nd day (first day it was less bad for some reason) and I found a great way to speed Firefox at this link [https://wiki.archlinux.org/index.php/Firefox_Ramdisk](https://wiki.archlinux.org/index.php/Firefox_Ramdisk)

Basically they suggest 3 ways, I did the easy one:

>  Method 1: Use RAM-only cache

Firefox can be configured to use only RAM as cache storage. Configuration files, bookmarks, extensions etc. will be written to harddisk/SSD as usual. For this

    open about:config in the address bar
    set browser.cache.disk.enable to "false" (double click the line)
    set browser.cache.memory.enable to "true" (double click the line)
    set browser.cache.memory.max_entry_size to the ammount of KB you'd like to spare, to -1 for automatic cache size selection 

Main disadvantages of this method are that your tabs won't survive a browser crash, and that you need to configure the settings each user individually. On the other hand on a personal system it probably is the easiest method to implement.


It makes a huge difference so I decided to share this trick :D Also wondering if anyone else has tricks to make persistent live-USB Ubuntu faster?

---

### Post by vasa1 on 2012-12-24
Trivial point but an ad blocker does wonders as well. Adblock Plus for Firefox has an advanced option that is really powerful and I find it very useful for sites I visit often.

And then there as some CSS tricks that may make for a plainer but "lighter" experience:
```
* {
-webkit-box-shadow: none !important;
-webkit-gradient: none !important;
-webkit-linear-gradient: none !important;
text-shadow: none !important; 
-webkit-border-radius: 0 !important; 
}

```
Of course, webkit may need to be replaced by moz depending on the browser.

---

### Post by Rebelli0us on 2012-12-24
Use SDHC **UHS** flash drive, and if possible boot form USB 3.0 port with USB3+UHS-compatible card reader. That way Linux will run just like from hard-disk.

---

