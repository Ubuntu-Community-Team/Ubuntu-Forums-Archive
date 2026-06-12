---
title: "Weird problem with editors after Ubuntu upgrade. Squares instead of strings visible"
date: 2011-06-03
forum: Desktop Environments
---

### Post by chausberger on 2011-06-03
Hello,

after upgrading from Ubuntu 9.04. do 11.04 (new installation), I have weird problems with the Eclipse editor. I also saw this in other editors like Gvim, so maybe this is GTK/Gnome related (Eclipse uses GTK on Linux as far as I know).

With the Eclipse PyDev plugin, whenever I typ single quoted strings like 'bla', they appear as squares (both the quotes as well as the string).

First I thought this was a problem with the PyDev plugin, but it also happens with Java and Scala Plugins.  With Java, it happens, for example, when typing

System.out.println("bla") and then "out" is shown as squares only.

See the attached screenshot.

This is very weird. I've never had this before with any Ubuntu, Java or Eclipse version.

Currently, I use:
Ubuntu 11.04.
Eclipse 3.6
Java 1.6.0_25

I doubt is has anything to do with Java as I use the same versions on older Ubuntu installations (10.04, 9.10, etc) at work.

Any ideas what could be wrong here and how to fix this?

Claus

---

### Post by sergey_korobov on 2011-08-17
That is because there is no italic version of the font used to show text (Monospace). You can change font to Liberation Mono for instance.

---

