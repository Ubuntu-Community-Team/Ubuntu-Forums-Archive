---
title: "Konqueror dont save view profile for all folders"
date: 2006-07-25
forum: Desktop Environments
---

### Post by amarra on 2006-07-25
I've that annoying bug on my Kubuntu 6.06 Konqueror which doesn't remember the "view mode" I set also if I record the profile.

I've found a bug report on the KDE bug tracking system, please check on 

[http://bugs.kde.org/show_bug.cgi?id=108542](http://bugs.kde.org/show_bug.cgi?id=108542)

Comments #33, 34 and 38 are good ones.
I give here a small summary of the solutions:

a) You must use the complete KDE Control Center by launching from a terminal window the command "kcontrol" (without quotes...)

b) Then navigate the tree on the left side of the kcontrol window on "KDE Components" / "File Associations"

c) Now another tree appears on the right side of the KDE Control Center. Here select the "inode" node and then "directory", click on the "Embedding" tab and make your preferred view mode the first on the list in "Services Preference Order" by selecting it and by clicking the "Move Up" button several times.

d) Repeat the c) step for "directory-locked" and "system_directory" nodes in the right tree

e) Repeat the c) step for all nodes under the "media" node in the right tree that shows the view modes list when selected, as for example "audiocd", "camera_mounted", "hdd_mounted", etc. 
Note that you can select different "view modes" for each type of "object" in the right tree.

f) Click on the "Apply" button in the lower side of the KDE Control Center

That's all. It function very well.

I hope that this can help someone that like me get struggled by the strange Konqueror behaviour in Kubuntu.

Bye

Antonio

---

### Post by Secutor on 2008-05-06
Thanks for posting those instructions. They work for me.

---

