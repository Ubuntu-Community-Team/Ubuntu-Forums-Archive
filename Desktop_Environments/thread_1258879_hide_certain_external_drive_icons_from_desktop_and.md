---
title: "hide certain external drive icons from desktop and file manager"
date: 2009-09-05
forum: Desktop Environments
---

### Post by mrwilloby on 2009-09-05
Greetings,

I'm running Xubuntu 9.04 from an external USB hard drive. My issue is that on the Desktop and in the sidebar in the File Manager an icon for 35G Volume (the external volume that is /) and an icon for File System both show up. They point to the same place.

I'd like for the OS to not create an icon for 35G Volume anywhere, including: the Desktop, the File Manager, and Places. I'd rather just access it from the shortcuts to File System.

The complication is that I don't want to turn off all icons/shortcuts for external drives, as I have a number of other ones that I connect to the machine.

(I'd also like a shortcut icon to the internal drive of the system as well, but that may be another issue.)

Any suggestions would be great. Thanks.

---

### Post by mcduck on 2009-09-06
Mount those drives through /etc/fstab (instead of automounting) and define their mount points anywhere else than inside /media.

---

### Post by mrwilloby on 2009-09-06
> **mcduck said:**
> Mount those drives through /etc/fstab (instead of automounting) and define their mount points anywhere else than inside /media.

The drive that I'm most concerned with is not mounted in /media because it is mounted at /. It still shows up everywhere with a shortcut to the volume along with the normal shortcut to "File System". They both point to the same place, which bothers me.

Thanks for the tip about any other drives, though.

---

