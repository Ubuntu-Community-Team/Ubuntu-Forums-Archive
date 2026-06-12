---
title: "Can't find compizconfig-settings-manager!"
date: 2007-11-17
forum: Desktop Effects &amp; Customization
---

### Post by Scorpio123 on 2007-11-17
Hi there, i'm running Ubuntu 7.10 "Gutsy" and I cannot seem to find the "Compizconfig-settings-manager" so that i can install it.. I checked Synaptics, it wasn't there, i even tried in Terminal, but again it couldn't find the package..

Any idea where i can get it!? The "Extra" desktop effects seem to be working fine, but i want Compiz Fusion..

Thanks for any help!

---

### Post by oneoverzero on 2007-11-17
Make sure all the repositories are enabled.  You can do this in Synaptic under one of the preferences panels.

---

### Post by Zorael on 2007-11-17
```
zorael@azrael:~$ apt-cache policy compizconfig-settings-manager
compizconfig-settings-manager:
  Installed: 0.5.2+git20070912-0ubuntu1
  Candidate: 0.5.2+git20070912-0ubuntu1
  Version table:
 *** 0.5.2+git20070912-0ubuntu1 0
        500 http://se.archive.ubuntu.com **gutsy/universe** Packages
        100 /var/lib/dpkg/status
```

So yes, see to that your universe repositories are enabled.

---

### Post by Scorpio123 on 2007-11-17
Awesome guys, thanks a lot for the help!

Im a first time ubuntu user so i didnt really know how to do all that before heh.. nice one!

By the by, when i do the cube rotation, am i not supposed to have 4 desktops? It kinda rotates between two right now...

---

### Post by Zorael on 2007-11-17
You can set the number of desktops in General Options -> Desktop Size.

Don't touch Number of Desktops; set Horizonal Virtual Size to the number of sides you want.

---

### Post by Scorpio123 on 2007-11-17
Thanks a lot for your help mate!!

---

### Post by pat_can_vault on 2007-11-29
I am running 7.10 Gutsy Gibbon (I've ben using it for three days with no previous linux experience) and I cannot find the compizconfig-settings-manager either. I have made sure all repositories are checked, and I entered the above command in the terminal and got the message "Compizconfig-settings-manager not installed". Is there anything you could recommend? Also, would it matter if I'm not connected to the internet? Thanks in advance!

---

### Post by FilmAficionado on 2007-11-29
> **pat_can_vault said:**
> I am running 7.10 Gutsy Gibbon (I've ben using it for three days with no previous linux experience) and I cannot find the compizconfig-settings-manager either. I have made sure all repositories are checked, and I entered the above command in the terminal and got the message "Compizconfig-settings-manager not installed". Is there anything you could recommend? Also, would it matter if I'm not connected to the internet? Thanks in advance!

The command is:
sudo apt-get install compizconfig-settings-manager

AND YES, you need to be connected to the internet. Where else will it download it from, silly? The repositories that you made sure are working are repositories of files online.

---

### Post by applehead on 2007-11-29
Am I missing something here?  Don't you just go to preferences then advanced desktop settings?  Or is that something else?

---

### Post by pat_can_vault on 2007-11-30
lol, ok. I thought so. I'm having trouble connecting though... I've posted in a section like that. Thankyou.

---

