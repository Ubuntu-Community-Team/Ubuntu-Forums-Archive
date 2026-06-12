---
title: "Window Focus (lack thereof)"
date: 2007-12-16
forum: Desktop Environments
---

### Post by Mikebert on 2007-12-16
I've put up with this for a long time on different ubuntu editions, but I can't stand it anymore.  Does anyone have a solution or quick fix?  

When one program opens a new program to display a file, the new window is not focused.  It sits in the background until I bring it up.  Example:

Surfing the web in Firefox and videos open in mplayer/vlc in the background.

I'm using Gnome, but like I said, I've seen this happen everywhere.  It's infuriating to no end.  It doesn't matter if the document opens in a new instance of a program or it opens within an existing instance of a program, the window focus never changes to what I just opened.  Any ideas?

---

### Post by erfahren on 2007-12-17
I was watching this thread for awhile to see if anyone had an answer.

I didn't want to just make a "I know what you mean" post

but..., I know what you mean

seriously though, I had that problem with Gutsy and tried to look into it a little, and looked through the configuration editor as well.

I've since reverted to Feisty (for other reasons) and am not really having that problem. I wasn't really sure at the time if it was something in Gutsy's configuration options or with Compiz Fusion.

Anyway, I do offer something here. I took a look at the gconf-editor again and found this:
under apps > metacity > general there are some settings for window focus. One in particular got my attention: "focus_new_windows" and it's set to "smart" - you might take a look at that.

---

### Post by Mikebert on 2007-12-17
Thanks for the heads up; I looked in the metacity settings saw what you referred to, but it does not help (the gconf-editor description explains how it works).  I'm using compiz, so the issue should be there, and not metacity, right?

---

### Post by erfahren on 2007-12-17
yep, I bet the problem is with Compiz Fusion, that seems much more likely.

---

### Post by Mikebert on 2007-12-18
Yeah I know it happens more times than in firefox.  Another example I pinned down last night is when you're browsing nautilus and open pictures, the default viewer opens in the background.  Just in case someone out there wants to verify that it's not just me.

---

### Post by tehschulman on 2007-12-25
I'm having this issue too and it's really beginning to bug me. In my case it happens when a window currently has focus. If I open anything while, say, browsing firefox or using my file manager, it will pop under the current window instead of pop over which I would like. If nothing has focus however the window will pop over without a problem. It'd be nice to have the pop over action happen in both instances.

---

### Post by Hairy_Palms on 2007-12-25
i like that behaviour, when things steal focus its annoying, synaptic is the worst candidate for that as when it finishes downloading and starts installing it steals focus from whatver else im doing.

---

