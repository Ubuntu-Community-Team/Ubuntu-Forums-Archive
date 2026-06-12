---
title: "[SOLVED] compiz config corruption"
date: 2007-11-24
forum: Desktop Effects &amp; Customization
---

### Post by MegaJim on 2007-11-24
I keep having serious issues with the compizconfig-settings-manager.

It seems the more I customise things, the higher the chance of the whole thing "breaking" and I end up with random things happening.

Here is a list of the kind of corruption I have experienced:
[LIST]
[*]Window borders invisible
[*]Window borders visible, but not clickable / interactive
[*]Alt+Drag window stops working
[*]Virtual desktops disappear
[*]Shortcut keys fail to work (e.g alt+f2 for run and switch desktop keys)
[*]Whole screen being redrawn smaller but with cursor still moving to the edges of the monitor
[*]Plugins randomly turning on and off/settings changing
[/LIST]

The only option I have to fix this is to use the CCSM to restore everything to defaults... which is a bummer !

Am I the only one?

Some info:

The problem box is running feisty on dual 7600 nvidias, restricted driver and no other graphical issues as far as I'm aware.
compiz-fusion is from Amaranth's repository.  Read something about changing the configuration backend - will try that and see how it goes.

---

### Post by Forlong on 2007-11-24
Yeah, just switch to the flat-file backend in ccsm.
The default gconf-keys in Feisty (for the pre-installed Compiz) interferes with other versions.

---

### Post by MegaJim on 2007-11-24
> **Forlong said:**
> Yeah, just switch to the flat-file backend in ccsm.
The default gconf-keys in Feisty (for the pre-installed Compiz) interferes with other versions.

Thanks mate, hey your blog is really good ! :)

Marking as solved as it seems to have stopped the corruption, cheers!

---

