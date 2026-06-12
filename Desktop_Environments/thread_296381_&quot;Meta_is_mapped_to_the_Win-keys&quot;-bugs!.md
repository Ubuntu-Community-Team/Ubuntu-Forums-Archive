---
title: "&quot;Meta is mapped to the Win-keys&quot;-bugs!?"
date: 2006-11-09
forum: Desktop Environments
---

### Post by kalle314 on 2006-11-09
I have tried to map Meta to the win-keys by choosing "Meta is mapped to the Win-keys" in the GNOME keyboard settings. This will not work very well.

The default is that Alt works both as Meta and Alt, and Esc emulates Meta when it is pressed and released.

When Meta is mapped to win instead of Alt, Emacs will use this, and the Alt key will no longer work there. However, applications that use Readline will continue with Alt as Meta, and Win does nothing, even though both the program xev and the command "xmodmap -pk" confirms that the Meta is mapped to Win.

Anyone have the same problem, or has solved this problem? 
I thought that I maybe should file a bug for this, but where should that be? Ubuntu, Xorg, GNOME or GTK?

Furthermore, choosing "Meta is mapped to the Win-keys" will result in the "Alt Gr" key being transformed into a second Alt key. Choosing "Meta is mapped to the left Win-key" lets you keep Alt Gr. This is already reported as Debian bug 276143 since 2004:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=276143](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=276143)

---

### Post by kalle314 on 2006-11-09
I went ahead and reported this in launchpad:
[https://launchpad.net/distros/ubuntu/+bug/71138](https://launchpad.net/distros/ubuntu/+bug/71138)

---

### Post by kalle314 on 2006-11-10
Could someone confirm the bug please? 	[-o<

Or maybe think of a better package to file it under? I did put it under "xkeyboard-config", but I am not very sure as to where the problem is.

---

