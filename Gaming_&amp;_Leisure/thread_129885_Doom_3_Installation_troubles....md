---
title: "Doom 3 Installation troubles..."
date: 2006-02-14
forum: Gaming &amp; Leisure
---

### Post by Ben Stamper on 2006-02-14
For some reason, when trying to paste the .pak files to the /base directory, Ubuntu will not allow me to paste them in. I copy it, it tells me that it will be copied if I use the paste command, and then the option is grayed out.

---

### Post by udha on 2006-02-15
go to a terminal and copy them with sudo cp /mnt/cdrom/filename /path/to/doom3/base/file1

If you want to use the gui you will need permissions for writing to the doom 3 base directory, as you will not have permission to write to it yet, open a terminal, and cd to the doom3 directory,

for me this is /opt/games/doom3 but it's typically /usr/local/games/doom3

then ls and note the permissions on the directory, to allow everything to it type:

chmod -R 777 base

then you should be able to paste to base folder they way you were expecting, it's recommended to set the permissions of that folder back to what they were originally once you are done.

---

### Post by Zeroedout on 2006-02-19
..... or he could just do ```
sudo nautilus
``` I'de like to think that is just more simple.

---

