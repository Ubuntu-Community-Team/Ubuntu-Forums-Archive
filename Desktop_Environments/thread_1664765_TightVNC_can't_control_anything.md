---
title: "TightVNC can't control anything"
date: 2011-01-11
forum: Desktop Environments
---

### Post by Jundy on 2011-01-11
Hi,

First time using Ubuntu, Please treat me as one.

I have successfully managed to install and connect via remote TVNC as shown in this site:
[http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop](http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop)

Now after I have updated and restarted the system.... it worked 100%

I can click, open, close, choose anything on screen.

Next update is Nvidia driver, The Ubuntu update window popped up again to update the Nvidia driver, so I clicked Activate and restarted.

Now, when I use TVNC, I can only login, and see the Xwindow, but can't do anything, open, choose, close, nothing is working.

I checked the options under remote desktop and the allow other users to control your desktop is ticked.

Please advise ?

Regards,
Jundy

---

### Post by Jundy on 2011-01-11
Yay, I found it

[http://ubuntuforums.org/showthread.php?t=1599894](http://ubuntuforums.org/showthread.php?t=1599894)

I made my search for the first time couldn't find anything,

now I found the solution.

Thanks for reading, 

Regards,
Jundy :D

---

### Post by endotherm on 2011-01-11
the problem is likley your desktop effects. after installing the nvidia driver, the target box most likely enabled compiz effects, which have a history of messing up VNC. 

in your vnc client settings look for a check box about "X damage" or somthing like it, and flip it to see if it clears up your issue. 
alternately you can either disable desktop effects on the target box (rclick the desktop) or you can ssh into the box first and run 
```
metacity --replace
``` to disable compiz before connecting to vnc.

---

### Post by Jundy on 2011-01-11
Thanks for the useful info

-J

---

