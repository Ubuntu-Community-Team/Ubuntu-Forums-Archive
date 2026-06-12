---
title: "problems with everything! i need help!"
date: 2009-07-11
forum: Desktop Environments
---

### Post by adam182 on 2009-07-11
hi everyone, ive been using 9.04 jaunty, for about 2 months now but slowly problems have started to show up and i have no idea how to fix them!!! so . . 

first problem, i try to install the recommended upgrades but the computer says that there is not enough disk space (why not! 500gb hard drive, 4 gb ram, new computer!!!)

second problem (also with memory) i have tried to transfer all my pictures from an external hard drive to the pictures folder, however, once again not enough memory (total folder size only 84mb)!! 

and thirdly, after the first 2 months (maybe something ive done but don't understand!) gnome , compiz and all visual effects, cube and themes (such as dark room) re-set themselves to ´human' each startup!! so it feels like the first time you've ever turned it on! every time! which is really anoying!! 

and as a noob to this OS i would apreciate any help i can get to help resolve these issues

any ideas??

---

### Post by Blacklightbulb on 2009-07-11
For the disk space problem first.

Did you partition and format you hard disk correctly?

Go to SYSTEM->ADMINISTRATION->Partition Editor

Now check that your mounted partition had enough free space. If not select it an resize it properly.

---

### Post by irv on 2009-07-11
Are you just running Ubuntu or are you dual booting with Windows? When you installed Ubuntu there were three options to install:
1.) use available space
2.) use the entire drive
3.) manual install (setup the partitions yourself)
Which one did you do?

---

### Post by adam182 on 2009-07-11
well, IRV, thank you for answering my query (not normal in my experience, normaly have bad luck with forums!) i did what it said, and the installation wizard said install as partition, 

so when i turn on the computer now it gives me the option of. 

boot ubuntu kernal 
boot ubuntu generic (crash recoverry)
windows vista
windows vista 

is this the problem?

---

### Post by irv on 2009-07-11
> **adam182 said:**
> well, IRV, thank you for answering my query (not normal in my experience, normaly have bad luck with forums!) i did what it said, and the installation wizard said install as partition, 

so when i turn on the computer now it gives me the option of. 

boot ubuntu kernal 
boot ubuntu generic (crash recoverry)
windows vista
windows vista 

is this the problem?

This is normal. You did a dual boot with vista. Now I don't know how much disk space your vista was taking up when you did the install so a good way to find out how much space you have is to boot into ubuntu kernel and go to Applications>Accessories>Disk Usage Analyzer and post the results. Or you can open the Disk Analyzer and take a screenshot, and upload it to a post.
This will tell the story on how big your partition for Ubuntu is and how much space you have left.

---

