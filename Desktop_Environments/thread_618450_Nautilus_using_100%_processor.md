---
title: "Nautilus using 100% processor"
date: 2007-11-20
forum: Desktop Environments
---

### Post by DeadTaco on 2007-11-20
I'm not quite sure what's going on, but I'm running a fresh install of Ubuntu 7.10, and after browsing files and closing the nautilus window, nautilus eats my processor and gets stuck in memory.  I have a processor meter running in my upper toolbar to see how much is being used, and it constantly shows 100% useage until I view processes and force nautilus to close.

No Nautilus windows are visible when this happens.  It's like it has a hard time clearing itself from memory and gets jammed.

All compiz screen effects are turned off.

Any ideas?

---

### Post by DeadTaco on 2007-11-28
Bump.

---

### Post by DeadTaco on 2007-12-11
Bumpety Bump bump?

The problem is even worse now, and the system is nearly unresponsive.  Only happens after browsing files on the desktop (Nautilus).  :mad:

---

### Post by DeadTaco on 2007-12-14
In case anyone else gets cursed with this problem, I found out why it's happening:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/151168](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/151168)

It's just too bad nobody else could help me out with this before I removed Ubuntu completely and reinstalled it out of frustration, only to run into the same issues.  So goes life, I guess.

---

### Post by DeadTaco on 2007-12-14
Nevermind.  Even after turning off compiz and turning off the restricted nvidia drivers, nautilus jumps back to 90%-100% usage even after a full reboot.  It only happens *after* I close any file browsing windows.  Please help :confused:

---

### Post by astoltz on 2007-12-14
When it happens, you just have to kill nautilus and then re-start nautilus.```
killall nautilus
nautilus &
```Apparently, nautilus is supposed to re-start itself after the first command but I've never had that happen so the second command is necessary for me.

There is a bug in Nautilus - I'm sorry but I can't remember the details and it most likely won't be fixed until Hardy.  In the mean time, I found an ugly work-around:  Edit the file "/etc/gdm/PostSession/Default" and add the line "killall nautilus" right before the exit 0 line.  This will kill nautilus when you log out (it only goes to 100% if log in / log out / log in again).
Before:```
PATH="/usr/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}

exit 0
```
After:```
PATH="/usr/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}

killall nautilus
exit 0
```

---

### Post by foxmulder881 on 2007-12-14
I get this same problem but with Firefox. And only on selected websites. Funnily enough, Ubuntuforums.org is one of those websites I always have problems with. 
At first, I thought it was a Java or Javascript error, but I installed and now use the IcedTea packages instead but still have the problem. It plagued me in Feisty too, but I have learnt to live with it as I can't find a solution to the problem. And it seem no-one else knows how to fix it either.
Sometimes it gets to a point where the only way to browse the net is to use my backup browser, Flock. And I hate it!

---

### Post by DeadTaco on 2007-12-18
> **astoltz said:**
> When it happens, you just have to kill nautilus and then re-start nautilus.```
killall nautilus
nautilus &
```Apparently, nautilus is supposed to re-start itself after the first command but I've never had that happen so the second command is necessary for me.

There is a bug in Nautilus - I'm sorry but I can't remember the details and it most likely won't be fixed until Hardy.  In the mean time, I found an ugly work-around:  Edit the file "/etc/gdm/PostSession/Default" and add the line "killall nautilus" right before the exit 0 line.  This will kill nautilus when you log out (it only goes to 100% if log in / log out / log in again).
Before:[CODE]PATH="/usr/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS


Thanks for this tip.  I will certainly give it a shot.

I noticed that Nautilus also goes nuts whenever I close any window that is browsing files, not just when I log off.  I have placed a script on my desktop that I can click any time this happens, but it's still frustrating.  I guess they used Nautilus version 2.20 for Gutsy Gibbon, which is not a stable build.  They should have stuck with version 2.12, which is the stable one.  I tried compiling 2.12 to replace 2.20, but it failed.  So goes life, I suppose.

-----------------

foxmulder881, have you tried firefox 3.0 beta?  I hear it fixes a lot of memory issues, and may help you out.

---

### Post by foxmulder881 on 2007-12-20
> **DeadTaco said:**
> foxmulder881, have you tried firefox 3.0 beta?  I hear it fixes a lot of memory issues, and may help you out.

Nah, haven't tried it yet mate.
I think I'll wait until it goes gold before I give it a shot.

**Update:** I downloaded the tar archive for Firefox 3.0 beta 2 and am simply running it from the binaries from a temp folder.
I must say, it does actually seem to have dealt with memory issues (in particular, UbuntuForums.org) a lot better than Firefox 2.0.0.11. But it's also as slow as buggery at rendering pages.
And what's with the new theme and buttons, it's darn ugly!
I most certainly hope that the Mozilla Developers speed it up before it goes gold. Because if this is how it will be in the final release, I most certainly wouldn't upgrade.

[IMG]http://img.techpowerup.org/071220/Screenshot.png[/IMG]

---

