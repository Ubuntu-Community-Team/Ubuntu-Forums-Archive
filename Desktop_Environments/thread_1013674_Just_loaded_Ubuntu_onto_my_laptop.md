---
title: "Just loaded Ubuntu onto my laptop"
date: 2008-12-17
forum: Desktop Environments
---

### Post by northmantim on 2008-12-17
Hi there. I just got the Ubuntu CD in the mail today and just loaded it onto my computer. I have a few questions as I am obviously new to this;
How do I reformat my computer to only Ubuntu?
How do I check the HD memory with Ubuntu? 
How do I change the mouse speed? Everything you can come up with as a question, I will more than likely be asking hehe.
Also, I play Lord of the Rings Online. How do I load it onto Ubuntu?

 Any and ALL help would be GREATLY appreciated as I know nothing, but am willing to learn this OS compared to VISTA that I am running now. 

Thanks in advance.

---

### Post by bgerlich on 2008-12-17
1. Just start the installer - it will give you an option to resize the windows partition or to use the entire disk. You can do it and a lot more manually but if one of those two option suits you, you won't need to.

2. Please elaborate on what you mean by "HD memory"

3. System -> Preferences -> Mouse

4. You can either boot into Windows if you decide to keep it, or you can use Wine - a compatibility layer for windows programs in linux, it seems to support Lord of the Rings well [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14566](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14566). You can install it and thousands of other programs using "Add/Remove Programs" in Applications.

---

### Post by Angry Dog on 2008-12-17
> **bgerlich said:**
> 2. Please elaborate on what you mean by "HD memory"


I suspect he means hard disk space.

Go to Places > Computer.  Right Click on your hard disk and left click on Properties.

If it doesnt show you then double click on your drive first, then go back to Computer and right click on the drive.

---

### Post by Angry Dog on 2008-12-17
Also doing

```
df -h
```

from Terminal will give you the info.

---

### Post by northmantim on 2008-12-17
Wow, Thank you for the fast responses.
 Tho, I am looking to completely get rid of Vista. As it stands, I can not seem to start Ubunto 8.10 on my computer (Duel booting at the moment) without having the disk in the disk drive, if it's not in there, it asks for a command from a DOS like screen when I try to boot Ubuntu. Vista starts normaly (Gods I hate Microsoft-But if it werent for them, I wouldnt know about Ubuntu hehe).
I didnt see an option to overwrite Vista when I first installed Ubuntu. There were 3 options; The first option was to run Ubuntu as a trial. The second was to explore Ubuntu. The third...Well, I don't remember, but it didn't look like it would install it either.
So, after installing Ubuntu into the duel boot mode, how do I completely overwrite Microsoft from this point?

O, and yes, I was talking about my Hard Drive Space in my last post. 

Thank you in advance. I will check the post again after my doctors appointment.

---

### Post by ugm6hr on 2008-12-17
It sounds like you tried to use Wubi, and then only partly installed.

Start again, using this advice: [http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

When you get to the "partitioning" section, just select "Guided - use entire disk".

---

### Post by northmantim on 2008-12-17
Ok thanks guys. I got it loaded fully. Sory about that, I am blonde LOL.
I can already see MAJOR improvements in speed on my computer without Vista, not to mention all the memory and such I now have without it. Only a couple of hours of use, and I already love it. Wish I would have known about something like this when I got my first computer in the late 90's (I am MUCH older than that, but only had my first experiance with one in 1999). 

Now, to fgure out how to load my game on it.

My wife was checking out Ubuntu earlier and I may be loading it onto her computer soon as well. 
I will be definately talking my friends and family into getting this. As so far, it seems pretty straight forward and user friendly. But only time will tell.

 I will be checking out the rest of the forums for any other questions I may come up with to see if they havent already been asked and answered.

Thanks for the fast responses guys!

---

### Post by ugm6hr on 2008-12-17
> **northmantim said:**
> My wife was checking out Ubuntu earlier and I may be loading it onto her computer soon as well. 

I would certainly advocate on behalf of Ubuntu.  But just be wary about promoting it to others until you are in a position to support them through some of the potential pitfalls!

---

### Post by Vantrax on 2008-12-17
I would recommend installing an IRC client such as Xterm and hitting up the #ubuntu channel on freenode for more help too. There are usually people willing to help.

---

