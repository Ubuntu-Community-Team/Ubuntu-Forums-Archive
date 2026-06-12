---
title: "compiztray"
date: 2007-11-12
forum: Desktop Effects &amp; Customization
---

### Post by coloured on 2007-11-12
I am running gutsy and have installed the compiztray software package from synaptic.
when I run compiztray I lose all my window decorations and the only way to get it back is by running metacity --replace, then go into system<preferences<gl desktop and re-enable gl desktop.

this is the output of compiztray from a terminal.
> jbaier@jbaier-laptop:~$ compiztray
Your language translation is not available.
I'll use your default language UI.
Process handled:  [[6171, 'compiz'], [6265, 'compiz.real']]
Compiz cannot find the specified window decorator
There's any previously initialized compiz?  True
Decorator: emerald
Calling WM; ['compiz.real', 'compiz.real', '--replace', 'ccp']; STARTED (PID 6587).
Waiting 15s to clear...
Window manager was restarted.
Killing useless process...
    PID 6171 ( compiz ) cannot be killed.
    PID 6265 ( compiz.real ) cannot be killed.
Compiz tray started.
Calling DECORATOR; ['emerald', 'emerald', '--replace']); STARTED (PID 6688).
Waiting 15s to clear loop...
compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz.real (core) - Error: Failed to manage screen: 0
compiz.real (core) - Fatal: No manageable screens found on display :0.0
Killing useless process...
    PID 6171 ( compiz ) has been killed.
    PID 6265 ( compiz.real ) has been killed.
    PID 6264 ( emerald ) has been killed.
Cleanning children...
    Nomore to clean.
Traceback (most recent call last):
  File "/usr/bin/compiztray", line 1154, in <module>
    gtk.main()
KeyboardInterrupt


---

### Post by Flare183 on 2007-11-13
Try reinstalling compiz.

---

