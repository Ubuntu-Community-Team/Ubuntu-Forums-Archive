---
title: "Compiz window decorator crashes frequently"
date: 2011-12-06
forum: Desktop Environments
---

### Post by evencoil on 2011-12-06
I have been using Ubuntu 11.04 for a while now and I am surprised this hasn't been fixed in any of the updates.

The problem, simply put, is that the compiz window decorator plugin crashes. Very frequently. Especially when I open GVim (not sure what is special about that application).

Of course I can restart compiz and all is well, but doing so resets the window configurations on my screen, which is a real annoyance.

I've searched around and found that this is a common problem. The only solution I've found is to restart compiz. Well yes...but isn't there something better? And why hasn't this been fixed yet? Is it ever going to be fixed? I have an older version of compiz on a 10.04 install where this happens occasionally when I log in (but not after that)--so the basic bug has been around for a long time. It seems to be getting worse.

---

### Post by stinkeye on 2011-12-06
Inn **ccsm > window decoration** check that the command is 
```
/usr/bin/compiz-decorator
```
Just click on the default button.
Sometimes changes to gtk...something or other.

---

### Post by Krytarik on 2011-12-07
> **evencoil said:**
> The only solution I've found is to restart compiz. Well yes...but isn't there something better?
While, too, lacking a real solution, you could just restart the window decorator, not the entire Compiz, by running the command *stinkeye* noted in the above post, or the other (more direct) one would be:
```
gtk-window-decorator --replace
```That would be the decorator for Metacity themes, for Emerald it would be:
```
emerald --replace
```I had to do the latter for some time when I, same as you're describing it, had issues with the decorator coming (or staying) up at login, in Lucid 10.04.

Run either of those commands via the Alt+F2 dialog, or prepend "setsid" to them if running from a Terminal.

Regards.

---

### Post by evencoil on 2011-12-07
Replacing the command with /usr/bin/compiz-decorator didn't help.

The replace suggestion is a decent workaround--I will just bind a key to that command and then run it as needed.

---

