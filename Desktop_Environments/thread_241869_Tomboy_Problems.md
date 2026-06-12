---
title: "Tomboy Problems"
date: 2006-08-22
forum: Desktop Environments
---

### Post by bparham on 2006-08-22
When I try to start tomboy I get the following error message...

```

&#65279;Trying Plugin: Evolution.dll ... EvolutionPlugin. Done.
Trying Plugin: ExportToHTML.dll ... ExportToHTMLPlugin. Done.
Trying Plugin: PrintNotes.dll ... PrintPlugin. Done.
Tomboy remote control active.
EnableDisable Called: enabling... True
Binding key '<Alt>F12' for '/apps/tomboy/global_keybindings/show_note_menu'

(Tomboy:14607): libtomboy-WARNING **: Binding '<Alt>F12' failed!

Binding key '<Alt>F11' for '/apps/tomboy/global_keybindings/open_start_here'

(Tomboy:14607): libtomboy-WARNING **: Binding '<Alt>F11' failed!
```

Any ideas?

---

### Post by Scunizi on 2006-09-05
I get the exact same error and I thought it had something to do with me screwing up my top panel.  I've tried re-installing it with no change.  I haven't tried un-installing it because I really don't want to loose all my notes.  Hopefully someone will come up with a fix.:-|

---

### Post by Scunizi on 2006-09-05
I just figured out the answer.  Right mouse click in the top panel and add "Notification Area".  That did the trick for me.  All of a sudden I got the Tomboy icon appearing and functional!

---

### Post by kerry_s on 2006-09-06
Right click tomboy and uncheck the last preference for keyboard input. I think that is what that message is. I switched to xpad instead it smaller and doesn't start all those extra apps, It's like post it notes..

---

