---
title: "way to modify gnome kbd shortcuts from cmd line?"
date: 2006-08-29
forum: Desktop Environments
---

### Post by zeus77 on 2006-08-29
As a possible solution to an unresolved [problem]("http://ubuntuforums.org/showthread.php?t=244366") I've been having, is there a way to modify the gnome keyboard shortcuts from the command line?

For example, suppose I wanted to change the window-switching behavior from Alt-Tab (the default) to something like Alt-1.  The usual GUI route is to go System-->Prefs-->Kbd Shortcuts.  But is there a way to do it from the command line?

Thanks.

---

### Post by lagagnon on 2006-08-29
I think you would have to manually edit a file such as:
~/.gconf/apps/gnome-terminal/keybindings

It may not be that exact file, but something similar. Hunt around till you find it.

---

### Post by luopio on 2006-08-30
I was also having a problem with gnome-keybindings: could not set alt+p to start rhythmbox - it would not accept alt as modifier even though the settings GUI showed "<Alt>p". Instead it just used "p", which of course didn't work that well...

BUT I scoured the forums and ran into this howto: [http://ubuntuforums.org/showthread.php?t=79560](http://ubuntuforums.org/showthread.php?t=79560)

xbindkeys really does the trick and now my alt+p works on all my different DEs :D

---

### Post by zeus77 on 2006-09-03
Thanks for the leads.  Turns out, the Alt-Tab window switching is a metacity thing.  The relevant config file was 
[INDENT]~/.gconf/apps/metacity/global_keybindings/%gconf.xml[/INDENT]
and the window-switching behavior can be changed with this command (this example obviously sets it Alt-Tab, the default):
```
gconftool-2 -t string -s /apps/metacity/global_keybindings/switch_windows "<Alt>Tab"
```
Can also be done with the gconf-editor GUI, which is useful for finding the names of all the shortcuts.  Thanks again.

---

