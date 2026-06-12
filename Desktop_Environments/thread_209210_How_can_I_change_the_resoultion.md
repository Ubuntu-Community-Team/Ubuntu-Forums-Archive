---
title: "How can I change the resoultion?"
date: 2006-07-04
forum: Desktop Environments
---

### Post by Dooq on 2006-07-04
the max resoultion in My Kubuntu 6.06 LTD is 1024X7~~
I need to add new resoultion.My perfict resoultion is 1024X854 How can I add it to the choice?

---

### Post by atoponce on 2006-07-04
[quote=Dooq]the max resoultion in My Kubuntu 6.06 LTD is 1024X7~~
I need to add new resoultion.My perfict resoultion is 1024X854 How can I add it to the choice?[/quote] A couple of ways.  You can manually add it to your xorg.conf file, or you can run in the terminal:

```
sudo dpkg-reconfigure xserver-xorg
``` 
...and make sure you select it as a choice when going through the options

---

### Post by Dooq on 2006-07-16
I did the two way but the new resolution wasn't in the choice again.
:confused: 
the resolution I need is 1024*854

---

