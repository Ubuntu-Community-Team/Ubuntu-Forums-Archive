---
title: "Some applications take forever to load!!!"
date: 2006-07-13
forum: Desktop Environments
---

### Post by DimitrisC on 2006-07-13
I installed ubuntu dapper on my new Dell Inspiron 6000 system as soon as it was released and i think is great.  Almost everything worked out of the box.  I installed many apps from the repositories and i try to keep my system up to date.  However there are some applications that take a long time to load.  Skype for instance takes about 2 minutes from the time i click the shortcut until the main window appears.  Acrobat reader takes a long time to load too.  These are the 2 applications i have a problem with.  Everything else works great and very fast.  Is there a way to speed this 2 apps as well?  Or if its not possible at least make the mouse show that those apps are loading in the background?  (you know like the litle hour glass next to the cursor in wind*ws?)

---

### Post by Schalken on 2006-07-13
I don't know how to speed up those particular apps, but I can tell you that when the mouse cursor has a little spinning circle in it it is the same as the little hourglass next to the cursor in Window$.

---

### Post by meng on 2006-07-13
Skype takes quite a long time to load even on a well-spec'd desktop. As for Acrobat, well there's alternatives such as xpdf and evince, although what you gain in load time you may lose on rendering during runtime. But does Acrobat really take 2 minutes to load?

---

### Post by Vorian on 2006-07-13
> **DimitrisC said:**
> I installed ubuntu dapper on my new Dell Inspiron 6000 system as soon as it was released and i think is great.  Almost everything worked out of the box.  I installed many apps from the repositories and i try to keep my system up to date.  However there are some applications that take a long time to load.  Skype for instance takes about 2 minutes from the time i click the shortcut until the main window appears.  Acrobat reader takes a long time to load too.  These are the 2 applications i have a problem with.  Everything else works great and very fast.  Is there a way to speed this 2 apps as well?  Or if its not possible at least make the mouse show that those apps are loading in the background?  (you know like the litle hour glass next to the cursor in wind*ws?)
Are you using the 386 or 686 kernel version?

---

### Post by DimitrisC on 2006-07-15
Thanks for your replies. I am using 386 kernel. I've searched the forums and finally got an answer.  Skype takes forever to load due to a debian specific problem.  There is a solution to this by using the mandriva rpms through alien but i will just wait until version 2 is released that is said to fix the problem.  As for acrobat reader (no it doesn't actually takes 2 minutes to load :-D) it needs about 35-40 secs to load.

How can i enable launch feedback (the spinning circle mentioned) in all applications?  Some applications like totem, xine, nautilus etc  use launch feedback while others (skype, acrobat reader etc) dont.  Is there a way to enable launch feedback like in KDE for specific applications?

Thanks again for all your help.

---

### Post by DimitrisC on 2006-07-15
Just answering my own question :-D

There is a way to make the spinning circle launch feedback thing work with other applications as well.

Add the following line in the .desktop file for the application launcher:
StartupNotify=true

Check: [http://www.ubuntuforums.org/showthread.php?t=26256&highlight=launch+feedback](http://www.ubuntuforums.org/showthread.php?t=26256&highlight=launch+feedback)


However it would be nice if this was the case for all applications in the first place with a setting in gnome settings menu to turn off and on this feature.

---

### Post by tturrisi on 2006-07-15
My winbook notebook has a P4 3.06 w/ ht & when running the 386 kernel openoffice apps take 21 seconds to load, while if boot using the 686 kernel they open in 9 seconds.  The 686 kernel is much faster for these large apps.   I suggest using xpdf in place of adobe reader.

---

### Post by 3rdalbum on 2006-07-15
Skype should still not take 2 minutes to load. It doesn't really take very long on my computer, which is not speed demon.

---

### Post by philippe_carlo on 2006-07-15
Skype uses the QT libraries, which are not statically linked and usually not loaded (unless you use Kubuntu). It is the loading of the QT libs that takes an awful lot of time. It takes roughly half a minute on my machine too. Using the 686 kernel may result in some speedup there.

You will notice that KDE-apps sometimes take longer to load too, for the same reasons.

---

