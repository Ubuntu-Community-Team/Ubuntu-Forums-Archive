---
title: "Problems after Hoary-&gt;Breezy upgrade"
date: 2005-11-04
forum: Desktop Environments
---

### Post by ISagalaev on 2005-11-04
Hello!

I want to share my experience after upgrading from Hoary to Breezy and also ask for some help.

After upgrading several things have broken:
- due to changing default output sound device to ESD I had no sound. Changing to ALSA helped
- USB drives named with non-ascii letters no longer mounted automatically (filed a bug [https://bugzilla.ubuntu.com/show_bug.cgi?id=18904](https://bugzilla.ubuntu.com/show_bug.cgi?id=18904))
- new version of my text editor of choice - SciTE - was completely broken. Solved this by stealing new version from Dapper Drake repositories (filed a bug [https://launchpad.net/distros/ubuntu/+source/scite/+bug/3906](https://launchpad.net/distros/ubuntu/+source/scite/+bug/3906))

And for these things I still have no solution:
- CD player also stopped outputting any sound
- 'Import photos' popup that should appear after plugging digital camera doesn't appear. Manually launching from gthumb works though... I saw such problem somewhere in these forums but without answers.
Please help!

P.S. I'm sure Breezy is a big step forward but I'm just glad that my first Ubuntu was Hoary. If it was Breezy then my first experience consisted of "no camera support, no USB drive and no sound" :-).

---

### Post by tmckellar on 2005-11-05
It sounds like your problem may be the Gnome Volume Manager for most of it. When I originally installed Ubuntu 5.04 I messed around and somehow got Gnome Volume Manager to not work quite right. My suggestion would be to try reinstalling the Gnome Volume Manager. After that if it still acts twitchy I'd try reinstalling the Gnome Desktop and Ubuntu Desktop.

---

### Post by iNerdSure on 2005-11-07
Hi, tried reloading Gnome Volume Manager, Gnome Desktop and Ubuntu Desktop.

Still SILENCE - NO SOUND.

Any other trooubleshooting or diagnostics I can use?

---

