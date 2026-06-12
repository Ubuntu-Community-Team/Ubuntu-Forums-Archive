---
title: "Looking for a program repor for my pc..."
date: 2006-07-12
forum: Desktop Environments
---

### Post by carontis on 2006-07-12
Hellò. I have Ubuntu 6.06 installed, but I can't find a program that let me know exactly the hardware I have and related infos. Do you know something (like siSoft Samdra for windows) so I can have exact datas from it, or in alternative, a command to use (like the 'netsh diag gui' in windows) for collecting all those infos? Thanks to everybody...

---

### Post by T700 on 2006-07-12
Open a terminal (the command line) and type ```
sudo lshw
``` now press Enter.

Paul

---

### Post by Maggot on 2006-07-12
Not sure off of any programs.  

I looked at
[list]
[*]SYSTEM
[*]ADMINISTRATION
[*]DEVICE MANAGER
[/list] 

but its pretty useless seeing as no info is actually provided.

Alternatively you can use the following commands in a terminal:

[list]
[*]lspci
[*]lsusb
[*]dmesg | less
[/list]

Not overly friendly but might help for the moment

---

### Post by Maggot on 2006-07-12
> **T700 said:**
> Open a terminal (the command line) and type ```
sudo lshw
``` now press Enter.

Paul

Hey, cool. Thanks :cool:

---

### Post by carontis on 2006-07-12
Many thanks, T700, but the only last thing I need too, is datas about my monitor, 'cause I haven't found anything good in Internet (Samsung site). How can I do for having all datas (H-V etc) for it? There is another possible command or what? 
Thanks again

---

### Post by carontis on 2006-07-12
Thanks to you too, MAGGOT, but the problem still here, 'cause I need all datas, also those in regard to mounted printers, scanners etc (switched on) and included the monitor (I have a Samsung LCD SyncMaster 172v). I already used a program to intercept all those datas, but was simple and less technical... I need something really technical, like answer given from those commands you & T700 wrote. 
Thanks

---

