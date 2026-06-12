---
title: "Keyboard mapping change when Gnome session starts"
date: 2007-04-25
forum: Desktop Environments
---

### Post by sean.clarke on 2007-04-25
Hi,
    I am seeing an odd problem whereby on the GDM login screen my keyboard works perfectly, however when I login my keyboard mapping changes to be something completely unusable.

I am not running an "average" system, I am using Feisty with Sun Ray thin clients. I have tried on the Sun Ray forums and not been able to get to the root of the problem. I'm hoping a Gnome guru sees this and can let me know the steps Gnome goes through when it starts a new session so I can try and locate the problem.

I have cleared out a users keyboard settings in their gconf directory, but still I see this problem and I have systematically tried all of the Gnome mappings in the "keyboard" admin section - still no luck.

Edgy would have some issues that the keyboard mapping might change if i were using some remote X windows on a local desktop, or sometimes if I used Java applications - but with upgrade to Feisty it is no instant, so my system is not usable.

Does anyone know enough about the Gnome start up to give me some pointer on where there are any scripts etc. so that when Gnome it changes the keyboard mappings?

Any help would be appreciated.

Many thanks
Sean

---

### Post by koojak on 2007-05-01
After a scratch install of Feisty, and the instructions to install Sunray 3.1.1 at [http://wiki.sun-rays.org/index.php/Sun_Ray_on_Ubuntu#SRSS_on_Ubuntu](http://wiki.sun-rays.org/index.php/Sun_Ray_on_Ubuntu#SRSS_on_Ubuntu) I ran into the same problem.
I wonder if there is a relation with the vnc issues [http://ubuntuforums.org/showthread.php?t=382441](http://ubuntuforums.org/showthread.php?t=382441)

Thanks and regards

Koos

---

### Post by koojak on 2007-05-19
Hello,

the solution given at [http://www.mail-archive.com/sunray-users@filibeto.org/msg06588.html](http://www.mail-archive.com/sunray-users@filibeto.org/msg06588.html) solved my problem.

best regards 

Koos

---

