---
title: "CUPS Server"
date: 2009-02-26
forum: General Help
---

### Post by Knuffle on 2009-02-26
I am running a server (Ubuntu-Server edition 8.04) with a printer hooked up to it. I was wondering if anyone knows how to make it so my other computers can print through that server.

---

### Post by oldsoundguy on 2009-02-26
open your system> administration> printing.
Right click on the printer and select shared
then click on security at the top
settings
tick publish
and allow printing from the internet.

---

### Post by Knuffle on 2009-02-27
That is what everyone has told me. There are two problems with that. I have Ubuntu-Server edition with no GUI, and I don't want a GUI. The second problem is that I only want the PrintServer available to the LAN.

---

### Post by Zip247 on 2009-02-27
use the cups webgui from another pc

check out this

[http://ubuntuforums.org/showthread.php?t=310450](http://ubuntuforums.org/showthread.php?t=310450)

its old so I dont know if it will work with 8.10, but its a place to start

wdecker

---

### Post by Knuffle on 2009-02-27
Some of the steps don't work for me, such as adding cupsys to the shadow group. Some of the things it tells me to change in the config file don't exist either.

---

### Post by graphius on 2010-03-25
> **Knuffle said:**
> Some of the steps don't work for me, such as adding cupsys to the shadow group. Some of the things it tells me to change in the config file don't exist either.I just ignored what didn't work, and my printer works fine now...

---

