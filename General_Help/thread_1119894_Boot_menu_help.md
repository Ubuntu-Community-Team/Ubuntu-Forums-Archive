---
title: "Boot menu help"
date: 2009-04-08
forum: General Help
---

### Post by Matt Burnside on 2009-04-08
Hi, im just after a little help. Im currently running ubuntu and windows xp on seperate hard drives and im just wondering if theres a way to stop my computer loading either when i switch on the power. What i want is some kind of menu to come up, preferably not on a timer, simply just to choose which system to boot.

Thanks in advance.

Matt

---

### Post by GeeZor on 2009-04-08
I think you should install GRUB...
Work for almost everyone...

Good luck!

---

### Post by kryptikos on 2009-04-08
Stopping the auto boot selection is fairly easy. Log into your ubuntu and open a terminal (Applications -> Accessories -> Terminal)

Once that opens we need to modify Grub's menu.lst file from the prompt on the terminal:

1. enter: ** sudo nano /boot/grub/menu.lst**

2. Once the file opens move the cursor down with the arrow keys to the line that says: [B]## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3
[/B]

3. Add a "#" in front of the 'timeout 3' value (do not input the "")

4. hit Ctrl+O and save the file out (just hit enter) and then Ctrl+X to exit nano. 

Next time you reboot the box should just hold at its splash screen until you choose which OS you desire to boot. Hope this helps :)

---

