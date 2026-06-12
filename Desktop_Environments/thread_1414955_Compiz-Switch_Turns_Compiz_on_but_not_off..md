---
title: "Compiz-Switch Turns Compiz on but not off."
date: 2010-02-24
forum: Desktop Environments
---

### Post by kopatops on 2010-02-24
Hi!

Just would like to know if anyone else has had this problem, or if perhaps you can help me?

I'm running the latest pre-release version of Lucid Lynx with Compiz-Switch 0.4.3. Compiz-Switch is a really neat program that toggles the state of a composited/not composited desktop. I use it extensively.

Recently (upon first upgrade to a prerelease Ubuntu) the program can turn compiz on as usual, but not off.

Thought I'd post this problem here, in case others have the problem or a solution. I wasn't expecting things to work flawlessly in the prerelease Lucid. Posting on the forum usually raises interesting topics though. ;)

Should I report this as a bug somewhere?

Tnx!

/still newbie although not that much'

EDIT: Oh, and yea I'm perfectly aware the problem may be caused by human error on my side, or entirely by the program itself. Not Ubuntu. I'm clueless regarding that.
Running a laptop with an NVIDIA 8600M GT card, latest drivers clumsily installed by hand.

---

### Post by stinkeye on 2010-02-24
Try fusion-icon```
sudo apt-get install fusion-icon
```
Allows you to switch window managers and window decorators.
Add to startup applications using
```
fusion-icon -n
```
-n stops it from loading a window manager at start which is not neccessary
and can cause problems.

---

### Post by kopatops on 2010-02-24
Thanks stinkeye!

Works pretty dmn good :)

Any way to use this by command line though? Don't really want the icon switcher.

---

