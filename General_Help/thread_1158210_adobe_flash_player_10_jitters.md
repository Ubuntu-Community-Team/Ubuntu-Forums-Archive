---
title: "adobe flash player 10 jitters"
date: 2009-05-13
forum: General Help
---

### Post by Ceiber Boy on 2009-05-13
Hello Everyone

i have just upgraded to Ubuntu 9.04. having done this my adobe flash player 10 jitters, and keeps buffering in full screen mode, whilst using BBC iplayer and youtube. my internet connection is broardband that is fast enough to support these sights/

i did not have this problem using ubuntu 8. therefore assuming that this problem is due to the upgrade. dose anyone else experiance this problem, or know how to fix it?

---

### Post by Tipped OuT on 2009-05-13
I had a similar problem before too. I just un-installed all of the flash packages that there were on Ubuntu, and installed Adobes Flash Player again. Do you need a guide for that?

---

### Post by Ceiber Boy on 2009-05-13
I did try reinstalling, but that did not fix the problem. when one goes to the adobe web sight, and pull down the drop down menu for which distribution of Linux you are using it has ubuntu 8 listed but not 9.04!

dose adobe need to then make their flash player compatible with ubuntu 9.04?

---

### Post by Ceiber Boy on 2009-05-13
I searched for flash and installed the supporting adobe software (which consisted of two additional boxes).

but nothing else.

unfortunately i still have the problem

---

### Post by lovinglinux on 2009-05-13
> **Ceiber Boy said:**
> I did try reinstalling, but that did not fix the problem. when one goes to the adobe web sight, and pull down the drop down menu for which distribution of Linux you are using it has ubuntu 8 listed but not 9.04!

dose adobe need to then make their flash player compatible with ubuntu 9.04?

Open a terminal from "Applications >> Accessories >> Terminal", then type the following code and hit enter:

```
sudo apt-get install flashplugin-installer
```

---

### Post by lovinglinux on 2009-05-13
EDIT: oops, replied to the wrong person.

---

### Post by Ceiber Boy on 2009-05-13
From the terminal

[sudo] password for laptop: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
laptop@laptop-laptop:~$ 

would it be best to un-install first?

---

### Post by lovinglinux on 2009-05-13
> **Ceiber Boy said:**
> From the terminal

[sudo] password for laptop: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
laptop@laptop-laptop:~$ 

would it be best to un-install first?

Not necessary. The flash plugin is already installed and un-installing won't fix your problem. There are several threads about these issues. Check it out [here](http://www.google.com/search?q=flash+problem+9.04+site%3Aubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0) and [here](http://www.google.com/search?q=flash+problem+Jaunty+site%3Aubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0).

---

### Post by Ceiber Boy on 2009-05-13
these are related subjects, but still can't find the answer of why it jitters, and even fails in full screen mode!

---

