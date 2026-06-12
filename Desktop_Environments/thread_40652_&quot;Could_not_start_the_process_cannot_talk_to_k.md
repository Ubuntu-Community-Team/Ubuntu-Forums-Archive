---
title: "&quot;Could not start the process cannot talk to klauncher&quot; message error"
date: 2005-06-09
forum: Desktop Environments
---

### Post by Peter Alien on 2005-06-09
Many times when i log off from KDE 3.4, it appears this message:

"Could not start the process cannot talk to klauncher"


Can anyone tell me what this message means, and how to fix it ?


Many thanks

---

### Post by Sav on 2005-06-10
[QUOTE=Peter Alien]Many times when i log off from KDE 3.4, it appears this message:

"Could not start the process cannot talk to klauncher"


Can anyone tell me what this message means, and how to fix it ?


Many thanks[/QUOTE]

Same problem.
I tried to change the permissions to the klauncher file, but even as root I can't perform the operation.

---

### Post by Peter Alien on 2005-06-12
Anyone knows how-to ?

---

### Post by Altmenorg on 2005-07-19
[QUOTE=Peter Alien]Anyone knows how-to ?[/QUOTE]
 A bit late, but I had the same erreor message and found a solution that worked for me...

Go in "/home/youusername/.kde/share/config/session"

The files are saved when you logoff and are the list of files to launch next boot...

I had a file that was "Kwin-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"

I removed that file, killed the process (sudo killall kwin), rebooted, and now everything is working fine.

---

### Post by d4n on 2005-08-25
I tried this but no change. It just creates the kwin-xxxxxxxxxxxxxxxxxxxxx file again I find. Any other ideas?

---

