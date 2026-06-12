---
title: "Where is gnome-panel-add?"
date: 2011-09-14
forum: Desktop Environments
---

### Post by cwhittier on 2011-09-14
I am trying to add a launcher from the command line. Multiple post say to use the /usr/lib/gnome-panel-add script, but this does not exist on 9.04 or 9.10. It's mentioned in the release notes in both releases when I google it, but I have no idea where i'm supposed to find it. Can anyone tell me?

---

### Post by raja.genupula on 2011-09-14
> **cwhittier said:**
> I am trying to add a launcher from the command line. Multiple post say to use the /usr/lib/gnome-panel-add script, but this does not exist on 9.04 or 9.10. It's mentioned in the release notes in both releases when I google it, but I have no idea where i'm supposed to find it. Can anyone tell me?

```
locate  gnome-panel-add
```
will gives the location of that 
all the best

---

### Post by cwhittier on 2011-09-15
locate comes up blank, which would tell me its not on my system, but the change logs I found online reference it, so I don't know what to think. 

I've actually found another way to solve my original issue, which is outside the scope of this thread, but I will leave this open for a little while longer, as I am still interested in what the situation is here.

---

### Post by raja.genupula on 2011-09-15
[http://ubuntuforums.org/showthread.php?t=279751](http://ubuntuforums.org/showthread.php?t=279751)

---

### Post by cwhittier on 2011-09-16
I appreciate the link, but that thread doesn't contain any answers to my question. That's just someone else looking to make a bash script, and nobody answered him how to do it.

Regardless, I found a solution. If you have desktop files or 'launchers' created already, you can use the script provided in the following link, to add them. Be weary however, if for some reason the panel you are adding to currently has no other objects on it, this script will not work right, because it wants to append a comma to the existing list, assuming there are items already in it. You'll have to modify it not to do that.

[http://blogs.warwick.ac.uk/mikewillis/entry/add_application_launcher](http://blogs.warwick.ac.uk/mikewillis/entry/add_application_launcher)

---

