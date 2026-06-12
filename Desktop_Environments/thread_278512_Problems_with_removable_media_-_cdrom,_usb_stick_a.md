---
title: "Problems with removable media - cdrom, usb stick and usb hdd"
date: 2006-10-16
forum: Desktop Environments
---

### Post by kennywest on 2006-10-16
I am using Ubuntu since Hoary and on the whole I am very pleased with Ubuntu. Upgrading to a next version, however, can be quite painfull. But, since I know my way around in Linux I've always managed to fix my install.
After upgrading to Breezy, devices were not mounted automagically anymore. I found another person that had the same issue: [http://www.ubuntuforums.org/archive/index.php/t-77141.html](http://www.ubuntuforums.org/archive/index.php/t-77141.html)
I didn't care much because I could always mount stuff by hand, but somehow I can't live with the fact that it "should" mount automagically, but in my specific case it "just doesn't". Even after I upgraded to Dapper the issue is still there.
Can someone please give me some clues on how to fix this?

---

### Post by kennywest on 2006-10-16
I've found a solution to my problem: [http://www.ubuntuforums.org/archive/index.php/t-186560.html](http://www.ubuntuforums.org/archive/index.php/t-186560.html)

solved the problem by adding

session optional pam_foreground.so

to the end of /etc/pam.d/common-session

No idea why this solves my problem ...

---

