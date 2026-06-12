---
title: "Help with HDD?"
date: 2009-02-26
forum: General Help
---

### Post by fedex14 on 2009-02-26
>	im using ubuntu from live cd, to backup data from a laptop that has got windows not wanting to boot, so i start ubuntu and go to computer and when trying to access the HDD it gives an error, so I followed some comands:
        
>         sudo /bin/bash
	mkdir /media/disk
	mount -t ntfs-3g /dev/sda1 /media/disk -o force

from a [webpage]("http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/") that had this tutorial to backup windows data, but it gives me an error, saying that the NTFS has inconsistencies, may be hardware error, error of entrance/exit or sth like that, sth about softraid/fast/raid, to use chkdsk from win which i cant access...

what can i do? any command? i don't know much about linux, but manage correctly with computers.

---

