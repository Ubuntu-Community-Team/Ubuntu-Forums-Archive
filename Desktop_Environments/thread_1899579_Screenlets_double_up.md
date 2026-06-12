---
title: "Screenlets double up"
date: 2011-12-23
forum: Desktop Environments
---

### Post by jfreak53 on 2011-12-23
Have a minor problem, my screenlets seem to be doubling up when I start gnome for the past two days.  What ever I had when I shutdown it opens double when I start the computer the next day.

Using UBU 11.04

---

### Post by Guido Tabbernuk on 2011-12-24
> **jfreak53 said:**
> Have a minor problem, my screenlets seem to be doubling up when I start gnome for the past two days.
Probably you just have to delete the instances of screenlets you do not use. Delete it from screenlet menu --- and not just close it.

---

### Post by jfreak53 on 2011-12-24
Well I just noticed this morning when I started up that it's not all that I have running.  I am using folderview and that seems to be the one that is doubling up on me when I start up.  So it's not the ones I am not using that do it, it's the single one (folderview) that I do use.  But I only have one pane on the desktop, and when I start there are double of that one single.  If I close both then restart two new still come up ha ha

So not sure.  Probably something with folderview.

---

### Post by jfreak53 on 2012-01-23
Ok, finally figured this one out, it's a problem with folderview.

In the folder ~/.config/Screenlets/FolderView/default are the INI files for folderview configuration.

For some reason the first time you start folderview it creates double INI files, and hence it starts double views when you start up.  So it's just a matter of deleting the second INI file and your good to go.

Man what a pain ha ha

---

### Post by jeepfanatic on 2012-04-27
Not sure if you're still having an issue, but I thought I'd respond anyway.  I just had a very similar problem with my screenlets - especially the Pidgin screenlet because for some reason it takes so long to startup and multiple copies just bogged down the whole thing.  

I solved it by making a copy of the correct INI files to a backup folder and running a script on login to delete the existing files, copy in the "correct" ones, and then launch the screenlets.  Haven't had a problem since.  Would prefer to NOT have to put a bandaid on but it's not that big of a hassle.

Happy to help anyone with questions about how I did this exactly - just drop me a message.

---

