---
title: "Trying to uninstall AVAST but having some problems."
date: 2009-02-19
forum: General Help
---

### Post by sotvomike on 2009-02-19
Ok, so I found a thread in here already addressing this, but where they solved the issue, I just keep getting more errors.  Here's what the terminal is telling me:

sotvomike@sotvomike-laptop:~$ sudo dpkg --force-remove-reinstreq --remove avast4workstation
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 122187 files and directories currently installed.)
Removing avast4workstation ...
/var/lib/dpkg/info/avast4workstation.prerm: 4: /usr/lib/avast4workstation/share/avast/desktop/install-desktop-entries.sh: not found
dpkg: error processing avast4workstation (--remove):
 subprocess pre-removal script returned error exit status 127
/var/lib/dpkg/info/avast4workstation.postinst: 4: /usr/lib/avast4workstation/share/avast/desktop/install-desktop-entries.sh: not found
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 avast4workstation

So, anybody have any idea what can be done about this?  I tried to reinstall like it says, but that runs into its own set of problems as well.

Mike

---

### Post by konqueror7 on 2009-02-19
the last time i unistalled avast when i was in hardy, i just issued this in the terminal
```
sudo apt-get autoremove --purge avast4workstation
```
after that, all is well, see if it works for you..

---

### Post by sotvomike on 2009-02-21
Anyone?  No one at all?

---

### Post by Bablefish on 2009-02-21
I had Avast installed, and all I did to remove it was head on over to the Synaptic package manager.

---

### Post by sotvomike on 2009-02-25
Thanks for the advice guys.  Well, I tried both going to the Synaptic Manager and using the purge terminal command.  Both instances I got this message:

E: The package avast4workstation needs to be reinstalled, but I can't find an archive for it.

It's the same thing every time.  Any ideas?

---

### Post by mmccan02 on 2011-01-09
I know that this thread is almost 2 years old, but since it's one of the first hits on Google, I want to share my success story:

After playing with this issue on & off for two weeks -- and finally drawing the line when I couldn't even open Synaptic, Update Manager, etc. -- I cluged together some scary ways to fix it:

All of this was done in a terminal:
cd /var/lib/dpkg/info/
sudo rm avast4workstation*
sudo dpkg --remove --force-remove-reinstreq avast4workstation

I got an interesting message that I should really reinstall before deleting, and that the package was missing its files, but hallejulah it worked!  I can now run apt-get, synaptic, update manager, etc. without issue.

I hope that this helps anyone else in this predicament.

--Melanie

---

