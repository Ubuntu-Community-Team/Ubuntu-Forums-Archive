---
title: "Raid error? Grub not loading."
date: 2009-01-11
forum: General Help
---

### Post by Kukabarra on 2009-01-11
Dear all, got a severe problem. Tried to install 8.10 on a computer of my girlfriend), with Vista onboard. Computer has 2HDDs and RAID. To install Ubuntu the boot partition of Vista (disk C) was shrinked (successfully) using gparted and the ubuntu was installed to the partition formed from all of the unallocated space, including first region of the HD. After that I've reinstalled grub to the correct partition.

Now comes the crap. None of the systems boots; the only option to load is ubuntu live cd. Grub menu does not appear. Any ideas what to do?

Thanks in advance.

---

### Post by themusicalduck on 2009-01-11
Does any error message come up when you try to load grub? Or is there just a blank screen and nothing else?

---

### Post by Kukabarra on 2009-01-11
No error message, and turning off the disk on which linux was installed makes booting vista possible.

So the correct algorithm is to turn off raid mirror, resize partitions, install linux, relocate grub, turn on raid mirror?

---

### Post by domoso on 2009-01-11
I just had a problem with a 8.10 on my desktop because I have a RAID controller installed in addition to the controllers built in to the mobo. However, I did get a menu. It just wouldn't run any of the entries. 

The fix for me was to remove the RAID controller and reinstall grub from livecd. It worked. After that I reinstalled the RAID controller. Everything is good. 

I'm guessing you're running RAID 0? Perhaps you should break the mirror, remove the second harddrive and reinstall grub from live cd??? Then reinstall the second harddrive and reestablish the mirror.

---

### Post by themusicalduck on 2009-01-11
Unfortunately my experience with raid is more limited than with grub, so not sure what to suggest. Sure someone else on here will have an idea though.

---

### Post by caljohnsmith on 2009-01-11
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

