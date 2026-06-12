---
title: "Accents under Ubuntu"
date: 2005-09-09
forum: Desktop Environments
---

### Post by NoHope on 2005-09-09
Hello all! I don't know why, but Ubuntu is not recognizing dead keys, when I type '+a, it returns 'a, but I want á...

What could I do?

Thank you! Bye!

---

### Post by mlomker on 2005-09-09
I haven't looked into it very far but there are some [FAQ's](http://ubuntuforums.org/showthread.php?t=27039) on keyboard mapping.  I also assume that there is a gnome keyboard/internationalization applet in the control panel (I use KDE and it's in the control center there).

---

### Post by shino on 2005-09-10
[QUOTE=mlomker]I haven't looked into it very far but there are some [FAQ's](http://ubuntuforums.org/showthread.php?t=27039) on keyboard mapping.  I also assume that there is a gnome keyboard/internationalization applet in the control panel (I use KDE and it's in the control center there).[/QUOTE]
 I've got the same problem here with KDE. Curiously everything works great with Gtk applications, but with KDE when I Type ^+e for exemple it returns ^e as NoHope described.

In control panel internationalization is activated, and the command of xkb is : "setxkbmap -model pc105 -layout fr -variant basic"  so deadkeys should work...

Any ideas ? ^^

---

### Post by shino on 2005-09-10
My problem is solved: I had to run !
$set-language-env -r
in my profile to cancel modification done by this script, and accents are working again in KDE !

---

### Post by kairu0 on 2005-11-05
I misread the last post and ran set-language-env.

Now my default locale is missing :(

---

### Post by Commuto on 2006-03-07
[QUOTE=shino]I've got the same problem here with KDE. Curiously everything works great with Gtk applications, but with KDE when I Type ^+e for exemple it returns ^e as NoHope described.

In control panel internationalization is activated, and the command of xkb is : "setxkbmap -model pc105 -layout fr -variant basic"  so deadkeys should work...

Any ideas ? ^^[/QUOTE]
There is a possibility that the keyboard layout was not *really* stored in the system preference. In that case [bug report 15372](http://bugzilla.ubuntu.com/show_bug.cgi?id=15372) provides a fix :D

---

