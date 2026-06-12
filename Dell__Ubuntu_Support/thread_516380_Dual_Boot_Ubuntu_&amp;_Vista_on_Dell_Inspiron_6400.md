---
title: "Dual Boot Ubuntu &amp; Vista on Dell Inspiron 6400"
date: 2007-08-03
forum: Dell  Ubuntu Support
---

### Post by neogenesis213 on 2007-08-03
I have been dual booting windows and ubuntu (well actually triple booting if you count XP and Vista separately) for a few yrs on my desktop. I seem to be having problems with my laptop though, which I bought recently.

The specs on the inspiron 6400 are 1.8Ghz core 2 duo, 1G ram, 160Gb hard drive, intel GMA 950.

Vista came preinstalled. I installed feisty and made a separate boot partition and installed grub on that. However after I restarted my laptop it booted straight to windows. No grub menu or anything of that sort. I can see that there are linux partitions from paragon partition manager and I can see that some space has been used on those including the boot partition. However no GRUB. It boots straight to windows. 

Has anyone else had this problem? Any help would be appreciated!

---

### Post by pbcartwright on 2007-08-03
google dual boot +vista..
[http://apcmag.com/5045/how_to_dual_boot_vista_with_linux](http://apcmag.com/5045/how_to_dual_boot_vista_with_linux)
it can be done, there are just a few extra steps.

---

### Post by neogenesis213 on 2007-08-04
Thanks pbcartright. I tried the method using easyBCD. I made sure I had all the right settings but unfortunately it was all to no avail. When i choose linux on the vista boot manager a few lines came up. No errors. But there it froze. It did not make it to even the loading screen of ubuntu. If someone has experienced this problem and has solved it without having to wipe their hard drive clean plz help. I think the dell utility partition at the start of the hard drive may have something to do with the problem. This is my first dell so im a noob. plz help!

---

### Post by jongkind on 2007-08-04
This may not be of real help for you, but I just used installed Feisty on an Inspriron 6400 which had Vista already installed. I used the alternate disk for this and no problems were experienced. 

What I suspect is that when you made the partitions you forgot to tick the "bootable flag" of your root partition. You can correct that with Gparted via a Live CD.

---

### Post by neogenesis213 on 2007-08-04
you nailed it jongkind that's exactly what I had to do and voila it worked!

---

### Post by Computer Guru on 2007-08-07
[SIZE=2]I know you got this to work, but for anyone else trying this out:[/SIZE]
[SIZE=2]If EasyBCD wouldn't boot the Ubuntu partition it's probably because GRUB wasn't installed to the Bootsector but rather to the MBR (as is the default).[/SIZE]
 
[SIZE=2][EasyBCD 1.61]("http://neosmart.net/forums/showthread.php?t=642") has a new option for adding a "GRUB-less" Linux entry to EasyBCD & the Vista boot menu - it should do the trick.[/SIZE]

---

### Post by neogenesis213 on 2007-08-08
Haha you just gotta hate microsoft or is it dell. Well now that ubuntu is working I cannot seem to hibernate when in windows. So when I click hibernate in vista it seems to be working then screen goes blank and instead of shutting down I am presented with the login screen - as if i  had resumed from hibernate. What did you do to solve this jongkind? or anyone else?

---

### Post by Computer Guru on 2007-08-09
It's a known bug: [http://neosmart.net/blog/2006/vistas-hideous-wakeup-support/](http://neosmart.net/blog/2006/vistas-hideous-wakeup-support/)

---

### Post by jongkind on 2007-08-09
> **neogenesis213 said:**
>  What did you do to solve this jongkind? or anyone else?

Stopped using Vista.

---

