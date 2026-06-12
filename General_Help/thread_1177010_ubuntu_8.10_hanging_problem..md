---
title: "ubuntu 8.10 hanging problem."
date: 2009-06-02
forum: General Help
---

### Post by prabhanjan2906 on 2009-06-02
i am using ubuntu 8.10. i actually upgraded to 9.04(through update manager) and when every thing had got installed the computer restarted. then when i entered the user name and password i noticed that mouse cursor was not moving. when i pressed enter after entering the password it did not move any further. i got hanged there only. then nothing could be done. i could only restart. i then inserted the ubuntu cd and selected the option "install without making any change to my computer" and then saw the type of the disk where the ubuntu was installed it showed
SEC_TYPE="ext2" TYPE="ext3". is formatting the only option or can i get back my ubuntu?

---

### Post by utnubuuser on 2009-06-03
Can you access the recovery console at boot?

And if yes, have you tried > sudo dpkg --configure -ato see if the install can clean itself up?  (I'm not sure if that command works anymore with 9.04, but it might be worth a try before re-installing).
and yes, you can install ubuntu without over-writing the files.  -- choose not to format at partitioning. (It's a checkbox option you can check/uncheck if you select manual partitioning. - not sure if it's an option if your not selecting partitions manually.

---

