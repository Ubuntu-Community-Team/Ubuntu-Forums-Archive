---
title: "Anybody using Mondo with edgy"
date: 2006-11-10
forum: Desktop Environments
---

### Post by jamesr on 2006-11-10
Has anybody managed to get Mondo working with edgy. Mondo and Mindi seem to work but I cannot burn a CDR.

---

### Post by click4851 on 2007-01-23
at least your seems to work. Mine I don't know.....mindi doesn't respond to the very first question about my kernel, yes or no it just sits. Mondo seems to work, but since I have no experience with it, and without mindi I'm kinda gun shy. I also noticed in synaptic that the package "mindi-partimagehack" won't install because of a conflict with libnewt0.51 and libnewt0.52. I also can't install the latest mondo deb for the same reason, I was thinking of trying the latest debs. If I try to rollback to libnewt0.51 according to synaptic I have to uninstall the kitchen sink. ERRRRR.

---

### Post by jamesr on 2007-01-24
Hi 

There was a problem with Mondo and Mindi re UUID addressing instead of standard fstab. You cannot use the copy on the Ubuntu site nor standard Debs. A revised version has been posted on the Mondo sub site from Andre L. but because of time restraints I have been unable to test it out. But others on the mondo site have posted successes. I was hopefully going to test the system this weekend. Both a Dapper base ie equiv to my server and a Edgy base.

Where were you finding the lastest deb files?

---

### Post by click4851 on 2007-01-24
I have tried the packages in edgy and have dowloaded the debs from Debian and was going to try those, but your comment makes me wonder if its all for not. Just for giggles what was the revised version? I haven't tried the packages from Mondorescue, I know that libnewt0.51/libnewt0.52 was a conflict with Mindi.

---

### Post by click4851 on 2007-01-25
okay so heres where I'm at.....mindi 2.20-2 , mindi-busybox 1.2.2, mondo 2.20-1.1, failsafe kernel 2.4.27-3. Mindi doesn't like gksudo, likes root. Failsafe kernel should be 2.4.27-3 but when selected it comes up "/boot/vmlinuz-2.6.17-10-386". In dependency I'm missing "lvmiopversion" still trying to find that one.

---

### Post by click4851 on 2007-01-25
lvmiopversion is not missing, but for some reason mindi can't find it, it seems to be looking in my home directory, I have found lvmiopversion, but its in /sbin. I wonder if i could symlink to the correct place, has anyone had to edit mindi for reasons like this?

---

### Post by click4851 on 2007-01-26
rather than try to edit mindi, I went back and tried the Ubuntu Edgy packages but using root instead of gksudo, this time it gets past the dependancy check and trips up here:

Dividing data into several groups.................................Cannot add file ./lib/modules/2.6.17-10-386/volatile/nvidia.ko to minidir /tmp/mindilinux/5430/minidir

The files have been subdivided into 9 directories.                              Failed to fit data into several dirs.
Fatal error. Too much stuff!
 

So....anyone had to fight this dragon before?

---

### Post by Schleproque on 2007-02-14
I am having similar problems. 

Right now I am trying to solve the problem with the incompatible libnewts and the latest release.

Can you remember how you worked around that?

Thank You,
Rodney

---

