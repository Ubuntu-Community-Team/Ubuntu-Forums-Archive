---
title: "Customizing Ubuntu 14.04 to Look like Ubuntu 10.04"
date: 2015-08-25
forum: Desktop Environments
---

### Post by ruzekle on 2015-08-25
I would like to change Ubuntu's icons to the older Ubuntu 10.04 version. There ought to be an archive folder somewhere that I can just clone. But I'm not sure how to do this. Anyone know how or can give me a tutorial on how to do it?

---

### Post by Frogs Hair on 2015-08-25
Moved to Desktop Environments

Visit Link: 

[http://www.webupd8.org/2014/04/how-to-install-and-tweak-gnome.html](http://www.webupd8.org/2014/04/how-to-install-and-tweak-gnome.html)

---

### Post by v3.xx on 2015-08-25
You may also find this interesting

[https://ubuntu-mate.community/t/can-you-tell-the-difference-ubuntu-mate-vs-ubuntu-11-04/2119](https://ubuntu-mate.community/t/can-you-tell-the-difference-ubuntu-mate-vs-ubuntu-11-04/2119)

---

### Post by ajgreeny on 2015-08-25
Why not try one of the other more traditional DEs?

Mate is a fork of gnome 2, and xfce (ie Xubuntu) acts much more like gnome 2 than the attempted version suggested in that link, in my opinion, and I believe it is now the best of the bunch.

Of course, you are free to disagree.

---

### Post by ruzekle on 2015-08-25
> **v3.xx said:**
> You may also find this interesting  [https://ubuntu-mate.community/t/can-you-tell-the-difference-ubuntu-mate-vs-ubuntu-11-04/2119](https://ubuntu-mate.community/t/can-you-tell-the-difference-ubuntu-mate-vs-ubuntu-11-04/2119)  Good find. I do enjoy Ubuntu Mate; however, there is a system breaking bug that effects nvidia users. :(

---

### Post by v3.xx on 2015-08-25
Nvidia user here and not aware of this bug.  Maybe your referring to a particular driver bug.

---

### Post by ruzekle on 2015-08-25
Could be. I will test other drivers to see what may be the issue.

---

### Post by Dennis N on 2015-08-25
> **ruzekle said:**
> I would like to change Ubuntu's icons to the older Ubuntu 10.04 version. There ought to be an archive folder somewhere that I can just clone. But I'm not sure how to do this. Anyone know how or can give me a tutorial on how to do it?

Humanity, or Humanity Dark (for dark panel background) should be authentic. Installed was version 0.5.2.1

Download:  [https://launchpad.net/ubuntu/maverick/i386/humanity-icon-theme/0.5.2.1](https://launchpad.net/ubuntu/maverick/i386/humanity-icon-theme/0.5.2.1)

says maverick, but the same version is on 10.04.

---

### Post by ruzekle on 2015-08-26
> Nvidia user here and not aware of this bug. Maybe your referring to a particular driver bug.   I tried reinstalling Ubuntu Mate with the tested nvidia driver with the one tested. I will now try installing with other drivers. I will keep you posted.  > **Dennis N said:**
> Humanity, or Humanity Dark (for dark panel background) should be authentic. Installed was version 0.5.2.1  Download:  [https://launchpad.net/ubuntu/maverick/i386/humanity-icon-theme/0.5.2.1](https://launchpad.net/ubuntu/maverick/i386/humanity-icon-theme/0.5.2.1)  says maverick, but the same version is on 10.04.  Thanks! This is exactly what I wanted. :)   --- UPDATE:  The bug is found here. [http://askubuntu.com/questions/603398/what-is-0-4486641-acpi-pcc-probe-failed-starting-version-219](http://askubuntu.com/questions/603398/what-is-0-4486641-acpi-pcc-probe-failed-starting-version-219)  I could not get beyond the issue, so I'm going with Xubuntu for now. ----- UPDATE: The bug exists on Xubuntu too. At least I know now that this is an overall issue with Systemd and Ubuntu. I am going back to Debian 8. @_@

---

### Post by Dennis N on 2015-08-26
> **ruzekle said:**
> I tried reinstalling Ubuntu Mate with the tested nvidia driver with the one tested. I will now try installing with other drivers. I will keep you posted.    Thanks! This is exactly what I wanted. :)   --- UPDATE:  The bug is found here. [http://askubuntu.com/questions/603398/what-is-0-4486641-acpi-pcc-probe-failed-starting-version-219](http://askubuntu.com/questions/603398/what-is-0-4486641-acpi-pcc-probe-failed-starting-version-219)  I could not get beyond the issue, so I'm going with Xubuntu for now. ----- UPDATE: The bug exists on Xubuntu too. At least I know now that this is an overall issue with Systemd and Ubuntu. I am going back to Debian 8. @_@

The "acpi pcc probe failed - starting version 219" message is from systemd and kernel 3.19. Nothing to do with the particular Ubuntu flavor you are using. Use a 14.04 release and it won't happen.

I get the same message on one of my computers, but it does not stop the system from loading and working normally in my case. It is fixed, I think, in the upcoming 15.10 releases as far as I can see.

---

