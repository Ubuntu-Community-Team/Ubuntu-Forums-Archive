---
title: "activesync for linux"
date: 2006-01-25
forum: Desktop Environments
---

### Post by metaosp on 2006-01-25
Can I sync my pocket pc with evolution?  Any activesync-equivalence on ubuntu?

---

### Post by bikeman on 2006-01-25
Well, it ain't easy, but you can get at least *most* of the functionality.  You need to use synce and multisync.  There is a how-to [here]("http://www.ubuntuforums.org/showthread.php?t=30936").

I found it difficult to follow the how-to successfully.  I eventually ended up going to the [synce page]("http://synce.sourceforge.net/synce/index.php") on sourceforge.  It seemed as if installing synce and multisync via apt-get did not get all of the packages I needed, while downloading all of them from sourceforge eventually took care of all of the dependencies.

Bottom line, I can now successfully sync my Dell Axim X5 with Evolution for contacts, tasks, and calendar.  I don't use the PPC for email, so I don't know if that will sync.  I also have not yet figured out how to get Ubuntu to see the PPC as a drive to copy files directly to it.  The how-to addresses setting up a hotplug, but I'm not there yet.

Two words of warning - if you force multisync to manually re-sync, you will get all of the items duplicated.  Also, I have only been able to get calendar items to sync if they have an alarm set.  I don't know why, but that's the way it currently works for me.  Also, I could not seem to get dccm to run (see the how-to), without first changing to its directory.  So my steps to sync are as follows:
stop firestarter (I can never sync with firestarter running)
insert PPC in base
open terminal
cd /usr/local/bin
dccm
sudo synce-serial-start
(password)
pstatus (just reads some PPC info, I use it to verify connectivity)
multisync
(opens multisync window, I click sync button)
click on terminal, ctrl-C to kill job
sudo synce-serial-abort (now you can remove PPC)
restart firestarter

This works for me every time, but I do want to add the ability to copy files to the PPC.  Good luck!

---

### Post by FerGeCo on 2006-05-28
Hey!

If you want to copy files and stuff try this how-to (worked for me)
[http://ubuntuforums.org/showthread.php?t=136257&highlight=SynCE-TrayIcon](http://ubuntuforums.org/showthread.php?t=136257&highlight=SynCE-TrayIcon)

but first read the comments (symlink has to be different if you dapper and stuff).

Hope this helps

---

