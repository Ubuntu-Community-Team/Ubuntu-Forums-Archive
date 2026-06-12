---
title: "Kill Compiz gracefully / fallback window manager"
date: 2007-11-25
forum: Desktop Environments
---

### Post by kooldino on 2007-11-25
I'm running Kubuntu 7.10

With my video card, at least, (an ATi x700 or so) compiz likes to freak out when I run certain programs (like OpenOffice) and makes them almost unusable.

When this happens, I'd like to be able to kill compiz gracefully (I'm currently doing a "pkill compiz" since that's the only way I know how), and I'd like it to auto load some kind of fallback window manager, like the default KDE window manager, or at minimum OLWM or something.

I have the crash handler plugin enabled, and in the command box I put "olwm", but when it crashes, no window manager loads.

Any advice short of getting a geforce?

---

### Post by kooldino on 2007-11-26
bump

---

### Post by kooldino on 2007-11-28
Help!

---

### Post by Melcar on 2007-11-28
Once I get my Kubuntu install back up I will try messing with some commands.  I have been meaning to make something similar too, because running fglrx with AIGLX still has some issues.  Maybe custom lunchers with the on and off Compiz commands?  It should be possible.  Maybe even add custom keyboard shortcuts while I'm at it.

---

### Post by kle on 2007-11-29
Hello

I found this good advice posted here on these pages (somewhere), and it certainly stopped my Kubuntu from crashing, but I have not tried openOffice since. 

Use alt-F2 (to run a command):
compiz --replace 
# to turn compiz on

kwin --replace
# to revert to kwin

(kwin is native to Kubuntu)

---

### Post by kooldino on 2007-11-29
Ah, thank you very much.

Now I just need to set up the fallback that can somehow detect when there is no window manager running, and it launches itself.

---

### Post by Levant on 2007-11-29
Perhaps you can try "sudo apt-get install fusion-icon". This will place the compiz fusion control icon in your tray, where you can right click it and select your window manager (compiz or kwin in this instance). I do not use KDE, but this solution worked great in GNOME, it should work for you too.

---

### Post by kooldino on 2007-11-30
Package not found.

However, the gnome-compiz-manager package says it has a tray icon.  Not sure if that would work for me being as I have kubuntu.

---

### Post by Levant on 2007-11-30
Sorry! I forgot to tell you that you need to add these to your software sources:

deb [http://ppa.launchpad.net/maco.m/ubuntu](http://ppa.launchpad.net/maco.m/ubuntu) gutsy main restricted universe multiverse
deb-src [http://ppa.launchpad.net/maco.m/ubuntu](http://ppa.launchpad.net/maco.m/ubuntu) gutsy main restricted universe multiverse

Those repos contain the fusion-icon package, they aren't in the usual repos.

This thread might also be useful for you: [http://ubuntuforums.org/showthread.php?t=601310](http://ubuntuforums.org/showthread.php?t=601310)

Good luck

---

### Post by kooldino on 2007-11-30
> **kooldino said:**
> Package not found.

However, the gnome-compiz-manager package says it has a tray icon.  Not sure if that would work for me being as I have kubuntu.

Well, I installed it anyway, but it doesn't seem to do anything.

---

### Post by kooldino on 2007-12-05
> **Levant said:**
> Sorry! I forgot to tell you that you need to add these to your software sources:

deb [http://ppa.launchpad.net/maco.m/ubuntu](http://ppa.launchpad.net/maco.m/ubuntu) gutsy main restricted universe multiverse
deb-src [http://ppa.launchpad.net/maco.m/ubuntu](http://ppa.launchpad.net/maco.m/ubuntu) gutsy main restricted universe multiverse

Those repos contain the fusion-icon package, they aren't in the usual repos.

This thread might also be useful for you: [http://ubuntuforums.org/showthread.php?t=601310](http://ubuntuforums.org/showthread.php?t=601310)

Good luck

Ah, ok, great.  That got the fusion icon on there.

Is there a way to get that to run automatically when KDE loads?  Putting it in my .profile did bad things, so that won't work.

---

