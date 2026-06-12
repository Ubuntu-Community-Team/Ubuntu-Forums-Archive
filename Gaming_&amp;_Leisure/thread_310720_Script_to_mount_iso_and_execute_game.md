---
title: "Script to mount iso and execute game"
date: 2006-12-01
forum: Gaming &amp; Leisure
---

### Post by HeavyAl on 2006-12-01
Hey All,

I tried to write a script that allows me to mount my starcraft iso, then run starcraft (via wine) and then unmount it all without having to type it in every time but the problem is that starcraft starts to kick off before I get asked for the password to mount the iso thus causing it to fail with the 'cannot find cd' dialog.

Heres what I've got:

```

#!/bin/bash
gksudo mount "/home/me/.wine/drive_c/Program Files/Starcraft/BROODWAR.iso" /media/fakedrv -o loop
wine "/home/me/.wine/drive_c/Program Files/Starcraft/starcraft.exe"
gksudo umount /media/fakedrv

```

So what am I missing? Do I need to delay it somehow? Does it require some stop parameter to tell it to wait for the result of gksudo before going to the program?

Thanks for any help!

---

### Post by KingBahamut on 2006-12-01
mount command is wrong I think 

mount -o loop,ro -t iso9660 install-x86-minimal-2006.0.iso /mnt/cdrom/

You have to specify type.

---

### Post by HeavyAl on 2006-12-01
Thanks for the response but no, that command works fine from the cl. iso9660 doesn't have to be specified, mount just tries all the loop devices supported by the system when you use -o loop.

I'm sure there is some way of stopping the script after each part is executed but I haven't been able to locate it yet.

---

### Post by Ptero-4 on 2006-12-01
use the "sleep" command to delay execution in a script. Read it's manpage to see how it works.

---

### Post by HeavyAl on 2006-12-01
Hahaha! Got it .. turns out it was gksudo that was the problem. I left the quotes off the command that needed executed. Noob error. 
Thanks for the tidbit about fs type though, for some reason I forgot to even check before I posted what the actual terminal output was or I would have found this myself. Checking the fs type made me realize where the problem was occurring. 

Thanks!

---

### Post by Merffle on 2010-01-14
could someone please post the working code here?? i've been trying to get exactly this to work for days now and the poster says he got it working but doesn't show what he did :frown:

---

