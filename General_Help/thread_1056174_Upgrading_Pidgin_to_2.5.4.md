---
title: "Upgrading Pidgin to 2.5.4"
date: 2009-01-31
forum: General Help
---

### Post by fearful on 2009-01-31
When I type ./configure while trying to upgrade pidgin I get this message:

XScreenSaver extension development headers not found.
Use --disable-screensaver if you do not need XScreenSaver extension support,
this is required for detecting idle time by mouse and keyboard usage.


I install XScreenSaver and nothing, I can't use that '--disable-screensaver' command, or I'm doing it wrong.

Any ideas?
Thanks

---

### Post by utnubuuser on 2009-01-31
are you using "sudo --disable-screensaver".

And I'm guessing here, but --disable is probably an argument for /.configure, not a stand-alone command.

as in  sudo /.configure --disable-screensaver

---

### Post by hikaricore on 2009-01-31
You should **never** need sudo to run a configure scipt.
The only sudo command you may need is for *make install* or *make uninstall*.

```
./configure --disable-screensaver
```

Should suffice.

[COLOR="DarkRed"]**Out of curiousity, is there some reason that version 2.5.4 on getdeb.net won't work for you? [http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin)**[/COLOR]

---

### Post by utnubuuser on 2009-02-02
Thanks hikaricore  --- learn something new everyday.

---

### Post by lethu on 2009-02-07
This may probably be useless to the op, since it comes a bit late, but just in case and for others in the same situation. If you can't live without the feature disabled by the following argument [COLOR="Blue"]`--disable-screensaver'[/COLOR] ([COLOR="Blue"]will build libpurple without support for detecting when it should mark accounts idle based on mouse or keyboard usage[/COLOR]) then the appropriate package to install should be "libxss-dev".

Good luck.

---

