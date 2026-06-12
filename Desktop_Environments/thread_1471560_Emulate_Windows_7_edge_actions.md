---
title: "Emulate Windows 7 edge actions"
date: 2010-05-03
forum: Desktop Environments
---

### Post by TommyBrunn on 2010-05-03
I would really like to configure compiz to emulate the Windows 7 edge actions. In case you haven't used Windows 7, the actions I'm interested in are:
Drag window to top of the screen - maximize
Drag window to left side of screen - take up the left half of the screen
Drag window to right side of screen - take up the right half of the screen

Those are really the only ones I care about. I know I used to be able to do this in Karmic, but I forgot to back up my compiz settings when installing Lucid, and I can't remember how I had it configured before.

Any help would be appreciated!

---

### Post by steveneddy on 2010-05-03
Is that maximumize?

---

### Post by xDarkicex on 2010-05-03
Compiz has some snapping features Like win7's Snap

---

### Post by DomesDKG on 2010-05-03
What is compiz?

---

### Post by krazyd on 2010-05-03
Switch to KDE. All those actions are available and more.

---

### Post by TommyBrunn on 2010-05-04
> **steveneddy said:**
> Is that maximumize?
Yeah, that's totalletely maximumize.

> **xDarkicex said:**
> Compiz has some snapping features Like win7's Snap
Okay. But I'm looking for the edge effects, and a way to resize the application that's being dragged.

> **krazyd said:**
> Switch to KDE. All those actions are available and more.
I'm afraid I'm not interested in switching to KDE at the moment.

---

### Post by stinkeye on 2010-05-04
> **TommyBrunn said:**
> I would really like to configure compiz to emulate the Windows 7 edge actions. In case you haven't used Windows 7, the actions I'm interested in are:
Drag window to top of the screen - maximize
Drag window to left side of screen - take up the left half of the screen
Drag window to right side of screen - take up the right half of the screen

Those are really the only ones I care about. I know I used to be able to do this in Karmic, but I forgot to back up my compiz settings when installing Lucid, and I can't remember how I had it configured before.

Any help would be appreciated!

This post shows you how to set it up with compiz.
It's probably an update of what you were previously using,where in this version, the edge button triggers only on mouse release.
You'll need to install wmctrl.
```
sudo apt-get install wmctrl
```

[**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=9190800&postcount=45[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=9190800&postcount=45")

---

### Post by TommyBrunn on 2010-05-04
> **stinkeye said:**
> This post shows you how to set it up with compiz.
It's probably an update of what you were previously using,where in this version, the edge button triggers only on mouse release.
You'll need to install wmctrl.
```
sudo apt-get install wmctrl
```

[**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=9190800&postcount=45[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=9190800&postcount=45")

Thank you! That is exactly what I was after!

---

