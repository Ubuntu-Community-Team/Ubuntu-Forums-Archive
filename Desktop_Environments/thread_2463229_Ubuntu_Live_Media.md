---
title: "Ubuntu Live Media"
date: 2021-06-06
forum: Desktop Environments
---

### Post by nezcrocman on 2021-06-06
Hello, I'd like to know if the "live Media" of Ubuntu Desktop 20.04 LTS have built in, and already installed on, Powershell.
If it does not, how can we include it by default ?

Thank you

---

### Post by CatKiller on 2021-06-06
> **nezcrocman said:**
> Hello, I'd like to know if the "live Media" of Ubuntu Desktop 20.04 LTS have built in, and already installed on, Powershell. 

It doesn't. There's no reason for it to be included. 

>  If it does not, how can we include it by default ?

Installation instructions are [here](https://docs.microsoft.com/en-us/powershell/scripting/install/installing-powershell-core-on-linux). If you're really desperate to always have it in a live session, you can look at "persistence" or modifying the image.

---

### Post by nezcrocman on 2021-06-06
Thanks for the links !
How can I modify the image to include it ?

Please don't *byte* (:o) me !

---

### Post by guiverc on 2021-06-06
The easiest method is just write the ISO as a persistent image...

I use `mkusb` to write ISOs normally; the persistent wiki page being [https://help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent) , but it's not the only tool that will create them.

Writing the existing ISO that way is easier than re-creating an ISO yourself.

---

### Post by ActionParsnip on 2021-06-07
Or...install to USB. You will need 2 USB sticks (One to install from and one to install to). You can then use the entire stick as a disk rather than the 4Gb limit in the persistence

---

### Post by grahammechanical on 2021-06-07
The Ubuntu live session will allow us to change system settings and install applications but once we shutdown the live session all the changes are lost. A Ubuntu live session with persistence will make any changes persist. They are not lost when we shutdown the session. And so will an install of Ubuntu onto a USB memory stick  This is why the above posts are making these recommendation.

Regards

---

### Post by nezcrocman on 2021-06-07
Thanks All ! I'll try that !
So, to sum it up : I "mount" (please note that I'm working on an Microsoft system) the current ISO (20.04) and install it onto a USB stick. Then, from that I make changes ? Or did I lost something in between ?

---

### Post by sudodus on 2021-06-07
> **ActionParsnip said:**
> Or...install to USB. You will need 2 USB sticks (One to install from and one to install to). You can then use the entire stick as a disk rather than the 4Gb limit in the persistence

Today there are several ways to use all available drive space for persistence, for example with **mkusb** in Ubuntu and **Rufus** in Windows.

See [this link](https://askubuntu.com/questions/1181854/how-is-it-easier-to-make-a-persistent-live-drive-with-ubuntu-19-10).

---

### Post by dddman on 2021-06-07
Rufus is user friendly, worked first try for me on win10.

---

### Post by ActionParsnip on 2021-06-07
+1 for Rufus. Some people like BalenaEtcher
[h=2][/h]

---

### Post by TheFu on 2021-06-07
> **nezcrocman said:**
> Thanks All ! I'll try that !
So, to sum it up : I "mount" (please note that I'm working on an Microsoft system) the current ISO (20.04) and install it onto a USB stick. Then, from that I make changes ? Or did I lost something in between ?

If you don't go with the persistent USB install, you'll need to remaster the ISO.  ISO files are read-only no matter what media they are on - CDROM, or HDD or flash. That type of file system isn't able to be modified. We can't just mount them and modify files.  Remaster.  There used to be an Ubuntu Remaster tool that would create a CDROM/DVD from a running Ubuntu system, but when EFI came, we lots lots of utilities which were pretty great.

Or just learn to get by without powershell, since there are many already included scripting languages on the ISO which are more powerful.  Heck, I bet there's a powershell-to-X converter where X is bash, perl, python, ruby or even awk.
If a month of not using powershell, you'll not want to go back.  ;)

Most of us here are converts from other OSes.

---

### Post by nezcrocman on 2021-06-08
> **nezcrocman said:**
> 
So, to sum it up : I "mount" (please note that I'm working on an Microsoft system) the current ISO (20.04) and install it onto a USB stick. Then, from that I make changes ? Or did I lost something in between ?
In regards to that, Ive installed unbuntu, with rufus, onto a USB stick. Now what ? I need anther stick ton install the 1st onto the second ?

I don't quite get it...

---

### Post by sudodus on 2021-06-08
- If you want an installed system in a USB drive, yes, install when booted from one drive into the other drive, and then install your program package(s) (powershell, and maybe later some other package) after rebooting into the installed system.

- If you want a persistent live system, which can be created by Rufus, you can install your program package(s) directly into that [persistent live system] when booted from the [one and only] USB drive. 

[hr][/hr]
So did you create a live-only or a persistent live system onto your USB stick?

[This link](https://askubuntu.com/questions/1181854/how-is-it-easier-to-make-a-persistent-live-drive-with-ubuntu-19-10) may help you. Scroll to the paragraph about Rufus in the answer (if you want a persistent live system).

---

### Post by nezcrocman on 2021-06-09
Thanks, but I can't go without it. The script was made in that language. Basicaly, I need this tool to be run at boot to recuperate some infos.

---

### Post by sudodus on 2021-06-09
It is easy to test with a persistent live system. If you install Powershell, it will persist after shutdown and reboot. I suggest that you try that before heading for an installed system (which is more difficult to create).

---

