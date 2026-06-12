---
title: "my windows partitian appears under devices however i cannot load into"
date: 2013-11-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by peterderdakmagic on 2013-11-08
[COLOR=#232323][FONT=helvetica]Hey so I had a working dual boot with windows 7 and ubuntu 13.10 on my inspiron 14z, and last night while I was on ubuntu I installed some system updates which it said were required, but now WHen i boot the laptop I cannot log into windows 7 EVEN THOUGH IT APPEARS UNDER DEVICES WHEN I AM IN UBUNTU...please help, I already tried boot repair tool and it had no luck/

**and let me clarify this dual boot [/FONT][/COLOR]
[COLOR=#232323][FONT=helvetica]VVV boot screen, normally window 7 is at the bottom..but ever since last nights update, it no longer appears and I have no way of logging into it.

[http://imageshack.us/photo/my-images/585/e8qc.jpg/](http://imageshack.us/photo/my-images/585/e8qc.jpg/)

VV my view when I am inside ubunut, the file labeled "OS" is the contents of my windows hard drive...But on the boot screen I cannot log into it
[http://imageshack.us/photo/my-images/202/dgmi.jpg/](http://imageshack.us/photo/my-images/202/dgmi.jpg/)[/FONT][/COLOR]

---

### Post by peterderdakmagic on 2013-11-08
here is my boot summary from boot repair app...still no help [http://paste.ubuntu.com/6385645/](http://paste.ubuntu.com/6385645/)

---

### Post by deadflowr on 2013-11-08
Firstly, did you read the very end of the boot repair output?

And secondly, did you try updating grub?
```
sudo update-grub
```

Post the output.

---

### Post by oldfred on 2013-11-08
Is this an Ultrabook with Intel SRT and small SSD using RAID? RAID will cause issues on installing grub correctly in a standard BIOS or UEFI system.
        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

---

