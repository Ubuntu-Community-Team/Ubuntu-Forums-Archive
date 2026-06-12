---
title: "Beryl &amp; Emerald"
date: 2006-11-07
forum: Desktop Environments
---

### Post by Bengaul on 2006-11-07
Hi,

I have been trying to install Beryl etc. on an ATI card Edgy system. All seemed to go well, but after reboot, and starting an XGL session, no 3D :confused: . 

After closer inspection it seems as if the entries for Beryl & Emerald I had put into the Gnome sessions start-up menu had disappeared. I re-entered them, closed the dialog box, then opened it again. Guess what? No entries for Beryl and Emerald! This went on for a couple of minutes! ](*,) 

Has anyone come across this issue before? Is there a text file that I can manually edit? Do I have to SU before the entry will stick? Is this just the tip of the Iceberg? 

Many thanks,

Ben.

---

### Post by Bengaul on 2006-11-07
Bump :)

---

### Post by SRParda on 2006-11-08
I'm using Beryl in edgy without problem.

But I'm using xorg with Ati open source drivers so beryl is using  aixgl extension instead.

Added to session programs 'beryl-manager' wihout problem.

Anyway executing 'beryl-manager' inside a terminal inside X started beryl and change the desktop to 3D windows at the moment.


I don't know, if xgl is using the same configuration files for the session that xorg uses. The file is configured in same place in a hidden directory in the user's home directory.
I think you must check and retrieve information about this question.

---

