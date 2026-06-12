---
title: "bash and permissions"
date: 2009-03-03
forum: General Help
---

### Post by notatoad on 2009-03-03
i wrote a little script to copy .torrent files into my watched directory when i download them

```

#!/bin/bash
cp $1 /watched/directory/

```

where /watched/directory is a local path to a folder that is actually a nfs share on my fileserver which rtorrent is running on. (i tried with options rw,all_squash and just rw in /etc/exports)

the problem is that when firefox runs the script and copies the file over, it gets no owner assigned to it, so rtorrent cannot open it.  how do i fix this?  is there a way i can set up the directory so that anything i copy into it is readable and writable by all?

---

