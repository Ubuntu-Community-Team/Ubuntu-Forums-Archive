---
title: "Why does Ubuntu get my DVD drives confused?"
date: 2006-10-04
forum: Desktop Environments
---

### Post by dwasifar on 2006-10-04
I have a DVD burner at /dev/hdc and a DVD reader at /dev/hdd.  Applications don't seem to be able to distinguish them correctly.  In movie players, choosing Open DVD will sometimes pick one drive, sometimes the other.  And in Gnomebaker, even though I have the BURNER selected in the preferences and in the burn dialog, when I click Burn it opens the READER, identifying it by name, and asks me to put a blank disc into it.  (Obviously the burn fails.)

My default-created /etc/fstab entry for optical drives only mounts /dev/hdc at /media/cdrom0.  I tried adding an entry for /dev/hdd at /media/cdrom1, and it mounts there, but that doesn't help matters any.

I feel like I'm missing something obvious.

---

### Post by dwasifar on 2006-10-04
bump

---

### Post by dwasifar on 2006-10-05
bump

---

### Post by deadgobby on 2006-10-05
[http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_CD.2FDVD-ROM_manually.2C_and_show_all_hidden_and_associated_files.2Ffolders](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_CD.2FDVD-ROM_manually.2C_and_show_all_hidden_and_associated_files.2Ffolders)

---

### Post by dwasifar on 2006-10-05
> **deadgobby said:**
> [http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_CD.2FDVD-ROM_manually.2C_and_show_all_hidden_and_associated_files.2Ffolders](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_CD.2FDVD-ROM_manually.2C_and_show_all_hidden_and_associated_files.2Ffolders)

Not sure why you think this will help.  I'm not having any trouble mounting the drives; the problem is that applications don't seem to be able to distinguish them consistently.

---

