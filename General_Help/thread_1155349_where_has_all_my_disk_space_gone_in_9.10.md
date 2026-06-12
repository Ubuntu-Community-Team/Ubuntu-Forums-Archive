---
title: "where has all my disk space gone in 9.10?"
date: 2009-05-10
forum: General Help
---

### Post by axel_2078 on 2009-05-10
I just installed Ubuntu 9.10 (fresh install) on my laptop about a week ago. I have a 140 GB hard drive and let Ubuntu use the whole thing during the install. Since then, I've installed some package updates as well as some other programs such as virtualbox. A few days ago, I created three VMs in virtualbox. One was 40 GB and the other two were 10 GB each.  I deleted everything out of the Virtualbox hidden folder in my /home directory. However, I still seem to be missing all the space that was taken by the VMs. When I run disk usage analyzer, it shows I'm using 44.8% or 63.1 GB of my hard drive. How could this be??? Surely Ubuntu, a few packages from Synaptic, and some updates couldn't take up 63.1 GB of space! What's going on here?

---

### Post by drs305 on 2009-05-10
It sounds like your trash may still be in your trash bin, where it continues to take up space. Your trash is located in $HOME/.local/share/Trash/files. If you use a file browser, use SHIFT-DELETE to get rid of it or it will remain in the folder. Of course, the default method is to right click the Trash icon and empty it that way.

You may also have root trash, which doesn't empty with your normal trash. Delete it the same way, with a file browser, but you need to do it as root:
```
gksudo nautilus /root/.local/share/Trash/files
```

I wrote a pretty comprehensive guide on finding out why free space has disappeared:
[https://help.ubuntu.com/community/RecoverLostDiskSpace]("https://help.ubuntu.com/community/RecoverLostDiskSpace")

---

### Post by axel_2078 on 2009-05-10
> **drs305 said:**
> It sounds like your trash may still be in your trash bin, where it continues to take up space. Your trash is located in $HOME/.local/share/Trash/files. If you use a file browser, use SHIFT-DELETE to get rid of it or it will remain in the folder. Of course, the default method is to right click the Trash icon and empty it that way.

You may also have root trash, which doesn't empty with your normal trash. Delete it the same way, with a file browser, but you need to do it as root:
```
gksudo nautilus /root/.local/share/Trash/files
```

I wrote a pretty comprehensive guide on finding out why free space has disappeared:
[https://help.ubuntu.com/community/RecoverLostDiskSpace]("https://help.ubuntu.com/community/RecoverLostDiskSpace")

You hit the nail on the head. I didn't even think about that crap being in my recycle bin. The icon is so small that I forget it's even there. Once I emptied everything out, disk usage analyzer reports that I'm using 4.3%, or 6.0 GB of my hard drive. I feel like such a noob. #-o

---

