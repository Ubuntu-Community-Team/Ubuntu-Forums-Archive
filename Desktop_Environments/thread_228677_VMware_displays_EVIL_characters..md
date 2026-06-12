---
title: "VMware displays EVIL characters."
date: 2006-08-03
forum: Desktop Environments
---

### Post by Washington Irving on 2006-08-03
I installed VMware using [this HOWTO]("http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware") which worked fine. I then installed Windows XP Pro and that too worked fine. Next I installed VMware Tools, as suggested in the original HOWTO. This all seemed fine. The next day, when I rebooted, there was an update for my kernel so I installed it. Then when I fired up VMware it displayed some really messed up characters. I searched for an answer and found a guy with the same problem on the VMware forums. Only one answer had been made and it said to re-run the vmware-config.pl script which I subsequently did. This did not fix it and I then realised that I should probably update my headers but when I typed ```
sudo apt-get install linux-headers-`uname -r`
``` I found that they were already installed (and come to think of it I thought I saw them in the update manager). I even tried re-installing VMware (with the vmware-uninstall.pl script) and then installing in accordance with the HOWTO. I still get these evil box characters. Screenshots attached. Anyone know how to solve this problem?

EDIT: I'm using 64-bit Ubuntu.

---

### Post by robmoore on 2006-08-03
I'm seeing the same thing... No clue how to fix it.

---

### Post by Washington Irving on 2006-08-04
I found the soulution (well miasma did):

> It's caused by the recent update of ia32-libs-gtk. You can revert to version 16 via "Force version" in Synaptic.

I found that at [this thread]("http://ubuntuforums.org/showthread.php?t=228518").

---

