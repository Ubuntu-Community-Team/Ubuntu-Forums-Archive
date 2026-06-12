---
title: "Reinstalling Grub"
date: 2009-06-19
forum: General Help
---

### Post by EmyrB on 2009-06-19
Hi All,

Got a quick question. I have tripple booted my PC, Win XP, Jaunty and Hardy. The last one to go on was Hardy. As Jaunty has upgraded the kernel, my grub list still shows that it boots into 2.6.28-11. I know I can boot into Hardy and manually edit Grub to boot into the newer kernel, but I was wondering if I could somehow re-install Grub, so that it is controlled by Jaunty and not Hardy.

Cheers

EmyrB

---

### Post by kk0sse54 on 2009-06-19
Was grub ever installed through Jaunty? If so rather than trying to reinstall grub chainloading Jaunty would probably be much easier. Check out this link [http://ubuntuforums.org/showthread.php?t=724817&highlight=multiboot](http://ubuntuforums.org/showthread.php?t=724817&highlight=multiboot)

---

### Post by EmyrB on 2009-06-19
> **C!oud said:**
> Was grub ever installed through Jaunty?

Yep. I installed XP first then, Jaunty. I needed Hardy as since Intrepid, my phone wasn't recognised as a mass media device but a 3G device so I couldn't access the photo's of music on it. Doesn't really matter now as I have upgraded my phone and it is recognised as a mass storage device :)

> **C!oud said:**
> rather than trying to reinstall grub chainloading Jaunty would probably be much easier.

Not really considered this, but after reading the article that you linked to it would be a lot easier. But saying that, I don't really need Hardy any more, hence my question about re-installing grub.

I noticed a few articles on the forums about reinstalling grub after an XP install, would one of those articles be OK to follow?


Cheers

EmyrB

---

### Post by philinux on 2009-06-19
Cloud has shown you the best way to go. you could just use gparted to remove the hardy partition.

Also see this thread.
[http://ubuntuforums.org/showthread.php?t=861205&](http://ubuntuforums.org/showthread.php?t=861205&)

Also when installing on a multiboot. Use the advance button at the end and install grub to the partition in question not the disk/default.

---

