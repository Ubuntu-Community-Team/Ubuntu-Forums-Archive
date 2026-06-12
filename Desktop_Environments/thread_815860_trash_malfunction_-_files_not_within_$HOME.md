---
title: "trash malfunction - files not within $HOME"
date: 2008-06-02
forum: Desktop Environments
---

### Post by kornelix on 2008-06-02
I own files on partitions other than my $HOME partition (/home/<user>) 
and I see that the trash function does not work in Nautilus. 

When I right click and select "Move to Trash" I get the useful diagnostic 
"Cannot move file to trash, do you want to delete immediately?" 
followed by the equally useful 
"The file xxxxxxxxx cannot be moved to the trash."

Is there a solution?

:confused:

---

### Post by VMC on 2008-06-02
> **kornelix said:**
> I own files on partitions other than my $HOME partition (/home/<user>) 

You create files and place them somewhere else. Is that what you mean?

Anyway, what do you have at /home/<user>/.local/share/Trash
Anything?

---

### Post by kornelix on 2008-06-02
I create them directly within directories external to /home
(partitions mounted at some other place, like /somename)
and which I am the owner of.

My   /home/<user>/.local/share/Trash  looks normal.
Files within /home/<user> can be sent to Trash normally.

I think Gnome may not be able to handle this case.
I am trying to find out if there is some secret setup
that makes it work.

---

### Post by sisco311 on 2008-06-02
> **kornelix said:**
> I create them directly within directories external to /home
(partitions mounted at some other place, like /somename)
and which I am the owner of.

My   /home/<user>/.local/share/Trash  looks normal.
Files within /home/<user> can be sent to Trash normally.

I think Gnome may not be able to handle this case.
I am trying to find out if there is some secret setup
that makes it work.

Just create a .Trash folder at the root of the partition:
```
sudo mkdir /somename/.Trash
``````
sudo chmod 1777 /somename/.Trash
```

---

### Post by kornelix on 2008-06-02
There is already a /somewhere/.Trash-<user> folder
which used to do the trash job before Hardy. 
Changing the name to .Trash makes no difference.
Also, the protection 777 seems loose. How about 700?

---

### Post by sisco311 on 2008-06-02
Delete all the .Trash folders from the partition.
Create a new one owned by root and with 1777 permissions.
```
sudo mkdir /somewhere/.Trash
sudo chmod 1777 /somewhere/.Trash 
```Now when you delete files the system will create a sub-folder, in .Trash,  according to your user id, owned by your user and with 700 permissions.

---

### Post by kornelix on 2008-06-02
Thanks, that is working better. 
How did you know this? Where should I look the next time?

---

