---
title: "[SOLVED] link to location"
date: 2008-05-04
forum: Desktop Environments
---

### Post by computx on 2008-05-04
Since I upgraded to hardy, making a link to a location on the desktop has issues. 
I have a mounted partition at /mnt/mountpoint.
I can create the link with a location of /mnt/mountpoint

but when I click on the link on the desktop i get 
Couldn't display "/mnt/mountpoint".
There is no application installed for this file type

Is there a new incantation I need to use when entering the location? It worked fine in fiesty.
Searching the forums hasn't helped on this one.

---

### Post by John_T on 2008-06-15
I wonder, do you have another, non Hardy machine to confirm that it's not a purely 8.04 issue?

I had similar problems, and was checking all the Hardy upgrade threads, only to discover that my wife's 7.10 desktop is now exhibiting the same symptoms.  Probably my own fault for (generally) applying upgrades with the "what could possibly go wrong?" attitude? :(

I've a post over in [another thread]("http://ubuntuforums.org/showpost.php?p=5189774&postcount=18") about it, which shows the same error message for a slightly different situation.

---

### Post by prshah on 2008-06-15
> **computx said:**
> Couldn't display "/mnt/mountpoint".



Don't create a link; instead, create a shortcut (Launcher) ```
file:///mnt/mountpoint
```

---

### Post by computx on 2008-06-15
Yes I discovered that now you need to use the file://location format. Before 8.04 I could leave out the file:// part and it still worked. I suppose it is due to the new gnome version. Nothing wrong with the file:// format but it is a bit irritating to have used the old method since early 1.x gnome and now have that functionality removed without the change being noted anywhere. Maybe it was a security issue. I have no idea why someone would remove it otherwise.

---

### Post by prshah on 2008-06-15
> **computx said:**
> Yes I discovered that now you need to use the file://location format. 


OK! Please mark the thread solved; click on "Thread Tools" _near_ the top right hand side of the page, then select "Mark Thread as Solved".

---

