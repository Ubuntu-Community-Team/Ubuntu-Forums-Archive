---
title: "Grey Window"
date: 2015-03-19
forum: Desktop Environments
---

### Post by michael-piziak on 2015-03-19
In 12.04 lts and 14.04 lts, sometimes, a window or screen will grey out while it's doing something.

What does this mean.  And how long should one wait.  For example, I'm installing Ubuntu Restricted Extras and it has sat there greyed for about 5 minutes or more.

---

### Post by kerry_s on 2015-03-19
that kept pissing me off to, i chose to move on to something else after unity crapped out on me a 3rd time.

---

### Post by deadflowr on 2015-03-20
> I'm installing Ubuntu Restricted Extras and it has sat there greyed for about 5 minutes or more.
Software Center?
Have you gotten to the Microsoft EULA yet?

---

### Post by JohnnyComeL8ly on 2015-03-20
It means that your system is busy... I advise, like kerry_s said, to just move to something else.  I recommend Lubuntu 14.10.  It is very resourceful (in the best of ways).  I haven't gotten fast enough hardware to run Unity or LinuxMint yet: I've always come back to Lubuntu because of that.  One thing you could try doing, which I found I liked, is installing Lubuntu from ISO (and then, in the order presented...) ```
sudo apt update && sudo apt upgrade && sudo apt install ubuntu-desktop-mir
```

---

### Post by Frogs Hair on 2015-03-20
```
ubuntu-desktop-mir
``` > Is a Settings package which installs everything Ubuntu Desktop needs to use Mir
(via XMir). This is experimental and not ready for daily use and is likely to break the system. Do not install unless testing unity8 which won't improve system resource usage. Unity8 testing should not be done on a daily user system.

---

### Post by deadflowr on 2015-03-20
I simply was wondering if, because the mention of ubuntu-restricted-extras, whether or not the EULA pop up window ever showed up.
Sometimes, it opens the pop up window behind the main software center window; it is not suppose to, but it happens.
In this state it is not because the window is busy, but because the window is waiting for the user action on accepting or denying the terms of the EULA.

There is also another state in the installation of the extras package where it might seemingly hang, and that is when flash gets installed.
When the extras package installs flash, the program connects to adobe's site directly, instead of the usual connection to the Ubuntu repos.
So, the connection to adobe depends on how well adobe's site is running at the time. IMO.

Why other windows hang usually depends on what type of file that particular program is trying to load.
Sometimes the program hangs because the file that it is trying to load is totally bonked.
Of course, though, this is only sometimes, and not reflective of all or every time.

---

### Post by JohnnyComeL8ly on 2015-03-26
I'm sorry if I gave out bad advice, but I thought it was already in use in Ubuntu by default....  I don't know if it makes a difference, but I haven't noticed any problems.

---

### Post by Frogs Hair on 2015-03-26
> **JohnnyComeL8ly said:**
> I'm sorry if I gave out bad advice, but I thought it was already in use in Ubuntu by default....  I don't know if it makes a difference, but I haven't noticed any problems.

 deadflowr may have been on the right track with EULA conformation for the restricted extras, specifically for the MS core fonts. 

You might not have noticed any difference without all the Unity8 components installed. ;) 
   
[http://www.phoronix.com/scan.php?page=news_item&px=MTg4MjQ](http://www.phoronix.com/scan.php?page=news_item&px=MTg4MjQ)

---

### Post by Stavro on 2015-03-30
I thought it usually meant your application being greyed out was not responding, most likely due to excessive page file usage. Basically, the window manager & programs talk to each other & the moment that conversation goes for a while is when the window manager decides to inform you about it (via making the window grey). Windows does this also, except the windows go white.

---

