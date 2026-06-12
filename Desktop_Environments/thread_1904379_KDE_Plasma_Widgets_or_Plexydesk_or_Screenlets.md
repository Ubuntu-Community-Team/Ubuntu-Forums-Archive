---
title: "KDE Plasma Widgets or Plexydesk or Screenlets??"
date: 2012-01-04
forum: Desktop Environments
---

### Post by tkabir11 on 2012-01-04
Was wondering which one is best out of the three and worth installing on Ubuntu 11.10??

---

### Post by Guido Tabbernuk on 2012-01-05
**Plexydesk** seems to be large and slow and still immature. Also there aren't too many widgets or installing them is not very straightforward. It works, yet hardly satisfies real users.

You can run **Plasmoids** on Ubuntu main edition, but it makes KDE context menu pop up from the desktop and causes some other irregularities as well as demands extra resource from your system. If you are okay with that, there are a lot of Plasmoids and they are easy to install. IMHO currently the best widget framework for Linux systems.

**Screenlets** is the only widget framework which is developed for and guaranteed to work on Ubuntu 11.10. If you install the latest 0.1.6 from Screenlets Dev PPA (ppa:screenlets-dev/ppa), everything should work fine in both Unity and GNOME shell. The problem with Screenlets is that not many new screenlets are created nowadays and some of the older ones have stopped working. However they are easy to install from PPA using Ubuntu Software Center (see [http://www.screenlets.org/index.php/Get_more_screenlets](http://www.screenlets.org/index.php/Get_more_screenlets)) and there's a Basic Pack of them distributed with the framework, which should all work all right. Rest of about 100 screenlets in PPA are of variable quality, but most of them work.

You may want to consider **Google Gadgets**, but they may not work with Unity and there's no official package since 11.04. If older Ubuntu versions do not work, you can try if some latest versions in Debian repositories work for you.

And there is also a project called **gDesklets**, which doesn't have installation package for 11.10, however I was able to install it once. It has smaller memory print than Plexydesk, but this too is quite immature. As though general usability and cooperation with desktop is a not so good as in Screenlets, gDesklets are actually usable in Ubuntu.

---

### Post by tkabir11 on 2012-01-06
Thanks for the reply. I finally decided to install the kde plasma desktop- and I gotta say it's the best desktop system I've ever seen :D I still have the option to use the unity desktop by choosing it at login- but I really don't think I'd be missing Unity that much. 
The only little problem I have with the kde desktop is that I cant open terminal from ctrl-alt-t anymore, I could only open it from the app launcher.

---

