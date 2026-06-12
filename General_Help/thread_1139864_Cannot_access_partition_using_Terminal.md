---
title: "Cannot access partition using Terminal"
date: 2009-04-27
forum: General Help
---

### Post by snorbens on 2009-04-27
Hi,
Hope that you can help a silver haired newbie.

I created a partition called Back Up and am trying to access it with Terminal without luck

This is what I input and the answers I got. I am obviously doing something very stupid,or missing something.
CODE:

mervyn@mervyn-laptop:~$ sudo su
[sudo] password for mervyn: 
root@mervyn-laptop:/home/mervyn# cd /media/Back Up
bash: cd: /media/Back: No such file or directory
root@mervyn-laptop:/home/mervyn# cd /media/Back-Up
bash: cd: /media/Back-Up: No such file or directory
root@mervyn-laptop:/home/mervyn# cd /Back-Up
bash: cd: /Back-Up: No such file or directory
root@mervyn-laptop:/home/mervyn# (/code)

Hope that you can help and I apologise for not putting the code in a box.
Someone told me what to do but I obviously misunderstood the instruction,and/or forgot.

Thanks.

---

### Post by mikewhatever on 2009-04-27
You can look into /media with **ls /media** command. Back Up and Back-up are not the same and aren't interchangeable, and could be labels and not mount points, but if Back Up is the mount point, the you should enter cd /media/Back\ Up/.

---

### Post by benj1 on 2009-04-27
if you go to places on the desktop other partitions should show up and you can open it in nautilus to check the path is correct.

on a side note be aware that if its a separate partition on the same hard drive, youll still lose the data on the backup partition.

ps to enter code either click on the '#' on the top of the text box or use CODE & /CODE in square brackets

---

### Post by snorbens on 2009-04-27
Thanks for your help.

I will check it out and try again.

At the moment I am doing a full backup via the terminal and will have a go soonest.

Once again thanks

---

### Post by snorbens on 2009-04-27
> **benj1 said:**
> if you go to places on the desktop other partitions should show up and you can open it in nautilus to check the path is correct.

on a side note be aware that if its a separate partition on the same hard drive, youll still lose the data on the backup partition.

ps to enter code either click on the '#' on the top of the text box or use CODE & /CODE in square brackets

Hi,
Just read your reply again about losing that partition as well.
Thanks. I will have to burn the backup to DVD RW.

---

### Post by snorbens on 2009-04-27
> **mikewhatever said:**
> You can look into /media with **ls /media** command. Back Up and Back-up are not the same and aren't interchangeable, and could be labels and not mount points, but if Back Up is the mount point, the you should enter cd /media/Back\ Up/.

Hi, Thanks. Worked a treat. cd /media/Back\ Up/.

I will gradually learn it...just at my age, it is going to take time, but I am really enjoying this OS:lolflag:

---

