---
title: "Brand new Dell Ubuntu machine hangs at Grub boot"
date: 2009-02-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kiwi8mail on 2009-02-02
I have a brand new Dell Ubuntu laptop that, two hours ago, was working.   For no (apparent) reason, switching it on now doesn't get me past the stage of "GRUB" appearing at the top of the screen, following by a space, followed by a flashing underscore cursor.   It continues in this state indefinitely, and has to be switched off.

I thought perhaps a failed hard drive, although putting the live CD in reveals the hard drive is still there, and the files on it are intact.

Is the Grub boot script somehow corrupted?   Or is this a hardware problem?

Is it worth trying to remedy this, or given how random this problem is, and how new the computer is, would it be wiser to send this back to Dell?   

Any advice much appreciated.

---

### Post by mikehenson on 2009-02-02
If Ubuntu is the only OS installed try this at the grub> command line

grub> root (hd0,0)
grub> setup (hd0)
restart computer 

"root (hd0,0)" will not give an output to the screen
"setup (hd0)" will give a few lines of output to the screen 

MSH

---

### Post by kiwi8mail on 2009-02-02
Thanks for the advice, but the keyboard doesn't seem to be responsive - no commands appear in response to my typing.   Incidentally, however, deleting what I have "typed" eventually causes it to start making beeping noises with each keypress, if I delete back far enough (to the beginning of the line?)

---

### Post by superm1 on 2009-02-02
> **mikehenson said:**
> If Ubuntu is the only OS installed try this at the grub> command line

grub> root (hd0,0)
grub> setup (hd0)
restart computer 

"root (hd0,0)" will not give an output to the screen
"setup (hd0)" will give a few lines of output to the screen 

MSH
Well if Ubuntu is the first partition and the only OS is a better way to say this.

If you have a preinstalled system, you will have more partitions, and those commands will need to be adjusted.

---

