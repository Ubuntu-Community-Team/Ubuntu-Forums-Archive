---
title: "Konqueror dont save view profile for all folders"
date: 2005-10-20
forum: Desktop Environments
---

### Post by einKI on 2005-10-20
Hi

I started konqueror and switched in view->view mode->detailed list view to the detailed view. Go to Settings and save the File Manager View Profile.

Now when i start konqueror for example with Alt+F2 "~" all apperas to be correct. But when i for example type into the location bar "media:/hda8"
I get the old "Icon View" style 
When I then go to "~" again there is also the "Icon View" style.
The only way to get back the detailed view is to restart konqueror or set it in the menu.

Is there a way to general use the detailed view independent of the directory i am in or if it as a network folder or something else?

thy
by
Lukas

---

### Post by SadaraX on 2005-12-09
I have this same problem. Has anyone found a solution to the problem?

---

### Post by chris_pmf on 2006-01-04
Hello,

I've the same Problem for the media:/ io-slave. Everywhere my profile loads just fine except in media:/* locations.

Has anybody a solution?

Thanks

---

### Post by SadaraX on 2006-01-04
I found two ways of getting around this problem. I use a application shortcut for 'kfmclient openProfile filemanagement' which opens a normal konqueror window. Then I do whatever settings and I want then save them under "Kubuntu File Manager" 

This will work fairly well. You cannot change the filename which you save the filemanager profile as. It must be Kubuntu File Manager. 

If the filemanager does not work, you can use the webbrowsing profile and save that as Kubuntu Web.

---

### Post by chris_pmf on 2006-01-04
Mhh, thanks but this doesn't work for me, maybe because I use the german translation!?

---

### Post by amarra on 2006-07-25
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

### Post by chris_pmf on 2006-07-25
Thanks, works! :)

---

### Post by maheshjagadeesan on 2006-10-13
> **SadaraX said:**
> I found two ways of getting around this problem. I use a application shortcut for 'kfmclient openProfile filemanagement' which opens a normal konqueror window. Then I do whatever settings and I want then save them under "Kubuntu File Manager" 

This will work fairly well. You cannot change the filename which you save the filemanager profile as. It must be Kubuntu File Manager. 

If the filemanager does not work, you can use the webbrowsing profile and save that as Kubuntu Web.
SadaraX, your second solution works like a charm!

---

