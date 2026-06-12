---
title: "Remove window decorations from a specific application"
date: 2010-03-15
forum: Desktop Environments
---

### Post by seecanadarun on 2010-03-15
Hello all,

I'm trying remove window decorations (title bar etc..) from rdesktop but cannot figure out how. I've done google searches and a brief survey of the forum but cannot find anything that helps.

Any ideas?

Also, using the -D option in rdesktop will not suffice.

---

### Post by Neil Woolford on 2010-03-26
I'm also looking for how to do this for the BBC iplayer Desktop.

It is a flash application and has its own minimize, maximize and close buttons.  Using the buttons on the window enclosing it causes trouble...

This may be a temporary problem with the 10.04 beta.

---

### Post by Jose Catre-Vandis on 2010-03-26
**devilspie** is your friend for this one

For example the Mplayer.ds file on my PC:
```
(if
   (is (application_name) "MPlayer")
   (begin
      (undecorate)
      (geometry "+950+50")
   )
)
```
removes the window decoration and opens the app near the top right hand corner of a 1280 x 1024 screen

---

### Post by asmoore82 on 2010-03-26
> **seecanadarun said:**
> Hello all,

I'm trying remove window decorations (title bar etc..) from rdesktop but cannot figure out how. I've done google searches and a brief survey of the forum but cannot find anything that helps.

Any ideas?

Also, using the -D option in rdesktop will not suffice.

You can toggle fullscreen at any time in `rdesktop` with <Ctrl><Alt><Enter>

---

### Post by Neil Woolford on 2010-03-26
Thanks Jose.  That looks much what we need.

Neil

---

### Post by stinkeye on 2010-03-26
If your using compiz, in ccsm
go to effects > window decoration
click on the add button for decoration windows
grab your window and mark the invert option

You should have something similar to this
```
(any) & !(class=Terminator)
```

---

### Post by nocnokneo on 2010-08-18
Thanks! This works great for Boxee:
```
(any) & !(class=Boxee)
```

---

