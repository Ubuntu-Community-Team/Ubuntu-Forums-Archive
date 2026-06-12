---
title: "Decoration Windows conflicts with the Unity plugin"
date: 2016-10-13
forum: Desktop Environments
---

### Post by szprott on 2016-10-13
hello after upgrade to 16.04 my compiz  crash Unity top bar, side bar, and window decorations are missing I tried enable Windows Decoration in  ccsm but it makes conflict with Unity Plugin 
I tried reinstall compiz ubuntu-desktop but nothing works
know someone the solution ?

---

### Post by Frogs Hair on 2016-10-13
If you have terminal access try the following.```
sudo apt-get install dconf-tools
```

```
dconf reset -f /org/compiz/
``````
setsid unity
```

---

### Post by szprott on 2016-10-14
> **Frogs Hair said:**
> If you have terminal access try the following.```
sudo apt-get install dconf-tools
```

```
dconf reset -f /org/compiz/
``````
setsid unity
```

doesn`t  work

---

### Post by CantankRus on 2016-10-14
Did unity ever work after the upgrade?
Were you using proprietary gfx drivers or third party ppas prior to upgrading?

The above commands should have worked from an xsession if it was a compiz config issue.
If not, try this method, to remove all user dconf changes.

Log out or reboot and at the greeter screen press ctrl+alt+F1
Log in and run this command....
```
mv ~/.config/dconf/user ~/.config/dconf/user.bak
```

Hit ctrl+alt+F7 to take you back to the greeter and login.

****Note****: You can no longer use the compiz window decoration plugin within the ubuntu/unity session.
The compiz Unity plugin now draws the decoration and thus conflicts.
If you attempt to enable the window decoration plugin, Unity will be disabled......no panel, no launcher.

---

### Post by szprott on 2016-10-14
> **CantankRus said:**
> Did unity ever work after the upgrade?
Were you using proprietary gfx drivers or third party ppas prior to upgrading?

The above commands should have worked from an xsession if it was a compiz config issue.
If not, try this method, to remove all user dconf changes.

Log out or reboot and at the greeter screen press ctrl+alt+F1
Log in and run this command....
```
mv ~/.config/dconf/user ~/.config/dconf/user.bak
```

Hit ctrl+alt+F7 to take you back to the greeter and login.

****Note****: You can no longer use the compiz window decoration plugin within the ubuntu/unity session.
The compiz Unity plugin now draws the decoration and thus conflicts.
If you attempt to enable the window decoration plugin, Unity will be disabled......no panel, no launcher.

thx but still doesn`t work i have enable the unity plugin  the window decoration off still the same  no panel no luncher:(

---

### Post by CantankRus on 2016-10-14
...and
> **CantankRus said:**
> Did unity ever work after the upgrade?
Were you using proprietary gfx drivers or third party ppas prior to upgrading?

Also, does unity work in the Guest session?

---

### Post by szprott on 2016-10-14
> **CantankRus said:**
> ...and

Also, does unity work in the Guest session?

unity work in 14.10 fine ,

I use nvida driver in lxde works fine 

guest session the same problem

today I upgrade to 16.10 still the same

---

### Post by monkeybrain20122 on 2016-10-14
When you say "upgrade" did you actually *upgrade* as in using the package manager doing it automatically or did you just mean installing a new system? If you did the former then the solution  is simple, just do a fresh install. "upgrade" is known to be problematic and might have corrupt your settings since OS changed quite a bit from 14.10 to 16.04. I

 have a spare computer and recently did an "upgrade" from 14.04 to 16.04 and unity was messed up. took 10 minutes to start firefox and maximise file manager froze the system. Did a fresh install and it all works. Lesson: avoid "upgrade"

---

### Post by szprott on 2016-10-14
> **monkeybrain20122 said:**
> When you say "upgrade" did you actually *upgrade* as in using the package manager doing it automatically or did you just mean installing a new system? If you did the former then the solution  is simple, just do a fresh install. "upgrade" is known to be problematic and might have corrupt your settings since OS changed quite a bit from 14.10 to 16.04. I

 have a spare computer and recently did an "upgrade" from 14.04 to 16.04 and unity was messed up. took 10 minutes to start firefox and maximise file manager froze the system. Did a fresh install and it all works. Lesson: avoid "upgrade"

can I make fresh install and save my home folder?

---

### Post by monkeybrain20122 on 2016-10-14
> **szprott said:**
> can I make fresh install and save my home folder?

If you have a separate /home partition then all you need to do is to install the system in /. But in your case even if you do it is not advisable as your settings are likely corrupted. Just save your data and do a completely clean re-install would be your best bet. To anticipate future OS update, before you install use gparted from a live usb to create three partitions: a small one for root (mount point /) about 25G should be more than enough (typically 15G  would be enough for most people but on the safe side it doesn't hurt to have some slack if you are not tight on hard disk space) then a /home partition for the rest, this is where all your data live, then a swap. When install, choose "something else" and instruct the installer to use these partitions as above. Then next time when you update your OS, you just have to reinstall in the '/" partition and leave the /home alone (don't format it next time)

---

