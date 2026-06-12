---
title: "How to re-add deleted firefox 3 file?"
date: 2008-08-03
forum: Desktop Environments
---

### Post by ArvoSukkula on 2008-08-03
I recently started encountering FF crashes on app startup. After some investigation, I identified some bad blocks on my disk. When finally running fsck I had no option but to delete the file on the bad block (something to do with xulrunner, but I unfortunately did not write the filename down). The filesystem seems to be OK now, but FF won't work due to the missing file.

So I need to be able to force reinstall of firefox (and open office, which had the other corrupt file) OR figure out what 2 files are missing and then just install those. FF has a lot of dependent packages in Ubuntu and uninstalling all of those and then reinstalling seems painful.

Any suggestions?

---

### Post by coffeecat on 2008-08-03
This sounds like a when-all-else-fails-at-your-own-risk option, but I found this in man apt-get:

> --force-yes
           Force yes; This is a dangerous option that will cause apt to
           continue without prompting if it is doing something potentially
           harmful. It should not be used except in very special situations.
           Using force-yes can potentially destroy your system! Configuration
           Item: APT::Get::force-yes.I presume you would use it as 'sudo apt-get --force-yes install packagename' but I've never had occasion to try that.

Another - perhaps less likely to be relevant:

>  -f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place.
           This option, when used with install/remove, can omit any packages
           to permit APT to deduce a likely solution. Any Package that are
           specified must completely correct the problem. The option is
           sometimes necessary when running APT for the first time; APT itself
           does not allow broken package dependencies to exist on a system. It
           is possible that a system´s dependency structure can be so corrupt
           as to require manual intervention (which usually means using
           dselect( 8 ) or dpkg --remove to eliminate some of the offending
           packages). Use of this option together with -m may produce an error
           in some situations. Configuration Item: APT::Get::Fix-Broken.And lastly, have you tried Edit > Fix Broken Packages in Synaptic? I doubt that will help but it might be worth a try.

---

### Post by ArvoSukkula on 2008-08-04
Synaptic yes. It turns out Synaptic has handy option mark for reinstallation (right click package)

It seems the missing file is libxul.so (at least xulrunner gnome support installition fails because it's missing)

Digging further...

---

### Post by ArvoSukkula on 2008-08-05
Basically all package reinstalls failed when installation script found missing files. The solution was to use synaptic to completely remove firefox 3 and xulrunner and then reinstalling them.

---

