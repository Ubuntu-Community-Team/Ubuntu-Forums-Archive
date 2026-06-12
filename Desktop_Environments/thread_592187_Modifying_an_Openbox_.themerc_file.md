---
title: "Modifying an Openbox .themerc file"
date: 2007-10-26
forum: Desktop Environments
---

### Post by The Tronyx on 2007-10-26
Hi everyone, I've found some solid themes for openbox but there is one thing I don't like that a lot of them have in common.  Often the close, minimize and maximize buttons are only visible when you mouse over them.  I would like to change it so that those buttons are visible all the time.

Here is the .themerc I am working with

[http://pastebin.com/m2ca14ed3](http://pastebin.com/m2ca14ed3)

Thanks for the help!

---

### Post by urukrama on 2007-10-26
I can't access the file you linked to, but editing a themerc file isn't very hard. What you are interested in are the following settings:

> window.active.button.unpressed.image.color: 

Change the colour code there to whatever colour code you want, save the file, reconfigure Openbox (using the root menu option 'Reconfigure'), and the changes will be visible. If you want the inactive window buttons to change as well, look for the 'window.inactive.etc' code. The theme options of Openbox are fairly straightforward. If you need more help, have a look at [this]("http://icculus.org/openbox/index.php/Help:Themes") page.

If you need help finding the colour code of the colour you like, you can use an application like gcolor2 or the gimp.

---

