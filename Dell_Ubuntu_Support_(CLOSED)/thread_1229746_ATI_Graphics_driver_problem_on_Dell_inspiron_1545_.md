---
title: "ATI Graphics driver problem on Dell inspiron 1545 for 3D games[SOLVED]"
date: 2009-08-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pratik_narain on 2009-08-02
This is my first post friends. I recently purchased a dell inspiron 1545 which comes with ATI Mobility radeon HD graphics card. At first when I installed the proprietery ati driver(fglrx), compiz worked but 3d games like assault cube had problems. After searching a lot, I downloaded the latest ati driver from the ati website. Then, I completely uninstalled  the preivious version with **sudo apt-get remove --purge xorg-driver-fglrx**. This left me with no graphics on the next reboot. So I just logged in to the recovery mode as root and installed the driver that I downloaded earlier from the ati website. After reboot, all was well. My 3d games work flawlessly, compiz of-course and my videos also run smoother. Hope this post might be helpful for somebody ahving a related problem. Also refer to [This Page]("https://help.ubuntu.com/community/RadeonDriver") for further help.

---

