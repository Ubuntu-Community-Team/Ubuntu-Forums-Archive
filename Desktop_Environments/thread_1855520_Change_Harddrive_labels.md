---
title: "Change Harddrive labels"
date: 2011-10-06
forum: Desktop Environments
---

### Post by kgerbers on 2011-10-06
When I look in computer, my windows partition named WINDOWS is showed as 500 GB harde schijf: WINDOWS

how can I remove the ¨500 GB harde schijf:¨ part?

I am dutch so in English it will say something like 500 GB harddrive.


Thanks in advance, 

Kees

---

### Post by spiky001 on 2011-10-06
Open Disk utility You can change the names there

---

### Post by cyiucsy on 2011-10-06
Well, there might be easier ways, but the first one that I could think of is using gparted.
if you don't have it installed, open a terminal and type
```
sudo apt-get install gparted
```

then you can open it
System->Administartion->GParted Partition Manager
or simply
Alt+F2->gparted

Then you should see a list of partitions.
Please unmount the partition first by
right-click "500 GB harde schijf: WINDOWS" and click "unmount".

Then right-click "500 GB harde schijf: WINDOWS" again
and click "label" and you should be able to rename it into whatever you want. ;)

---

### Post by kgerbers on 2011-10-07
Yes, I do know how to change te label, my problem is that i have a label, WINDOWS,
Which i can change in everything i want.
But after i click ok ubuntu adds this 500 gb harde schrijf text, which i can't change because it is added afterwards

---

### Post by Basher101 on 2011-10-07
I always change the Windows partition names from WITHIN windows. Works like a charm here

---

### Post by kgerbers on 2011-10-07
Maybe an example will make my question clear:

Laptop, dualboot win7 - ubuntu 11.04

In windows i have a partition named 'WINDOWS'
But when i start ubuntu, that same partition is named '500 GB harde schijf: WINDOWS'

I want to remove the '500 GB harde schijf' part,
My problem is that this is not part of the label, If i change the label in TEST with for example gparted,
Ubuntu shows:  500 GB harde schijf: TEST

So the label is only the uppercase name, the rest is added by ubuntu, and I suppose this has to be changed in some gnome conf file.

---

### Post by coffeecat on 2011-10-07
Hi, I know of no way to remove the "500 GB harde schijf:" in a "computer" nautilus window. Perhaps someone else does. It irritates a lot of people - you are not alone - but it's an upstream issue and it would appear the gnome people are unlikely to fix it, particularly as they are now focussed on gnome3.

This will be of little help to you, but here's another thread where the OP's question was originally misunderstood as well (regrettably including by myself):

[http://ubuntuforums.org/showthread.php?t=1841791](http://ubuntuforums.org/showthread.php?t=1841791)

There's a bug report cited towards the end of the thread.

By the way, I see you are using 11.04. Are you opening "computer" from the Places menu in the classic desktop? I don't bother with "computer" any more, because the partitions listed in the left pane of Nautilus tell me all I want to know and are not blighted with unnecessary information.

---

### Post by kgerbers on 2011-10-07
Thank you, i have searched for similar topics but i didn't know what keywords would describe it, therefore is my topic title also misleading.

I had some bad experiences with the new unity theme, it was very slow and crashed a lot, the classic is quick and hasn't caused me any trouble on my acer aspire 7730G laptop

But to answer your question, yes I open computer from the places menu, i've made shortcuts on my desktop for these partitions so i don't have to use the computer menu butni was wondering if it was possible to remove it.

I wil read the other topic, and hope they wil find a way someday or update as gnome3 will be released

Again thanks for the explanation.

PS: i found a patch for those who really want to remove these names, i will try it tommorow (or later this day) and post my result.
[http://askubuntu.com/questions/35955/how-to-hide-hard-disk-size-in-volume-name]("http://askubuntu.com/questions/35955/how-to-hide-hard-disk-size-in-volume-name")

---

### Post by kgerbers on 2011-10-09
The patch i mentioned in my previous post works perfect, until a solution is provided by nautilus , everyone can do it thIs way

---

