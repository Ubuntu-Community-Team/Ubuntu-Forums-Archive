---
title: "Reinstalling Ubuntu with dual OS"
date: 2009-05-25
forum: General Help
---

### Post by Sentience on 2009-05-25
How do I reinstall Ubuntu over my old version of it without also having to reinstall windows first?

Do I have to delete the partition first?

---

### Post by merlinus on 2009-05-25
The partitioner on the install cd will give you the option of where to install the new version.  Select manual, and format (ext3 or ext4), and mount point (/).  It will replace the existing version.

Just make sure not to format your windows partition, and be sure to back up your data files.

If you have a separate partition for home, do not format that either.

---

