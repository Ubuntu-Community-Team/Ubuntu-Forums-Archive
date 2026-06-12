---
title: "Lock gDesklets to desktop"
date: 2007-10-25
forum: Desktop Effects &amp; Customization
---

### Post by fhslacrosse13 on 2007-10-25
is there a way to lock the gDesklets on my desktop so that when I use the "Show Desktop" button they stay showing on the desktop?

---

### Post by werebus on 2007-10-25
In the Show Desktop section of the CompizConfig Settings Manager, under "Misc. Options", change the "Window Type" default value of ```
type=toolbar | type=utility | type=dialog | type=normal
``` to ```
(type=toolbar | type=utility | type=dialog | type=normal) & !name=gdesklets-daemon
```

There is also a "widget layer" control panel, but I haven't figured out how to always make it appear on top.  In theory, you should be able to put ```
name=gdesklets-daemon
``` in the _Widget Layer -> Widget Window_ box and the _Window Rules -> Above_ box and your desklets should show up on top of everything when you activate widget layer.  However, on my machine, the "above" half doesn't always catch, and I'm left with a widget layer that's behind all my other windows.  Might work for you, though.

---

### Post by NawaMan on 2007-10-25
I recall that just yesterday someone post the solution but can't find it :p ... Here is what he did (with out using Widget Layer)

"In Window Rules"
Set "Skip Taskbar" to be "class=Gdesklets"

Then in General Seeting UNCHECK "Hide Skip Taskbar Windows". 

This works reliable for me (not sure if I need to restar).

Hope this helps

---

### Post by fhslacrosse13 on 2007-11-02
So, none of these ways worked for me.  I have no clue how you get this to work.  Also, I'm now using screenlets just in case that would change anything.

---

### Post by Forlong on 2007-11-02
Just disable **Hide Skip Taskbar Windows** in *ccsm &#8594; General Options*

---

