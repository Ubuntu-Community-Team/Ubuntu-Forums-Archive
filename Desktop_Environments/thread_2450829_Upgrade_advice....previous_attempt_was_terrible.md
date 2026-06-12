---
title: "Upgrade advice....previous attempt was terrible"
date: 2020-09-21
forum: Desktop Environments
---

### Post by DigiAngel on 2020-09-21
Topic :)  My attempt at doing an in place upgrade from 18 to 20 was disastrous.  I lost my sound card in the UI (though it showed up fine in alsamixer on the console).   And after a reboot, Chrome and Opera windows wouldn't show ( I could see the apps running in ps list thought).  I'd really rather not have to start from scratch on this machine.  I realize there's not a lot of info in this post initially...just wanting to see what every one else was doing...or maybe I should just wait for the point release.  Thanks.

---

### Post by TheFu on 2020-09-22
Just restore from the backup you made prior to the do-release-upgrade run.  Systems with lots of non-Canonical packages and many PPAs installed often have failed upgrades. Best to use your backup/restore methods to just handle the data parts after doing a fresh install of the new OS.  20.04.1 has been released.
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    **Ubuntu 20.04.1** LTS
Release:        20.04
Codename:       focal
```
I didn't do anything special to get it beside my standard weekly **apt full-upgrade** patching.

If your backups are all-or-nothing, perhaps better backups are needed?

---

### Post by DigiAngel on 2020-09-22
Ya my clonezilla full backup right before I started worked fine...and my daily and weekly backups work fine as well.  Truth be told...I think this machine went from 14 to 16 to 18?  Is there a way to tell how many revs a machine has gone from/to?  Maybe it's time to just start fresh.

---

### Post by deadflowr on 2020-09-22
> Is there a way to tell how many revs a machine has gone from/to? 
Release upgrades should be logged to the /var/log/dist-upgrade directory,

---

