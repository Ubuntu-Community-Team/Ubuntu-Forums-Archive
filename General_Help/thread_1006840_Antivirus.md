---
title: "Antivirus"
date: 2008-12-09
forum: General Help
---

### Post by lenswipe on 2008-12-09
I know i dont need antivirus to protect ubuntu since its linux and therefore needs no antivirus but is there some program available to scan the files on it for viruses attached to them since its serving files up for windows machines via samba.


Thanks

-L

---

### Post by damis648 on 2008-12-09
ClamAV is pretty good.

---

### Post by Tamalin on 2008-12-09
I have realized that even though Linux is quite secure, that no OS is totally virus-safe.  I tried running Avast anti-virus for Linux, but It required an activation code (even though it is free), which is totally against open source.  But I couldn't find anything much better, and it seems to work fine.

---

### Post by lenswipe on 2008-12-09
> **damis648 said:**
> ClamAV is pretty good.

Isnt that for mailservers though?

-L

---

### Post by PocketDog on 2008-12-09
No, it's just an on-demand scanner. It doesn't monitor anything.

---

### Post by spcwingo on 2008-12-09
+1 on Avast.  I used it for a while on Windows before I switched to Ubuntu.  It even picked up some things that $100 worth of Norton didn't...for free!

---

### Post by mkvnmtr on 2008-12-09
There are some root kit scanners in the repositories. Search the package manager for root kits. They will make you feel better after you run them.

---

### Post by lenswipe on 2008-12-10
> **mkvnmtr said:**
> There are some root kit scanners in the repositories. Search the package manager for root kits. They will make you feel better after you run them.

ah, thanks :)


will that mess with any settings? Because its for a web/FTP/fileserver and i dont want it to mess with any settings, i only say this because i once installed a firewall on there and it screwed everything...


cheers


-L

---

