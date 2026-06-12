---
title: "DBAN error nook and boot"
date: 2008-12-18
forum: General Help
---

### Post by NoL618 on 2008-12-18
I did the nook and boot hard drive...I was running fine for two hours or so and then it gave me this message:

DBAN finished with non-fatal errors.  

What does this mean?  Do install the ubuntu OS now?

---

### Post by kanikilu on 2008-12-18
Haven't seen that error before. If you google it, there are some suggestions, such as changing a particular BIOS setting:

[http://bbs.heidi.ie/viewtopic.php?f=6&t=2578](http://bbs.heidi.ie/viewtopic.php?f=6&t=2578)

If you are using the UBCD, you could also try one of the alternate disk wiping utilities.

You could instead write zeros to the hard drive using dd from the live cd with the hard disk mounted:

[http://www.linuxquestions.org/linux/answers/Hardware/Clean_Hard_Drive_zero_fill](http://www.linuxquestions.org/linux/answers/Hardware/Clean_Hard_Drive_zero_fill)

It's not as effective as something like Boot and Nuke, but it's better than nothing.

---

### Post by ibuclaw on 2008-12-18
Is there anything else included with that message?

If not, I presume it may be safe to assume so.

But, as a precaution, just check the size of the disk first though, and make sure that it reads correct.
I had one lad the other week who used a hard drive shredding software only to find that the hard drive LBA was reset to 28bits, meaning that he could only access 137GB of his 250GB hard drive.

It was easily resolved though...

Regards
Iain

---

### Post by jimmy the saint on 2008-12-18
If the drive is blank don't worry about it.  The purpose of DBaN is to wipe the drive.  As long as it is wiped, errors don't matter.  That said, if the drive is making noise, that combined with the error might make me leary of using it for anything important in the futuer, as it may be a sign of a failing disk.

---

### Post by NoL618 on 2008-12-18
The whole message says:

DBAN finished with non-fatal errors.
This is usually caused by disks with bad sectors.
Send the log file with all support requests. 

How would I go about looking at the size of the space?

---

### Post by ibuclaw on 2008-12-18
> **NoL618 said:**
> How would I go about looking at the size of the space?

If you boot into the Ubuntu LiveCD, and go into
**System -> Administration -> Partition Manager**
In the menu, gparted will tell you the total size of the drive, and any listed partitions - ideally, there would be none if your run of dban was successful.

Regards
Iain

---

### Post by NoL618 on 2008-12-18
OK, i just tried booting from the live cd and got this error message:

"this kernel requires an x86-64CPU but only detected an i686 CPU.  Unable to boot please use a kernel appropriate for you CPU"

What does this mean?
What do I need to do?

---

### Post by kanikilu on 2008-12-18
Sounds like you have the CD for the 64-bit version. You need the 32-bit version for that computer, apparently.

Go to [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) to get the 32-bit ISO and make a new CD.

---

### Post by NoL618 on 2008-12-18
Ooooh....i have that one...let me try it! Thanks!!!

---

