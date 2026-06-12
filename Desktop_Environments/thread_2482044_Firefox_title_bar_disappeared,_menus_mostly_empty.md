---
title: "Firefox title bar disappeared, menus mostly empty"
date: 2022-12-17
forum: Desktop Environments
---

### Post by peyre on 2022-12-17
I turned on my computer last night and opened Firefox as usual, and the browser's all messed up.  The title bar is missing, and most of the menu items are blank, including--all my bookmarks are gone.  The minimize, restore, and close icons in the top left are also gone, though they outline if I hover the mouse over them.  It's a hell of a thing to come home to after a long day at the office.  Anyone know what to do about it?  I've tried removing and reinstalling in Synaptic, but it just goes back to the same behavior.

[ATTACH=CONFIG]291420[/ATTACH]

---

### Post by matthewrkarlsen on 2022-12-18
Hello peyre,

Does this affect other applications too?

If it is just Firefox, when you open Firefox, can you get to your bookmarks using Ctrl + Shift + O?

 If so, you could export them, and then rename the **[FONT=courier new].mozilla[/FONT]** directory in your home folder to **[FONT=courier new].mozilla-removed[/FONT]**

If you do this, once you restart Firefox it will generate a new configuration. You could then re-import the bookmarks with Ctrl + Shift + O followed by "Import Bookmarks From HTML".

I know it's a nuisance, and you'd have to reinstall add-ons, but it might get you back to a usable state?

(Ctrl + H in Thunar toggles visibility of hidden folders.)

Edit: As peyre's other poster makes apparent, this approach will only work with versions of Ubuntu before Ubuntu 21.10 (which moves over to snaps).
I don't use snaps, but the article [https://askubuntu.com/questions/1414757/where-does-firefox-snap-store-the-profiles](https://askubuntu.com/questions/1414757/where-does-firefox-snap-store-the-profiles) indicates that the relevant path would be different than that mentioned above.
Anyway, see peyre's post for an actual solution...

Regards,
Matthew

---

### Post by peyre on 2022-12-18
This is weird!  Someone responded to me yesterday, and said among other things that if it's a snap app he didn't know what to suggest.  That gave me an idea...Firefox does seem to be a snap, so I looked up how to fix/reinstall snaps.  I ran

sudo snap remove firefox
sudo snap install firefox

and that did it.  It erased my bookmarks, add-ins, and settings, but I can replace those.  I marked this as Solved, but it seems to have lost that somehow, as well as the other two posts.  Odd, I'll try marking it solved again.  Thanks for coming on to help!

---

