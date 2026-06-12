---
title: "[SOLVED] trouble with key bindings (probably quite remedial)"
date: 2008-12-10
forum: Desktop Environments
---

### Post by lamikins on 2008-12-10
Hallo!
I'm running a Xubuntu hardy OS, and it seems to be fairly common knowledge that there is no default keybinding wrt PrtSc.  I was trying to locate the bind code for the key with the intention of running:
[INDENT]$ bind '"whatever the PrtSc bind code is!": ksnapshot'[/INDENT]
I was tossing up between using xwd (xfce native i think) and ksnapshot (obviously imported from KDE)...  still undecided...  unimportant!  Moving on.

Long story short(er):  couldn't find PrtSc bind code, tried:
[INDENT]$ read [/INDENT]
[INDENT]<my input was> Fn-p [/INDENT]
[INDENT]- [/INDENT]
i.e. I though the bind code for function-p was a hyphen. So...
[INDENT]$ bind '"-": ksnapshot'[/INDENT]
Trouble is Fn-p doesn't pull up ksnapshot, and now in terminal I am unable to input hyphens.  Oh the perils of naive keyboard manipulation.

Does anyone know what I have done wrong?  Does anyone know the PrtSc bind code?  Does anyone know how to remove a bad key binding?  Find out in the next episode of: Fool in the Terminal!  Erm... sorry.

Thanks for listening thus far (thus far being the end of this dreary post)!

---

### Post by Denestria on 2008-12-10
Running **xev** in the terminal and then pressing the key you want will give you info about that key for your keyboard, but I have no idea what you are doing with read and bind.  Can't you just open the Settings Manager > Keyboard > Shortcuts and add a shortcut with the command for the screen shot program you want with the shortcut set to the printscreen button?

---

### Post by lamikins on 2008-12-12
You're probably right!  As I said - naive fiddling on my part.  I shall try it in a minute.  Thanks

---

