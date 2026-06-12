---
title: "Practically no KDE apps work on my computer."
date: 2008-11-11
forum: Desktop Environments
---

### Post by BetterSense on 2008-11-11
I run Ubuntu but have Kubuntu-desktop installed for the sake of programs. After updating to Intrepid, though, several programs are broken, including lyx, kate, and konqueror. They all fail to launch, running them from a terminal, nothing happens. I was reading that lyx is currently broken under Qt 4.4 but I don't know if that has anything to do with the other programs, or how to go back to Qt 4.3 to fix Lyx, which I desperately need.

This is  what koqueror says, then just sits there:

```
chaz@singularity:~$ konqueror
konqueror(6424) KToolInvocation::klauncher: klauncher not running... launching kdeinit
kdeinit4: preparing to launch /usr/lib/kde4/libexec/klauncher
kdeinit4: preparing to launch /usr/bin/kded4
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update
kdeinit4: preparing to launch 
konqueror(6424) KonqHistoryManager::loadHistory: The history version doesn't match, aborting loading 
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update


```

This is what kate says, then just sits there:

```
chaz@singularity:~$ kate
kate(6450): createDoc
kate(6450) KateSessionManager::KateSessionManager: LOCAL SESSION DIR:  "/home/chaz/.kde/share/apps/kate/sessions"
kate(6450) KateApp::initKate: Setting KATE_PID: ' 6450 '
kate(6450) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"

```

Lyx:

```
chaz@singularity:~$ lyx

```

konsole:

```
chaz@singularity:~$ konsole

```

wtf? note that I'm actually running gnome.

---

### Post by BetterSense on 2008-11-16
I gave up trying to fix my problem and finally did a clean install of Ubuntu 8.10. Then I installed kubuntu-desktop and some other programs. 

After the installation, I had the SAME PROBLEM. From a CLEAN INSTALL of ubuntu! No KDE apps I try run, nor does Lyx, which I desperately need for work. Does this happen to every one else or what? How can this only happen to me? Could it possibly be a hardware problem? Does kubuntu-desktop like, not run on Atom processors or something? 

W.
T.
F.

I guess the next thing to do is do ANOTHER clean install of Hardy, so at least I can use my computer at work.

---

### Post by skullmunky on 2008-11-16
If you're relying on apps for production and having trouble, my advice would be to keep your production machine at 8.04 and use a testing partition, drive, or other box for testing on 8.10 and future releases with KDE4 b/c KDE4 is still evolving so rapidly.

---

