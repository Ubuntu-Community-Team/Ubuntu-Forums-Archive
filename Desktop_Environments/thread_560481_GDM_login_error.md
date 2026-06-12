---
title: "GDM login error"
date: 2007-09-26
forum: Desktop Environments
---

### Post by miesnerd on 2007-09-26
I knew hard drive space was an issue and I was going to take care of it, but I installed updates for a few programs, and when I logged out and logged back in, all accounts get the error message:
GDM could not write to your ahuthorization file. This could mean that you are out of disk space or that you r home directory could not be openedfor writing. In any case, it is not possible to log in. Please contact your sysytem administrator.

How do I get around this?

I would think that using a live cd like Gparted, I could make more space on other disks, but I know that wont fix the problem.

-Miesnerd

---

### Post by mcduck on 2007-09-26
Just boot into recovery mode (you can select it in Grub menu) and try to clean some disk space. That will work as 5% of disk space is reserved for root user, just for cases like this.

After booting to recovery mode the first thing I'd do to recover some disk space would be cleaning apt-get's cached package files, you can do that by running 'apt-get clean'. If that's not enough try removing some of your own files if there's anything you don't absolutely need.

Edit: if you are very this low on disk space on your root partition you are likely to get the same problem again. If possible, it might be a good idea to get more disk space for Ubuntu one way or other. If you have some extra space on other partitions or disks you could shrink them a bit and create a new partition & make that your new /home.

---

### Post by miesnerd on 2007-09-26
Thanks McDunk-
Actually apt-get clean worked exactly as I needed it to.

---

