---
title: "Frozen Bubble doesn't run"
date: 2006-07-15
forum: Gaming &amp; Leisure
---

### Post by Remillard on 2006-07-15
Hello,

So I am still new in Ubuntu-land (though came from several years of Gentoo).  Everything seemed to be working fine, so I thought I'd install frozen-bubble and see if that worked.  The install seemed to go fine, however upon running the game, nothing happens.  Running from the terminal it seems to launch and I get down to [SDL Init] SDL_Init 65535 and then nothing happens.

Another side annoyance, I now have several frozen-bubble processes that I cannot kill.  It doesn't seem to be one of those times when it's regenerating new pid faster than I can kill it, It just doesn't die, even with sudo kill -9.  So if someone knows why this isn't working under Ubuntu, I'm all ears for that one too.

Anyhow if someone knows of something I can try, I'd sure appreciate it.  

Regards,
Remillard

PS:  Tried some other things.  Bzflag works fine.  Enemy Territory seems to work fine though I get REALLY strange smearing effects.  Makes aiming a bit difficult, but it did run enough to verify that it basically runs.  However, Chromium does NOT run.  Once again, I get some intro messages in the terminal and then it hangs, and once again I get these strange processes that I cannot kill.

---

### Post by Perfect Storm on 2006-07-15
Did you install the proper driver for you graphic card (for 3D acc.)?

Which version of ubuntu do you use? and which Structure?

Tried with reinstalling libsdl libs?

---

### Post by Remillard on 2006-07-15
As far as I know, I have the proper drivers for video.  BZflag works fine and looks REAL sharp.  They've really notched up the eye-candy on that one.

This is stock 6.06 LTS Ubuntu.  Not sure what 'structure' you mean, but it's the stock Gnome one.

I have not yet tried reinstalling libsdl.  I will go give that a shot.

PS:  Doesn't work.  I even tried switching it to libsdl-all (as opposed to libsdl-alsa) and that didn't work.

---

### Post by Perfect Storm on 2006-07-15
I mean i386, ppc, a64 :)

Try download the packages from here: [http://packages.ubuntulinux.org/dapper/games/frozen-bubble](http://packages.ubuntulinux.org/dapper/games/frozen-bubble)

[http://packages.ubuntulinux.org/dapper/games/frozen-bubble-data](http://packages.ubuntulinux.org/dapper/games/frozen-bubble-data)

First removing the existing:

```
sudo apt-get --purge remove frozen-bubble

```

It could be the package.

---

### Post by Remillard on 2006-07-16
Howdy,

Well got around to trying to manually install the package.  It's labeled precisely what was in the repository before, but now it works.  Couldn't tell you why.  I did reboot yesterday and so that might have been the issue, though I"m not really used to having to reboot just to get something like a game installed.

Chromium now works too, lending to the "reboot made it happen" theory.

Anyhow, thanks for the help, I do appreciate it.

Best regards,
Remillard

---

### Post by Perfect Storm on 2006-07-16
Could be something like 3D card acc driver that needed you to logout/reboot which could have been the case.

---

