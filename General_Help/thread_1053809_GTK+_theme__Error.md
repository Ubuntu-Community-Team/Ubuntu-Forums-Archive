---
title: "GTK+ theme  Error"
date: 2009-01-29
forum: General Help
---

### Post by Sonah on 2009-01-29
HI

I use Ubuntu 8.10

I get this Error txt when i select a theme :

> "This Theme will not work as intended because the required GTK[COLOR="Red"]+[/COLOR] theme engine is bot installed."

[IMG]http://i43.tinypic.com/2n6tezr.gif[/IMG]

---

### Post by mcduck on 2009-01-29
As long as the error doesn't actually define any GTK engine it's missing you can simply ignore the error message. Your themes work just fine.

---

### Post by UbuntuNerd on 2009-01-29
read here it explains it all about your problem, look at response number 5
[http://ubuntuforums.org/showthread.php?t=1040734]("http://ubuntuforums.org/showthread.php?t=1040734")

---

### Post by mcduck on 2009-01-29
> **UbuntuNerd said:**
> read here it explains it all about your problem, look at response number 5
[http://ubuntuforums.org/showthread.php?t=1040734]("http://ubuntuforums.org/showthread.php?t=1040734")

Honestly, the post nr. 5 on that thread is complete nonsense. :D

That error message is supposed to warn you if the theme you are using uses some GTK engine you haven't got installed. In that case you are supposed to get a warning that tells what the missing engine is, so you can install it.

However it's a common trick to use definitions for "empty" theme engine when making themes to "un-theme" some parts of applications. The current version of Appearance manager doesn't understand this, and then complains about missing a GTK engine (with no name).

Example of a real error message would be like this:
The theme will not look as intended because a required GTK+ engine **"Aurora"** is not installed.

However this error message that tells a GTK+ engine **"** is not installed is meaningless. The theme, at that point, doesn't define any engine at all and thus you are not missing any engine. The theme works as it's supposed to, but the Appearance manager complains because of the empty definition in the theme's .gtkrc file.

Like I said, the theme is working like it's supposed to, and that error message can be ignored. If it bothers you you can edit the theme and change all empty engine definitions ("") to "pixmap", for example, to get rid of the error message. This will however have no effect on the theme and takes a bit of work to do so I wouldn't bother.

---

