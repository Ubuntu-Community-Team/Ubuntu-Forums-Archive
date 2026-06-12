---
title: "Trash not visible with encrypted home folder."
date: 2007-12-08
forum: Desktop Environments
---

### Post by musther on 2007-12-08
I've got an encrypted home folder, I mount /home/musther.encrypted to /home/musther via encfs to achieve this.

When I send items to trash, they go to /home/musther/.trash as they should, but the applet on the panel still says there are no items in the trash.  I can only assume that this issue is due to the encryption, maybe the applet doesn't follow the fuse mount and sees that there's actually nothing at /home/musther/.trash?

Any ideas?

---

