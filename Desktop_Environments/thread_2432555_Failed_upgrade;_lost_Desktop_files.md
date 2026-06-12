---
title: "Failed upgrade; lost Desktop files"
date: 2019-12-04
forum: Desktop Environments
---

### Post by David_OConnor on 2019-12-04
Hi. I attempted to upgrade to Ubuntu 19.10 from 1904 using `sudo apt dist-upgrade`. It failed part way through ( I don't remember the error), and now all my Desktop files are gone, including some important ones. Any ideas? I just want the files back. This doesn't appear to be the issue where you reassign Desktop folders via a XDG config. Is there somewhere the upgrader would have sequestered the files? Thanks.

---

### Post by deadflowr on 2019-12-04
Are the files still in ~/Desktop? It's unclear if you lost the files on the Desktop or the Desktop folder itself.
BTW, that command doesn't upgrade releases on it's own, you'd only be able to do with that if you manipulated the repository sources as well.

---

### Post by David_OConnor on 2019-12-04
The files are not in ~/Desktop. Lost the files, not the folder; the folder continued to work, but I lost every file on it. No other files appear to have been affected.

---

### Post by bernard010 on 2019-12-13
Did it make a folder in [or next to] your home folder?         /home/

---

### Post by GhX6GZMB on 2019-12-15
Always do a settings backup before upgrading. I use Timeshift, and it's very reliable. Too late now, sorry....

---

