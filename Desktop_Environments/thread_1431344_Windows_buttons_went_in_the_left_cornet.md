---
title: "Windows buttons went in the left cornet"
date: 2010-03-16
forum: Desktop Environments
---

### Post by flapane on 2010-03-16
After the latest sysupdate, the windows buttons went from right to left corner.
How to fix that?
[IMG]http://i.imgur.com/IDltL.jpg[/IMG]

---

### Post by Simian Man on 2010-03-16
That's crazy!  I wonder why nobody else noticed this??

---

### Post by flapane on 2010-03-16
Is it ironic or what

---

### Post by pastalavista on 2010-03-16
crappy code...

---

### Post by howefield on 2010-03-16
Must be your system....

Is it a problem ?

[http://ubuntuforums.org/showthread.php?t=1430585](http://ubuntuforums.org/showthread.php?t=1430585)

---

### Post by pastalavista on 2010-03-16
[Ubuntu-Tweak]("http://ubuntu-tweak.com/downloads/") has an app for that

---

### Post by flapane on 2010-03-16
I feel less lonely now...

Definitely answer #2 "Yes, I have clicked on the wrong thing but only once".

I'm used to that on Osx since Tiger era, but I don't really like it in gnome.

@pastalavista I can't find it

---

### Post by mcduck on 2010-03-16
> **flapane said:**
> After the latest sysupdate, the windows buttons went from right to left corner.
How to fix that?
[IMG]http://i.imgur.com/IDltL.jpg[/IMG]

Let me guess, you didn't actually update 9.10 but instead upgraded to 10.04 alpha?

That's the order of buttons 10.04 uses. If you want to change it back to old layout then the simple way (that doesn't require you to install any extra software!) is this:

1. Press Alt-F2 and run "gconf-editor"
2. Browse to apps/metacity/general
3. Change the "button_layout"-key from "maximize,minimize,close:" to "menu:minimize,maximize,close"

---

### Post by flapane on 2010-03-16
9.10 here, I don't have those repos but I don't exclude that some ppa could contain some backported package.

Thanks, I solved!

---

### Post by alex.rayu on 2010-03-16
It's a feature.

---

### Post by flapane on 2010-03-16
silent feature, I'd say :)

---

### Post by asmoore82 on 2010-03-16
Big News!

[http://arstechnica.com/open-source/news/2010/03/ubuntu-dumps-the-brown-introduces-new-theme.ars](http://arstechnica.com/open-source/news/2010/03/ubuntu-dumps-the-brown-introduces-new-theme.ars)

[https://wiki.ubuntu.com/Brand](https://wiki.ubuntu.com/Brand)

---

### Post by stinkeye on 2010-03-26
Why min max close buttons were moved to left on lucid.[_**[COLOR="DarkRed"]Esfera: New UI Element Proposal For Ubuntu[/COLOR]**_]("http://www.webupd8.org/2010/03/esfera-new-ui-element-proposal-for.html")

---

### Post by J-raff on 2010-03-28
i actually set my button layout that way through gconf-editor. it's more ergonomically friendly. to me, at least.

---

### Post by Megafag on 2010-03-28
> **flapane said:**
> After the latest sysupdate, the windows buttons went from right to left corner.
How to fix that?
[IMG]http://i.imgur.com/IDltL.jpg[/IMG]

Needless to say, i loled.

---

### Post by paul.drover on 2010-04-05
> **mcduck said:**
> Let me guess, you didn't actually update 9.10 but instead upgraded to 10.04 alpha?

That's the order of buttons 10.04 uses. If you want to change it back to old layout then the simple way (that doesn't require you to install any extra software!) is this:

1. Press Alt-F2 and run "gconf-editor"
2. Browse to apps/metacity/general
3. Change the "button_layout"-key from "maximize,minimize,close:" to "menu:minimize,maximize,close"

Ahh... That's better!

---

