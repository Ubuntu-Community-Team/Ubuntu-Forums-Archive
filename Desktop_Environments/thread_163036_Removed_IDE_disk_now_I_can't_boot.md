---
title: "Removed IDE disk now I can't boot"
date: 2006-04-20
forum: Desktop Environments
---

### Post by osaeris on 2006-04-20
I had 3 disks in my system hda, sda, sdb.

hda was IDE primary master and was a storage area
sda and sdb are plugged into an adaptec 19160 card

Breezy is installed on sdb, sda is blank

Grub was installed on hda but unfortunately I didn't realise that when I removed it and formatted it to get more space in my other machine.

Now my machine dosen't have the grub boot menu I was hoping someone might have a suggestion for reinstating it. I don't mind backing up my home folder from a live CD and starting from scratch if all else fails.

I have tried to install grub using grub-install sda and grub-install sdb but I get an error about no BIOS device being found (I guess that's to do with the U160 card but I'm not sure).

I'm not a total newb' though you wouldn't know it doing something as stupid as this!

Any help most welcome.

Steve

---

### Post by dcstar on 2006-04-20
[QUOTE=osaeris]
.......
Now my machine dosen't have the grub boot menu I was hoping someone might have a suggestion for reinstating it. I don't mind backing up my home folder from a live CD and starting from scratch if all else fails.

I have tried to install grub using grub-install sda and grub-install sdb but I get an error about no BIOS device being found (I guess that's to do with the U160 card but I'm not sure).
......[/QUOTE]
Do a forum search for restoring Grub, there are numerous HOWTOs etc. about.

---

