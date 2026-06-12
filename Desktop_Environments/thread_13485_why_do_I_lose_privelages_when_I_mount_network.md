---
title: "why do I lose privelages when I mount network?"
date: 2005-01-31
forum: Desktop Environments
---

### Post by kdavison007 on 2005-01-31
I'll try to explain this the best I can.  I have a Fedora server sharing out my home drive.  "/home/kevin/media"  the smb file on the server is simple and works from my XP machine fine.  I have the writable = yes and I can write from the XP box.

However, on my Ubuntu laptop I mount on boot with fstab "//192.168.0.55/media    /home/kevin/media       smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0"

The mount sticks fine, but the folder turns into being owned by root and group root.  It is 775 permissions so I can read, but can't write from my user "kevin"  How come??  My fstab is right from the ubuntu starter guide how-to for mounting full permissions on boot.  My .smbcredentials file has my username "kevin" and the password.

---

