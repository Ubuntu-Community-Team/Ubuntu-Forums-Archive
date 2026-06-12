---
title: "[SOLVED] A couple of minor problems I'm having ...."
date: 2007-08-08
forum: Desktop Environments
---

### Post by TKR101010 on 2007-08-08
Howdy,

OK, I switched over to Ubunutu from XP & Vista (2 computers) about 2 weeks ago. I've been able to fix nearly all of my hardware issues (incorrect monitor resolution, sound not working, etc), but a couple of things are eluding me.

In the Sessions manager (accessing from the System menu), I have figured out how to add a program to automaticly start up when the system boots (i.e. added tomboy to the list). This works just fine on my laptop, but my desktop seems to not want to cooperate. It lets me go through the motions of adding the program to the list, but once I close the sessions manager dialog window and open it again the program I added is no longer on the list. Also, I had tried to install Beryl, but it ended up not working on the desktop, so I uninstalled it. But there's still an entry in the sessions manager for Beryl to start up at boot time. I've tried deleting it's entry from the session manager, but again it just keeps coming back.

Any ideas on how I can get the system to accept and save these changes?

Thanks in advance for any info,

TKR101010

---

### Post by YolaGP on 2007-08-08
You may have a permission problem. Go to /home/yourfolder/.config/autostart and in **properties** enable permissions for your user to create/delete files. This will help you save the changes you make in the session manager. Hope this helps.
YolaGP

---

### Post by TKR101010 on 2007-08-08
Thanks for the info :) Seems that was the problem.

---

