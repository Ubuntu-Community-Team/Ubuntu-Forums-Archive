---
title: "Missing window manager controls and session manager error."
date: 2011-11-03
forum: Desktop Environments
---

### Post by casbahdk on 2011-11-03
I have suddenly started getting the following session manager error: "Failed to connect to the session manager: SESSION_MANAGER environment variable not defined" This error occurs when I try```
$ sudo xfwm4 --replace
```to get my missing window borders back.

I am using Xubuntu 11.04 64 bit.

---

### Post by Toz on 2011-11-03
Don't use sudo, just:
```
xfwm4 --replace
```

---

### Post by casbahdk on 2011-11-03
> **Toz said:**
> Don't use sudo, just:
```
xfwm4 --replace
```

Thanks for the quick reply. That did the trick.

---

### Post by neu5eeCh on 2012-01-23
#&%^$!!!!!! :evil:

So.... I installed XFCE 11.10 on my wife's netbook thinking they had  fixed this problem, but  I get a call from her (from work) wondering  what the 'H' is wrong with her computer. Turns out it's this bug and the  Xubuntu devs still haven't fixed. ](*,)

The problem is that Chrome is up and is not surrendering control to any other window. ALT+F2 does nothing. It pops up but she can't type in the window. She can right click on the desktop and bring up a terminal, but she still can't paste into or write a command in the terminal. Any ideas?

Right now, she's sitting in front of a paper weight with XFCE 11.10 written all over it.

---

### Post by neu5eeCh on 2012-01-23
OK, for the next person (and there will be a next person until Xubuntu devs take this bug very seriously) you can do one of two things. CTRL-ALT-F1 will get you into a Virtual Terminal. Log in using your username and password. Once there, try either of the following:


mv ~/.cache/sessions ~/.cache/sessions.bak

This command renames your session (essentially deleting it while creating a backup).

or

rm -rf ~/.cache/sessions

This deletes the offending session. **r** is recursive (remove all directories and sub directories in the sessions, and **f** is force (ignore nonexistent files and never prompt).

CTRL-ALT-F7 will return you to your DE. For more info on Virtual Terminals, look [here]("http://www.tuxfiles.org/linuxhelp/shortcuts.html").

Once that's done, some users claim to have solved the problem by putting XFWM4 in their startup apps. That didn't work for me. You can find other solutions [here]("http://ubuntuforums.org/showthread.php?t=1846266").

And gor more information on this bug look [here]("https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/495361").

---

### Post by wkrekik on 2012-01-23
Does Ctrl-Alt-Backspace or Alt-PrintScreen-k works ? Both will kill X (so all non saved data will be lost) and get you back to the connection screen. Then log in into the recovery console instead of Xubuntu/Xfce session, type "xfwm4 --replace", then type "exit", now log in into the usual Xubuntu/xfce session, and it should be fixed.

EDIT : sorry, grilled .... And your solution is better :)

---

