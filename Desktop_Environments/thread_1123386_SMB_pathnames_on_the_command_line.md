---
title: "SMB pathnames on the command line"
date: 2009-04-12
forum: Desktop Environments
---

### Post by StuartN on 2009-04-12
When I open a shared SMB resource in Nautilus I get an easy file reference like smb://filestore/stuart, but when I want to refer to the same path on the command line I need to use /home/stuart/.gvfs/stuart\ on\ filestore/stuart. This is also a problem in applications like Meld that don't show SMB shares or hidden directories in the file browser, so I need to type the entire path from memory.

Is there an easier way? I was thinking of a script to mount the SMB share at /home/stuart/filestore - then Nautilus, the command line and applications like Meld would all see the same path. How should I free the share and unmount it in order to shut down?

---

