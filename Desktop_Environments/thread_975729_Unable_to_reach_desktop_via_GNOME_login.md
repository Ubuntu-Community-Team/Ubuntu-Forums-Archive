---
title: "Unable to reach desktop via GNOME login"
date: 2008-11-08
forum: Desktop Environments
---

### Post by Streeterer on 2008-11-08
Since upgrading to 8.10, I have not been able to reach my desktop by logging into the GNOME login screen. To access my desktop I go to tty1 and enter "sudo /etc/init.d/gdm stop" and then "startx". This is the only way I have been able to get to my desktop. I feel like the problem has to do with GNOME not having permissions in some way but I have no idea. Also, the only way to shutdown my computer is with the shutdown command, the graphical options never work. And my computer cannot hibernate or sleep, I dont know if thats related.

Any help or ideas would be much appreciated.


--Streeterer

---

### Post by Streeterer on 2008-11-10
Are there any suggestions?

---

### Post by WSmart on 2008-11-10
What video do you have?  Lots of problems with older Nvidia and certain AMD cards, above what we normally have, because of the change to the Jockey Restricted Driver Manger.  You have to enable the Intrepid Proposed Software respositiory to get the older proprietary Nvidia drivers, and the R300 AMD is open source for now.  Not that you should have any of those problems, but it's a know set of issues.

---

### Post by Streeterer on 2008-11-10
I have an Nvidia 7900 GTGo, so it is fairly new

---

