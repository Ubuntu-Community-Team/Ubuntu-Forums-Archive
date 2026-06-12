---
title: "Calling Gnome3 guru's - need help tweaking the dock - multiple 'like'window instances"
date: 2012-04-12
forum: Desktop Environments
---

### Post by miatawnt2b on 2012-04-12
I am really growing to like the new Gnome3 desktop. I like the application search and the dock a lot. In the past I've used cairo and awn pretty extensively, and there is one feature that I can't seem to replicate in Gnome3. 

with cairo, if you have multiple windows of the same application running, hovering the mouse over the dock icon will auto-expand the icon so that you can easily select one of the open windows.

Also, in cairo, holding shift and clicking will open another instance of the app.  I make heavy use of terminals, and can't seem to find an easy way with the gnome3 dock to do this other than a right click and select open new on the dock. Too many steps for my liking.

So I'd like some help from you Gnome3 guru's out there.  How can I get these features?

-J

---

### Post by markbl on 2012-04-12
> **miatawnt2b said:**
> 
with cairo, if you have multiple windows of the same application running, hovering the mouse over the dock icon will auto-expand the icon so that you can easily select one of the open windows.

Unity has this functionality but not Gnome-shell, at least yet. However, the easiest way to see and select from all your open windows of the same application is just to press ALT+[key above tab] while on a window of that app (and/or press ALT+tab to get to the app first). This same scheme works in gnome-shell, Unity, and Max OSX at least. "Key above tab" is the backtick key for US keyboards.

> 
Also, in cairo, holding shift and clicking will open another instance of the app.  I make heavy use of terminals, and can't seem to find an easy way with the gnome3 dock to do this other than a right click and select open new on the dock. Too many steps for my liking.

CTRL+click does that in gnome-shell.

Note that Unity and gnome-shell both provide also the default keyboard CTRL+ALT+t to open a terminal window which I think it ultimately quicker and easier.

---

### Post by saponempotenti on 2012-04-13
Was watching this thread, thanks for the info!

---

### Post by kiirokurisu on 2012-04-13
We should add that the Ctrl+Alt+t shortcut currently doesn't work in Gnome-Shell under Ubuntu (known bug)

---

### Post by markbl on 2012-04-13
> **kiirokurisu said:**
> We should add that the Ctrl+Alt+t shortcut currently doesn't work in Gnome-Shell under Ubuntu (known bug)
Well I've used gnome-shell on ubuntu since 11.10 release and it works for me. It is set in Systems Settings/Keyboard/Shortcuts/Launchers/Launch Terminal. I don't even think I have ever set this explicitly myself but if I did then it was long ago and has always worked fine.

---

### Post by kiirokurisu on 2012-04-13
Sorry, to be precise (haha, pun intended) the bug is in the 12.04 beta release.

---

### Post by souravc83 on 2012-04-13
Yes, Ctrl+Alt+t works great in my 11.10.
This is how /i open the terminal.
Another easy way is to just type "gnome-terminal" after you go to the activities tab (either by clicking it, or just taking your mouse there).
You will need to type the first two or three words, probably only "gno" and you will see the terminal as the option.

I haven't tweaked the dock much yet. I don't like the dock at all.  and that was the reason I left Unity and am using Gnome 3.

---

### Post by markbl on 2012-04-13
> **kiirokurisu said:**
> Sorry, to be precise (haha, pun intended) the bug is in the 12.04 beta release.
I don't understand why people post about bugs in a beta release? Just does not make sense. You expect such bugs there and they have no relevance to a normal user.

---

### Post by markbl on 2012-04-13
> **souravc83 said:**
> Yes, Ctrl+Alt+t works great in my 11.10.
This is how /i open the terminal.
Another easy way is to just type "gnome-terminal" after you go to the activities tab (either by clicking it, or just taking your mouse there).
You will need to type the first two or three words, probably only "gno" and you will see the terminal as the option.

Typing "terminal" is much quicker given there are so many "gnome-*" programs on most of our systems, particularly gnome-shell users. For me, "t" brings up gnome-terminal first.

---

### Post by saponempotenti on 2012-04-13
Normal users don't need a windows like GUI?  The point of Ubuntu was to take a sophisticated OP and make it more user friendly.  Ubuntu with Gnome should be user friendly, and what he is asking if very "normal user" orientated imo.  Thanks for additional answers!

---

### Post by jerome1232 on 2012-04-17
> **saponempotenti said:**
> Normal users don't need a windows like GUI?  The point of Ubuntu was to take a sophisticated OP and make it more user friendly.  Ubuntu with Gnome should be user friendly, and what he is asking if very "normal user" orientated imo.  Thanks for additional answers!

He's talking about the posting of a bug that's only relevant to a testing version of Ubuntu. The bug should be worked out by release and is largely irrelevant to this thread which has nothing to do with 12.04.

---

