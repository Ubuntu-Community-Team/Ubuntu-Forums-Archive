---
title: "Xara LX error message. Need help!"
date: 2009-06-09
forum: General Help
---

### Post by GARoss on 2009-06-09
I've read other post where this error message pops up when 1st starting Xara LX & haven't seen where it has been solved;

***Deleted stale lock file /home/george/.XARA-XTREME-WX-xaralx-george***

...then the program will start after the 2nd attempt. But, what I haven't seen is any commits concerning the hot running CPU (at least 50%) when this occurs; even after exiting the program the CPU is still at 50%. The only way to stop it is to go to the System Monitor & kill the process because Xara LX is still active after the program is closed.

I've un-installed/re-installed a couple of times but no help.
I'm running Ubuntu 9.04-amd64 fully updated.
Any ideas?

---

### Post by GARoss on 2009-06-11
I think I've solved this. 
Apparently, .XARA-XTREME-WX-xaralx-george (george is the name of the computer) is a hidden file that is created when opening Xara LX but is self deleting once Xara is closed. For some reason it did not self-delete at some point in the past so, when launching Xara, it will post an error - ***Deleted stale lock file /home/george/.XARA-XTREME-WX-xaralx-george*** because it detects the un-deleted file. 

All I did was simply delete the file (.XARA-XTREME-WX-xaralx-george) while Xara was closed. With the old file deleted, Xara opens & closes without an error & the CPU is running at normal levels, too.
HTH

---

