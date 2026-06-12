---
title: "tactical ops on linux"
date: 2008-10-05
forum: Gaming &amp; Leisure
---

### Post by Sponzenbroekske on 2008-10-05
I got the European version and I want to install it under linux ubuntu 8.04
Offcourse I get an error else I wouldn't be here :)

MY ACTIONS (and those of yakuake :p)
yannick@asus:~$ sudo sh ./tacticalops-3.1.9-install-x86.run
Verifying archive integrity... All good.
Uncompressing Tactical Ops: Assault On Terror for Linux (European Version)............................................................................

Extracting Tactical Ops files
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
mv: cannot move `/tmp/selfgz6924/fail/tacticalops' to `TACTICALOPS_SETUP/bin/Linux/x86/glibc-2.1/tacticalops': No such file or directory
mv: cannot move `/tmp/selfgz6924/fail/ucc' to `TACTICALOPS_SETUP/bin/Linux/x86/glibc-2.1/ucc': No such file or directory
[B]Unable to find file 'System'
Unable to find file 'TacticalOps'
Unable to find file 'Web'[/B]
[B]wine: cannot find '/tmp/ravage/i5comp.exe'
Could not load Mozilla. HTML rendering will be disabled.[/B]
[B]wine: configuration in '/tmp/selfgz6924/wine/.wine' has been updated.
wine: could not load L"Z:\\tmp\\ravage\\i5comp.exe": Module not found
wine: could not load L"Z:\\tmp\\ravage\\i5comp.exe": Module not found
wine: could not load L"Z:\\tmp\\ravage\\i5comp.exe": Module not found
wine: could not load L"Z:\\tmp\\ravage\\i5comp.exe": Module not found
uninstall: dynamic-link.h:57: elf_get_dynamic_info: Assertion `! "bad dynamic tag"' failed.[/B]
Aborted
setupdb-bin.kbdmhb: dynamic-link.h:57: elf_get_dynamic_info: Assertion `! "bad dynamic tag"' failed.
Aborted

yannick@asus:~$ tacticalops
dirname: missing operand
Try `dirname --help' for more information.
Creating directory /home/yannick/.TacticalOps/System
Couldn't run Tactical Ops: Assault On Terror (to-bin). Is TO_DATA_PATH set?


you can see there are several things not working

I also tried

export WINE_EXEC=/usr/bin/wine
sudo sh ./tacticalops-3.1.9-install-x86.run

but with the same result

If anybody can help, that would be appreciated

---

