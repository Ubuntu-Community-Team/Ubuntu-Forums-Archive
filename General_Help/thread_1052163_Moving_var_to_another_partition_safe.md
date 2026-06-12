---
title: "Moving /var to another partition safe?"
date: 2009-01-27
forum: General Help
---

### Post by jerome1232 on 2009-01-27
Hello, I've been doing some massive rearranging of my partitions recently and was contemplating moving /var and /tmp out to separate partitions, and sharing /tmp between OpenSuse and Ubuntu (since /tmp is cleared during the boot or shutdown process that should be fine right?)

I was going to simply create a new partition format it, mount it and Ubuntu's root partition, rsync /var/ to the new partition, remove all files under /var/, edit fstab to reflect the changes, and then boot into Ubuntu.

I've already moved out /home and shrunk my root file system by 140 GB, Everything works fine right now. Before attempting this I thought I'd search around about it first to see if my approach would work and I've stumbled on some blogs and etc... that seem to indicate moving /var won't be easy.

here's one.
[http://www.digizenstudio.com/blog/2007/06/14/watch-out-when-you-move-var-in-ubuntu/](http://www.digizenstudio.com/blog/2007/06/14/watch-out-when-you-move-var-in-ubuntu/)

This information seems to date back abit so I was wondering if anyone knew if this is still an issue.

While I see this thread is fairly recent and seems successful
[http://ubuntuforums.org/showthread.php?t=891612&page=2](http://ubuntuforums.org/showthread.php?t=891612&page=2)

---

### Post by jerome1232 on 2009-01-29
Since it seems no one that's viewed this thread has attempted this I went ahead and tried it in a virtual machine and it did indeed wreck the install. It get's errors about /var/run-lock not being a mount point and x fails to start, at which point I cannot use the keyboard and I can't get to a virtual terminal to trouble shoot because ctrl+alt+f1 takes my host os to a virtual terminal lol.

I'll think it's safe to say moving /var isn't advisable on Ubuntu.

---

