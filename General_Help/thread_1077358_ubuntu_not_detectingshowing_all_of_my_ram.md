---
title: "ubuntu not detecting/showing all of my ram"
date: 2009-02-22
forum: General Help
---

### Post by arod0405 on 2009-02-22
I have 3Gb installed: 2x 512Mb + 2x1Gb dual channel. Bios detects 3Gb and so does any 64bit kernel and lshw -C memory.
But when I run a 32bit stock kernel free -m, /proc/meminfo & C. all show 2Gb only. So what's happening? Is ubuntu using all of my ram or not?
Thanks!

---

### Post by sdennie on 2009-02-22
When running more than 2-3G of RAM, a 32 bit kernel may not be able to handle all your memory if you aren't running it with PAE enabled.  Is there a reason you can't just run the 64 bit version of Ubuntu?

---

### Post by arod0405 on 2009-02-22
What's PAE? How do I know if it's enabled and where?
I gave a look at kernel config file and found:
CONFIG_HIGHMEM4G=y
So support for at least 4Gb should be there.
I found a strange message at boot, just after grub has run, saying:
not using MMCONFIG
Is that a clue maybe?

Thanks

PS I'm not running a 64bit OS because 32bit is easier to manage.

---

### Post by arod0405 on 2009-02-22
Sorry everybody, it was my fault. I changed a setting in bios and then forgot about that when I installed the new ram banks. Now all is fine.
Thanks!

---

