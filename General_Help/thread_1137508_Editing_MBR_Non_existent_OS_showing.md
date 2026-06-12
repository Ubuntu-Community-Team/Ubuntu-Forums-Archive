---
title: "Editing MBR? Non existent OS showing"
date: 2009-04-25
forum: General Help
---

### Post by LightSeeker1445 on 2009-04-25
Hi, I thought I posted this question before, but I probably forgot to actually press the post button :)

Anyway ... I have a Windows XP installed, but due to some problems I had to install Ubuntu twice, but it was deleted when making the second instalation. The problem is, that I now have a GRUB loader that shows the first three options of running Ubuntu, then the XP OS and lastly it repeats the three options of running Ubuntu. 

Is there any way of fixing this, like deleting the unneccessary options in the MBR?

Any help will be apreciated, thanks!

---

### Post by SuperSonic4 on 2009-04-25
You can delete them by editing /boot/grub/menu.list as root

```
sudo nano /boot/grub/menu.list
```

You can then either comment out the last set of lines with a # at the start or delete them (in nano you can cut a whole line with ctrl+k)

Press Ctrl+x to exit and press enter twice to save it

---

### Post by LightSeeker1445 on 2009-04-26
Hey,
I deleted the unnecessary lines and partitions that I found were still having Ubuntu on it. Then Grub reported an error 22, couldn't boot up anything.

Then I used XP's recovery console for fixboot, and it could only run XP after that.

After that I downloaded Super Grub Disk and oordered it to restore my Linux MBR - it worked and I now only have the three options to run Linux plus the XP option.

Will all things be alright from now on? Did I do the thing correctly?

---

