---
title: "Find lost product key for Microsoft in Linux?"
date: 2009-02-18
forum: General Help
---

### Post by Smeags on 2009-02-18
Hello,

I have lost the product key for a copy of Microsoft Visio that is installed on a XP installation.  I can't boot into that installation currently.  As soon as I log in, it logs me right back off automatically and continues to do so in an infinite loop.

I can mount the drive in Ubuntu and view all the files with no problem.  I'd like to wipe the corrupted system and start clean, but I need Microsoft Visio on the system but I lost the product key for it.  Is there any way on Linux with the Windows drive mounted to find the product key for Visio that's installed on there?

---

### Post by Tony Flury on 2009-02-18
I don't see how - from what i know the product keys are not stored in plain text (not even in the registry), so it is unlikely that you could retreive it.

Did you register Visio with MS ? if so they might be able to re-issue a key.

---

### Post by Smeags on 2009-02-18
Unfortunately I don't know if it was ever registered with MS.  It is on a PC from our office that another user had been using, but that user is no longer with us.

---

### Post by whoop on 2009-02-18
This is a long shot :-)
Install wine and see if you can start visio from the windows partition while running in linux. If visio starts up you might be able to collect the product key in the about box.

Probably won't work, but you could try

---

### Post by Therion on 2009-02-18
Possible solution?  This from my Windows-useage days...  

[http://www.magicaljellybean.com/keyfinder/](http://www.magicaljellybean.com/keyfinder/)

Edit:  Oh, shoot... You can't even BOOT the XP partition??  Forget my above suggestion then.

---

### Post by philinux on 2009-02-18
[http://magicaljellybean.com/keyfinder/](http://magicaljellybean.com/keyfinder/)

try running windows in safe mode to get it. I've used this and it works.

---

### Post by Smeags on 2009-02-18
Haha, actually I can't boot into safe mode either!  I get the same login/logout loop as when Windows boots normally.

@whoop:  I hadn't thought about running Visio through Wine...I was able to view the registry via Wine, but I didn't try Visio.  Yes, probably a long shot, but I'll try it.  Thanks for the suggestion!

---

### Post by Smeags on 2009-02-18
Update: I installed Wine and tried to run Visio through it.  The Visio 2003 logo came up, but it just stays there frozen and it says error for the active window for it on the bottom panel.

I've done some quick searching to see if Visio can be run under Wine and it looks like it can, however from my brief browsing through search results it looks like that's for people that are installing it through Wine, which I can't do.  I need Wine to run an already installed Visio from a mounted Windows disk.

I'll keep searching.

---

