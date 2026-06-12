---
title: "Two desktop mgrs running?"
date: 2012-09-05
forum: Desktop Environments
---

### Post by Wombat Built For Combat on 2012-09-05
G'day - I tinkered with LXDE last night but came back to KDE, however I think I've broken something! See this picture ... :

[IMG]http://winwood.org/DesktopIssue.jpg[/IMG]

for proof of what I now get on my KDE desktop (I moved the left edge of the KDE bar to the right so you can see the LXDE bar beneath). Both bars work fine (though I can't launch anything from the LXDE one because there's no menu widget there).

So how did I get here? I did a 'sudo dpkg-reconfigure kde' thinking that would point everything back appropriately to kde and rebooted.

I've since done an 'apt-get remove lxde' and even an 'apt-get purge lxdm' with reboots in between but what you see above is what I'm left with.

Curiously the konsole session doesn't show on the KDE bar (but that might be perfectly correct for all I know - I didn't start konsole from the LXDE bar because it has no menu button to click but I note the 'snapshot' app shows on both. Hmm).

Anyone got any clues / hints as to what I need to do to *just* have KDM / KDE running? I'm obviously happy to supply other info e.g. 'ps' listings (no obvious 'lxd' entries if I grep against a 'ps -fe' though).


Many thanks in advance
Wombat

---

### Post by McNils on 2012-09-05
I have seen this behavior when I use icewm instead of kwin.

Try 
kwin --replace 
It might help you for your current situation.

---

### Post by Wombat Built For Combat on 2012-09-05
Thanks for the reply but it didn't work. I got a couple of screen flicker / flashes as the following text was churned out, and then (after about 20 mins of seeing if it would do anything else) I hit ^C noting nothing had altered screen-wise and tried a reboot to see if that would alter things. Same deal though.

```

$ kwin --replace
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
kwin(5743) KWin::EffectsHandlerImpl::loadEffect: EffectsHandler::loadEffect : Effect  "kwin4_effect_blur"  is not supported 
kwin(5743) KWin::EffectsHandlerImpl::loadEffect: EffectsHandler::loadEffect : Effect  "kwin4_effect_wobblywindows"  is not supported 
kwin(5743) KWin::EffectsHandlerImpl::loadEffect: EffectsHandler::loadEffect : Effect  "kwin4_effect_flipswitch"  is not supported 
kwin(5743) KWin::EffectsHandlerImpl::loadEffect: EffectsHandler::loadEffect : Effect  "kwin4_effect_startupfeedback"  is not supported 
kwin(5743) KWin::EffectsHandlerImpl::loadEffect: EffectsHandler::loadEffect : Effect  "kwin4_effect_cube"  is not supported 
kwin(5743) KWin::EffectsHandlerImpl::loadEffect: EffectsHandler::loadEffect : Effect  "kwin4_effect_coverswitch"  is not supported

```and using 'sudo' to run it :
```
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Error: "/var/tmp/kdecache-simon" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-simon" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-simon" is owned by uid 1000 instead of uid 0.
kdeinit4: Shutting down running client.
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
Error: "/tmp/ksocket-simon" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-simon" is owned by uid 1000 instead of uid 0.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x2600156
Error: "/var/tmp/kdecache-simon" is owned by uid 1000 instead of uid 0.
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-simon" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-simon" is owned by uid 1000 instead of uid 0.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
kwin(5647) KWin::EffectsHandlerImpl::loadEffect: EffectsHandler::loadEffect : Effect  "kwin4_effect_blur"  is not supported 
kwin(5647) KWin::EffectsHandlerImpl::loadEffect: EffectsHandler::loadEffect : Effect  "kwin4_effect_wobblywindows"  is not supported 
kwin(5647) KWin::EffectsHandlerImpl::loadEffect: EffectsHandler::loadEffect : Effect  "kwin4_effect_flipswitch"  is not supported 
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x2600156
Error: "/var/tmp/kdecache-simon" is owned by uid 1000 instead of uid 0.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x2600156
Error: "/var/tmp/kdecache-simon" is owned by uid 1000 instead of uid 0.
kwin(5647) KWin::EffectsHandlerImpl::loadEffect: EffectsHandler::loadEffect : Effect  "kwin4_effect_startupfeedback"  is not supported 
kwin(5647) KWin::EffectsHandlerImpl::loadEffect: EffectsHandler::loadEffect : Effect  "kwin4_effect_cube"  is not supported 
kwin(5647) KWin::EffectsHandlerImpl::loadEffect: EffectsHandler::loadEffect : Effect  "kwin4_effect_coverswitch"  is not supported 
QDBusConnection: name 'org.kde.kglobalaccel' had owner '' but we thought it was ':1.7'
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Error: "/var/tmp/kdecache-simon" is owned by uid 1000 instead of uid 0.

```

i.e. more output when using 'sudo' but nothing changes on the look of the screen.

---

