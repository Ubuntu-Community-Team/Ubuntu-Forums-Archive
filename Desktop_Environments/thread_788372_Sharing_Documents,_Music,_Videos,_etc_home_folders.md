---
title: "Sharing Documents, Music, Videos, etc home folders with Windows"
date: 2008-05-09
forum: Desktop Environments
---

### Post by jcarouth on 2008-05-09
I can't seem to find an answer for this, so hopefully someone can point me in the correct direction.

I have a dual-boot system that has Hardy Heron and Windows XP SP3. The OS's are on one drive and I have a second "storage" drive that holds all my media (videos, music, pictures) and documents.

What I currently do is have the second drive mounted automatically at point /mnt/storage and then I bind the home folder directories to their appropriate counterparts on the storage drive like this:

```
sudo mount --bind /mnt/storage/music ~/Music
sudo mount --bind /mnt/storage/documents ~/Documents
...
```
I also have a "workspace" for eclipse that is on the storage drive that I would love to be able to share between the two operating systems that is located at ~/workspace.

Any advice, or is this best solution?

---

