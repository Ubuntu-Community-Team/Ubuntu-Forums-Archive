---
title: "Windows XP won't boot after using ntfs-3g"
date: 2007-12-28
forum: Desktop Environments
---

### Post by roytang on 2007-12-28
Hi,

Sorry if this in the wrong forum, if so kindly redirect me as to where I can ask this.

I installed Kubuntu Feisty from a Live CD and downloaded and used the ntfs-3g driver to access my Windows drives. Everything is fine on the Kubuntu side, but now XP refuses to boot! I get a bluescreen message that says something like I need to remove any additional drives that have been added or run CHKDSK /F (no drives have been added)

I have backups of most stuff of course, but I'd still like to be able to boot back into XP. Is there a way to salvage the existing XP installation, or am I doomed to a reinstall?

Also, if I do this again, what should I do to avoid this problem?

If it helps, the line I added to fstab was:
/dev/hdb1       /media/c        ntfs    defaults,nls=utf8,umask=007,gid=46 0 1

Thanks,

Roy

---

### Post by kelbizzle on 2007-12-29
Run CHKDSK /F from a prompt and fix any errors you may have caused writing to your drive. [How to use the Windows recovery console.]("http://www.computerhope.com/issues/ch000627.htm")

---

### Post by Saubazi on 2007-12-29
apart from that your line in fstab says ntfs not ntfs-3g so with that entry writing will 
lead to tears...

---

### Post by roytang on 2007-12-29
Oops, it's a typo. This is the one in my fstab:

/dev/hdb1       /media/c        ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0                                                                                                    1
/dev/hdb5       /media/d        ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0            

BTW, even if the NTFS partitions are not mounted on boot, I can still mount them in the gnome file manager. Does it use ntfs-3g also?

---

### Post by roytang on 2007-12-29
Is there a way for me to evoke CHKDSK from within Ubuntu?

Unfortunately my DVD drive has a problem that it cannot read CD-ROMs, so I can't access my Windows installer disc from there :(

---

