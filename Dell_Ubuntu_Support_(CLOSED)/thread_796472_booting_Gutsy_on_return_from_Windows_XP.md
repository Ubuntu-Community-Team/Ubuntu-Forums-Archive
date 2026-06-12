---
title: "booting Gutsy on return from Windows XP"
date: 2008-05-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by silbar on 2008-05-16
Greetings,

Does anyone else have this problem?

Running on a month-old Dell Inspiron 530, dual boot with Ubuntu Gutsy Gibbon and Windows XP Professional.  It now looks like every time I try to return from XP to Gutsy, I get to the Grub Menu OK.  But if I try to go to the generic Gutsy, the screen says "Starting Up...", then stays that way for a bit trying to load Linux, and then it stops and restarts, going back to the Dell splash screen and repeats the boot process.  And would do the same each time it tries to go into the default generic boot.

The first time I was able to recover from this, I powered down the machine, disconnected it from the wall, and let it sit there, cooling its heels overnight.  In the morning it booted properly into Gutsy generic.

This morning, however, when I tried unpowering it for an hour, it still stayed in the repeat restart mode.  Obviously not cool enough.

I believe I've found a way to get past this problem.  From the Grub Menu, choose instead to go into the recovery mode.  Then, from the # command prompt (as single user, i.e., as root), type 'telinit 5'.  This then continues to load to level 5, i.e., gives me a login screen, etc.

If then I restart from Gutsy, the boot into the default generic Gutsy works as normal.

   Dick Silbar

---

### Post by silbar on 2008-05-28
An addendum to my previous (solitary) posting:

Apparently no one else has this problem?

This restart behavior also occurs (occurred, only tried it once) if I go into hibernate from Gutsy.  The 'telinit 5' trick from recovery mode works in that case also.

It may be that the problem is a bit erratic.  Yesterday my wife (I wasn't present) was able to boot the Inspiron 530 into level 5 after a shutdown from XP.  Very strange.

Dick Silbar

---

### Post by silbar on 2008-06-12
Another update.

The problem disappears if the machine is shut down and lies quiet (unused) for about 2 hours.  That was apparently why my wife had no trouble with her bootup.  I suspect that allows some memory-retaining RAM to clear itself.

I have, by the way, now upgraded to Hardy Heron, but I haven't yet gone into XP to see if this restart problem is still there.

Dick Silbar

---

### Post by jadeuru on 2008-06-17
I would like to know how it went with Hardy Heron..
I just got a 530 with xp and want to dual boot with it-
I just posted about how to go about it-
Did you install the 64bit version?

---

### Post by silbar on 2008-07-05
Well, after installing the upgrade to Hardy, it took a long time before I got around to rebooting into XP.  Today I did, and -- amazingly -- on restarting into Hardy (without a two hour pause), there was no problem.  I did NOT have to use the 'telinit 5' trick from the recovery mode command line.

Having only done this once, I don't know if it was a fluke or something got fixed.  

By the way, I believe I installed the 32-bit version: 'uname -a' returns "Linux Lynx 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux".

Dick Silbar

---

