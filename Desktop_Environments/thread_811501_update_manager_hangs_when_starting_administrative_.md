---
title: "update manager hangs when starting administrative application"
date: 2008-05-29
forum: Desktop Environments
---

### Post by hasplu on 2008-05-29
Hi all,

I have a strange problem with mu update manager - the orange star, that sties in the panel next to the clock, shows there are several updates available. When right click an choose show updates everything is ok, the update manager starts and show the available updates, but when I click on install updates whether on the star or in the update manager menu, a window administrative application appears for a few seconds and disappears without letting me enter my pass.As a result the update manager hangs and I have to kill the process manually. 
I tried running sudo apt-get update from a terminal, it check the repositories and finishes as there is no update available for me.

  It seems very much as this thread 

[http://ubuntuforums.org/showthread.php?t=756661&highlight=update+manager+hangs+starting+administrative](http://ubuntuforums.org/showthread.php?t=756661&highlight=update+manager+hangs+starting+administrative)

any ideas?
cheers:)

---

### Post by jimbreslauer on 2008-05-29
I had a similar problem that I traced to my /etc/hosts file. This thread helped me fix it.

[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

After I rebooted, my update manager worked properly.

---

### Post by hasplu on 2008-05-30
Hey, that fixed it! :guitar: Thanks a lot, man 
Cheers:)

---

### Post by billo38 on 2008-05-30
Some time after installing 8.04 and successfully installing several updates, Update Manager now hangs with "The list of changes is not available yet.  Please try again later." displayed under "Changes".  I cannot close the application and must kill all the processes involved in running the Update Manager. Any suggestions?

Bill

---

