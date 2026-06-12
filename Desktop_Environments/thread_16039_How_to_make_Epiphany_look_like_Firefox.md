---
title: "How to make Epiphany look like Firefox?"
date: 2005-02-18
forum: Desktop Environments
---

### Post by Buffalo Soldier on 2005-02-18
I think both browser has it's own pro and cons, and I hope this doesn't turn into a Epiphany vs Firefox thread :)

Now I'm trying to make my Epiphany looks more like a Firefox. I'm getting there (about 60%), but I think there's still a lot more to be done.

The changes that I made is to the *~/.gnome2/epiphany/**epiphany-toolbars-2.xml*** file.

```

<?xml version="1.0"?>
<toolbars version="1.0">
  <toolbar name="Toolbar">
    <toolitem type="application/x-toolbar-item" name="NavigationBack"/>
    <toolitem type="application/x-toolbar-item" name="NavigationForward"/>
    <toolitem type="application/x-toolbar-item" name="ViewStop"/>
    <toolitem type="application/x-toolbar-item" name="ViewReload"/>
    <toolitem type="application/x-toolbar-item" name="Location"/>
    <toolitem type="_NETSCAPE_URL" name="http://www.google.co.uk/search?q=%s&amp;ie=UTF-8&amp;oe=UTF-8"/>
  </toolbar>
</toolbars>

```

and here is how my Epiphany looks now. Anyone can suggest what else can I do/tweak?

EDIT:

Earlier changing Menu & Toolbars settings didn't change Epiphany toolbar setings. But now it did. I'm not sure why only now it manage to that, but I assume earlier I was messing with the config file and that intefered with the Menu & Toolbar settings.

---

### Post by Jad on 2005-02-18
LoL
Good work man, but still to way from FireFox

---

### Post by Buffalo Soldier on 2005-02-18
[QUOTE=Jad]LoL
Good work man, but still to way from FireFox[/QUOTE]
 Can't argue with that Jad :)

Right now I'm trying to set the toolbar so that it shows only icons and no text. I've tried ```
<toolbar name="Toolbar" **style="icons-only"**>
```
and it does show only icons on the toolbar, when I ran Epiphany once. Any restart of Epiphany would revert the toolbar back to icon+text :(

EDIT: solved that already. The cause of the problem is my own stupidity :)

---

