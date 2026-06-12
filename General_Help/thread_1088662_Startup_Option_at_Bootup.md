---
title: "Startup Option at Bootup"
date: 2009-03-06
forum: General Help
---

### Post by newbie_ub on 2009-03-06
Hello All
I had XP in my PC and then i installed ubuntu 7.10.
Now, at startup, it shows Ubuntu option at first and XP is at 4th position ( under Other OS).
The time to startup to the firstoption that is Ubuntu is 10 secs.

I want to make XP at 1st position so that XP starts by default when the time elapses.
What to do ?

I am a complete newbie to linux/ubuntu. Please help me out.

---

### Post by unutbu on 2009-03-06
There is a way to do this by editing /boot/grub/menu.lst, 
but if you'd like a nice GUI to control the changes, install the
startupmanager package.

Once installed, click System>Admin>Startup Manager.
The use of the GUI should be self-evident.

If you'd like to do it by editing /boot/grub/menu.lst, then all you have to do is open a terminal (Applications>Accessories>Terminal) and type
```

gksu gedit /boot/grub/menu.lst
```

and change
```

default   0
```

to 

```
default   3
```
Save the file.
 
(Since GRUB counts boot stanzas starting at 0, the number 3 represents the 4th boot stanza (i.e. XP))

---

