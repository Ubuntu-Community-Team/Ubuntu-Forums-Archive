---
title: "CPU Spikes every 3 seconds"
date: 2009-01-30
forum: General Help
---

### Post by mikehenson on 2009-01-30
I found after updating to Ubuntu 8.10, Kernel 2.6.27-11, my processor would spike to 100% every 3 seconds. I tied killing kacpid the processes using most time (nothing happened). I remember in the past never having this problem. So when my computer now starts I made the Grub boot Ubuntu 8.10, Kernel 2.6.27-7 and the heart beat goes away. I will continue to use the older kernel until another update comes.

MSH

Marked solved on 20090424

---

### Post by Mud.Knee.Havoc on 2009-01-30
> **mikehenson said:**
> I found after updating to Ubuntu 8.10, Kernel 2.6.27-11, my processor would spike to 100% every 3 seconds.

Did you run top (or whichever other version you prefer, I like htop) to see which process was doing this?

---

### Post by mikehenson on 2009-02-05
UPDATE
I dual booted my machine to run Xubuntu.

So I tried Xubuntu 8.10, Kernel 2.6.27-11, my processor would also spike to 100% every 3 seconds. 
After running top in terminal, I tied killing kacpid the processes using most time (top said Not Valid). So I booted into Xubuntu 8.10, Kernel 2.6.27-7 and the heart beat goes away. 

I am haveing the same problem in both Ubuntu and Xubuntu with Kernal 2.6.27-11
I will continue to use the older kernel until another update comes.

MSH

---

### Post by mikehenson on 2009-02-17
This is an update, I am still having this problem. I have attached a screen shot of my gnome with top running.

Any suggestions will be nice.

MSH

---

### Post by mikehenson on 2009-04-24
Update, I finally used this thread to solve my problem, [http://ubuntuforums.org/showthread.php?t=399619 ]("http://ubuntuforums.org/showthread.php?t=399619")

I did a acpi=off in the /etc/grub/menu.lst

MSH

---

### Post by mikehenson on 2009-04-28
Update,
I found that acpi=off also makes the volume buttons not work. After doing some more reading, and trying different things, I believe I found the problem. (maybe a bug) I have a completely dead battery, it will not hold a charge. I unplugged the battery while the computer is on and my heart beat stopped. I have attached images of my desktop for everyone's viewing. Please look at the system monitor icon located in the panel (upper left). 

MSH

---

