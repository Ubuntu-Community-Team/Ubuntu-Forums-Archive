---
title: "Is Xubuntu hiding  HD?"
date: 2009-06-14
forum: General Help
---

### Post by CalvinE on 2009-06-14
I decided to go to Xubunbu (from Win XP) and downloaded/burned the installation stuff. For some reason, it didn't want to boot from the live CD (BIOS is set to CD boot first), so I let the autorun start in Windows, and clicked the bottom "installation button", the one that says to click it if it won't boot from the CD. I had it overwrite all of XP, and it installed very nicely. I noticed some errors about not finding a hard drive, but I figured that since Xubuntu loaded just fine, everything must be ok.
 
But, I decided it would be a lot smarter to reformat the hard drive and partition it into two sections so I could also get Debian on it. The easiest way I could think to reformat/partition was with the Windows XP install disk (Legal CD), so I stuck it in and rebooted. Windows setup started, loaded all its stuff, then told me that there was no hard drive! I tried several times; each time it told me it could not find a hard drive. If I don't push enter when the Win XP CD tells me too, Xubuntu will come right up. I get an error that no HD exists, then Xubuntu hops in and loads up. So, what happened that Windows disk can't find a HD? Did that bottom button I clicked on the Xubuntu autorun popup when I still had XP on the computer some how hide the hard drive or...? 
 
Also, a little off topic, but what am I doing wrong that neither of my live CD's (Debian and Xubuntu) don't load at startup? I download the iso and burn it with Roxio (from a different Win XP comp) but the computer doesn't want to use it to start up (though it started off the Win XP disc).

---

### Post by QIII on 2009-06-14
Why didn't you want to just install from the live disk, if you were getting rid of XP?

You may still have a Windows boot partition on your HD, but probably not anything else.

The reason your XP disk won't work is that when it first loads, it loads into RAM and runs its processes there.  It does that because, as far as it is concerned, it hasn't done stuff like checking for hard drives, so can't run from a drive anyway.

The reason it is not finding a disk is because the only one you have on the machine now is no longer formatted for Windows (except for maybe the boot sector), so it makes no sense to the XP disk.

Do you want to install Xubuntu and permanently get rid of XP?  If so, if you can get the LiveCD running at all, just select the Install option.

---

### Post by ajgreeny on 2009-06-14
When you burn the CDs you must burn as a disk image, not simply copy the iso file to the CD.  If possible have a look on another computer and see if the CD contains just one file xubuntu###.iso, which is wrong.  It should have several folders and files, as in the attached pic of nautilus

---

### Post by QIII on 2009-06-14
Thanks ajgreeny.

I made an inappropriate assumption that the OP had properly prepared the LiveCD.

---

