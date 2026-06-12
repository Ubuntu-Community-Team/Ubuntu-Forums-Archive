---
title: "[Ubuntu 9.10] Dungeon Crawl Stone Soup fails to start"
date: 2009-11-26
forum: Gaming &amp; Leisure
---

### Post by lejonmanen on 2009-11-26
Hello!

I upgraded to Ubuntu 9.10 from the previous version but accidentally erased my old Dungeon Crawl Stone Soup installation, so I had to do it all over. I downloaded it from sourceforge.net and built it from source. When I got it to compile and ran the executable, it didn't display any output even though it consumed all the CPU cycles on one of my CPUs. (I'm gonna leave it on for some hours, if anything happens I'll report back to this thread.)

This problem exists both on version 0.5.2 (the latest version as of now) and the version 0.4.5 that I installed using Synaptic. On the previous Ubuntu 9.x I had no problem compiling and running 0.5.2. I suspect that it has something to do with some system setting I changed in Ubuntu, but I have no idea where to start.

Has anyone come across this problem and solved it?

/David  ](*,)

---

### Post by lejonmanen on 2009-11-30
*bump*

Is there something I should try or should I rephrase my question?

/David

---

### Post by Perfect Storm on 2009-11-30
Tried this? [http://gwos.org/doku.php/guides:64bit:dungeon_crawl_stone_soup](http://gwos.org/doku.php/guides:64bit:dungeon_crawl_stone_soup)

---

### Post by lejonmanen on 2009-11-30
Thanks for the link, I installed it using the instructions. I have also tried installing Dungeon Crawl Stone Soup version 0.4.5 from Synaptics, the package manager. In both cases the program behaved in the same way. I believe there is some setting in Ubuntu that is responsible for Crawl no longer working, but I don't know what I should do to find out what settings are causing the problem.

/David

---

### Post by lejonmanen on 2009-12-09
If anyone has the same problem, removing the folder .crawlrc in my home directory solved the problem...

---

