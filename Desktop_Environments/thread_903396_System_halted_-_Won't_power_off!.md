---
title: "System halted - Won't power off!"
date: 2008-08-28
forum: Desktop Environments
---

### Post by GodsDead on 2008-08-28
Hey all i have a new install of ubuntu 8.04 Desktop - all updates installed. Everything seems to run ok? although the entire system wont power off!!!
System runs through text on screen and ends with just 
```
[ 5160.620402] System Halted
```

And hands there forever, some bits in the PC turn off, as i can hear them click off and less sounds comes out but i dont know what they are :S

Please help! this is the "family" PC for my mum and she isnt "computer friendly" and i dont think she will want to hold teh power button every time -__-

---

### Post by yaztromo on 2008-08-28
Could you try the suggestion here: [http://www.understated.co.uk/2004/automatic-shutdown-in-ubuntu/](http://www.understated.co.uk/2004/automatic-shutdown-in-ubuntu/)

If that doesn't work you can try (especially if this is an old machine) to add the option acpi=force to the end of your kernel line in /boot/grub/menu.lst

---

### Post by GodsDead on 2008-09-04
whey hey! thanks dude, that link worked perfect =]

---

### Post by Shannon_VanWagner on 2010-02-08
I have one of those machines that has to either have ACPI turned off in the BIOS, or I have to boot with acpi=off.

My machine works good except it doesn't power off when I shutdown, just stops at "System Halted" with the power still on.

So after trying different things such as apm=power_off in grub.cfg / menu.lst, and apm in /etc/modules, etc. nothing was working for me.

What finally worked for me was a tip from [this]("http://www.brighthub.com/computing/linux/articles/39504.aspx") article by Michael Dougherty, where I booted with pci=noacpi in grub.cfg / menu.lst.

For Ubuntu Karmic 9.10, I made the following changes after making a backup copy of the "/etc/defaults/grub" configuration file:

sudo vi /etc/defaults/grub

Change the line
GRUB_CMDLINE_LINUX_DEFAULT=" acpi=off quiet splash"

to
GRUB_CMDLINE_LINUX_DEFAULT=" pci=noacpi quiet splash"

then run this to apply the changes and rebuild your grub.cfg
sudo update-grub

After rebooting, my machine shuts down without issue.

Ubuntu GNU/Linux is awesome!
Shannon VanWagner

---

### Post by itagomo on 2010-03-18
hey Shannon, i'm going to try this later, i'll post then if it fixes my problem.
I just received my 9.10 karmic koala this week.

---

### Post by itagomo on 2010-03-18
hehe, it didn't work.
Is there any other way for my 9.10?

---

