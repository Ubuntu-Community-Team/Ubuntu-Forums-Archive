---
title: "Desktop Effects could not be Enabled"
date: 2008-02-28
forum: Desktop Effects &amp; Customization
---

### Post by Mountainman11 on 2008-02-28
I just installed Gusty and tried to install Compiz-fusion.  I read around and made sure the restricted drivers were turned on.  I have an AMD 3800+ 64 bit x2 with an Nvidia GeForce 7800gt.  I'm fairly new to Linux and any help would be appreciated.

---

### Post by Yellow Pasque on 2008-02-28
Make sure your /usr/bin/compiz is set up properly:
[http://ubuntuforums.org/showpost.php?p=4202892&postcount=6](http://ubuntuforums.org/showpost.php?p=4202892&postcount=6)
Then, go to the terminal and type 'compiz'. It might run just by doing the first suggestion, but even if it doesn't, it will give you a much more specific error message than trying to enable through the GUI.

---

### Post by Mountainman11 on 2008-02-28
I didn't get to check if it was set up properly.  I tried typing compiz into the terminal and it came up with no whitelist driver.

---

### Post by Yellow Pasque on 2008-02-28
Well, make sure that file is set up properly and has nvidia in the whitelist (line 71).

---

### Post by ajeetraj on 2008-02-28
Alright i have solved the same problem like your's yesterday on this forum. Just go to this link and follow the instructions from my post!

I am pretty sure it will solve your problem :)

[try this link]("http://ubuntuforums.org/showthread.php?t=441399&page=2")

---

### Post by Yellow Pasque on 2008-02-28
> **ajeetraj said:**
> Alright i have solved the same problem like your's yesterday on this forum. Just go to this link and follow the instructions from my post!

I am pretty sure it will solve your problem :)

[try this link]("http://ubuntuforums.org/showthread.php?t=441399&page=2")

The OP has an Nvidia card which is not blacklisted, so that won't solve his/her problem.

---

### Post by Mountainman11 on 2008-02-28
I was getting the error that I didn't have XGL so I installed it.  Now when I try to run compiz it goes back to the loading screen then to the logon on screen and doesn't tell me anything else.

---

