---
title: "Odd keyboard behaviour with double and single quote marks"
date: 2008-11-15
forum: Desktop Environments
---

### Post by NZJon on 2008-11-15
Hi there,

I've come across something odd in my Ubuntu 8.10 x86 installation. Whenever I type the single quote key ['] or the double quote key ["], if I don't type a [space] after it, the quote is "added" to the subsequent character.

For example, if I type:

```
"a
```

what I actually end up with is:

```
ä
```

(That is, an umlaut above the letter a.) This behaviour is the same for single quote mark too. 

I&#7743; guessing I've put GNOME or my computer into some unusual mode, but I can't figure out how to undo whatever it was that I did. If anyone has suggestions, it would be REALLY appreciated...

Many thanks,

  Jon

---

### Post by andrewpay on 2008-11-15
This problem goes right back to the console settings

run the following command in a terminal

"sudo dpkg-reconfigure console-setup"

Read the messages with each setting.
Use the simplest possible setting with no variants to correct the problem.
After the keyboard works go back and add the variants.

WARNING If you tried to correct the problem with the graphical tools, you may have to undo that as well.

On "Xubuntu 8.10" Settings > Settings Manager > Keyboard > Layouts
make sure "Use X Configuration" should be checked until the problem is fixed.

---

