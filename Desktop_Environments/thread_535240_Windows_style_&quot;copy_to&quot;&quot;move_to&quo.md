---
title: "Windows style &quot;copy to&quot;/&quot;move to&quot; menu in Nautilus"
date: 2007-08-26
forum: Desktop Environments
---

### Post by zanadou on 2007-08-26
There's a similar thread [here]("http://ubuntuforums.org/showthread.php?t=525304") that talks about this, but now it's marked as "solved". Well, not completely enough for me...

I'm looking for a way to make a windows style "drag-with-the-right-button-let-go-and-select-copy-to-or-move-to" menu in Nautilus.

In that thread above, it was written:

> **logos34 said:**
> You don't need a script, there's a keyboard shortcut: hold down the Alt key and drag 'n drop the file from the main window to the destination dir in the side pane tree.  Select 'move' or 'copy'

That's what I'm looking for, but I'm now wondering if I can evoke it without using the alt key, in the above, right-clicking manner. Ideas?

(The solution should be added into Gutsy Gibbon I reckon; it's almost a shop-stopper for windows converts like me.)

---

### Post by Wolki on 2007-08-26
> **zanadou said:**
> That's what I'm looking for, but I'm now wondering if I can evoke it without using the alt key, in the above, right-clicking manner. Ideas?


Not by right-clicking, but by middle-clicking (usually the scroll wheel). Or, if you have 3-Button-Emulation enabled (which I think is default in Ubuntu), by dragging with both buttons.

If you wonder why, there's a reason. If this was put onto the right button, you couldn't popup the right-click menu when you press the mouse button, as the system wouldn't know whether you want to open the context menu or right-click drag. This would not only be inconsistent with the standard drop-down menus which open on mouse-down, but also make some ways of using context menus impossible, for instance, click-and hold, then release the mouse button over the correct menu entry.

---

### Post by disraeli on 2007-11-07
Great to hear this can be done with the middle-button!

---

### Post by Samhain13 on 2007-11-07
I've been using Ubuntu since Edgy and I only learned this now. Simple as it is, it's very, very useful especially "link here", which I've always done via command line. Thanks for the info! :D

---

### Post by juamez. on 2007-11-17
Is there a way to also add "extract here" to the same context menu? Because that would also be an option in windows if you have for example WinRAR or 7zip installed.

I kind of miss that in ubuntu, although it's great to see I can move and copy (and link!) with a drag+rightclick, which I thought was not possible at first.

---

### Post by mjpoetic on 2007-12-13
If this is of any interest to you all...some one made a patch for nautilus to enable a Windows-style "copy to move to" menu.  Here it is but I have no idea how to apply patches or anything:

[http://www.mail-archive.com/nautilus-list@gnome.org/msg04040.html](http://www.mail-archive.com/nautilus-list@gnome.org/msg04040.html)

---

### Post by OzzyFrank on 2007-12-16
Never would have thunk it, so many thanks for that tip. Just assumed if you couldn't right-drag, then it couldn't be done (without holding the Ctrl or Shift key and using the left mouse button, which is how I worked around it). The scroll wheel as a button in Windows is generally useless, so didn't even think to try it in Ubuntu.

As for the question about "Extract here"... I thought that was an option already when you right-click a file. Pretty sure I've done that plenty of times in both Nautilus and Thunar. And that was without installing anything extra, like you do in Windows. Pretty sure it is a default feature in Ubuntu in the standard (ie non-drag) context menu when right-clicking archives.

Also interesting to read about 3-button emulation, and it (probably) being enabled by default. Cheers guys.

---

### Post by oomingmak on 2007-12-17
> **Wolki said:**
> If this was put onto the right button, you couldn't popup the right-click menu when you press the mouse button, **as the system wouldn't know whether you want to open the context menu or right-click drag.**
That limitation may apply to Linux, but it certainly does not in Windows. So it most definitely is not a case of it being impossible for a "system" to differentiate between the two actions.

Just as the left mouse button has clicking actions (to open items) and also dragging actions (to move items) with both of these actions being accessed using the same mouse button, then likewise this can also apply to the right mouse button. Dragging and clicking are easily distinguished.

I personally find it totally inconsistent to have to use the middle button for context menus on drag-actions (and it's even more annoying given that my middle button is a mouse wheel which keeps rolling while I am trying to click on it).

---

### Post by Wolki on 2007-12-17
> **oomingmak said:**
> That limitation may apply to Linux, but it certainly does not in Windows. So it most definitely is not a case of it being impossible for a "system" to differentiate between the two actions.

Now, I haven't really used Windows in years, but if I remember correctly they open the context menu on mouse-up, which was my point.

> Just as the left mouse button has clicking actions (to open items) and also dragging actions (to move items) with both of these actions being accessed using the same mouse button, then likewise this can also apply to the right mouse button. Dragging and clicking are easily distinguished.

Both operating the context menu and drag&dropping can be dragging actions, similar to how you can operate drop-down menus by dragging, then releasing over the correct menu entry.

---

### Post by phenest on 2007-12-17
> **Wolki said:**
> Both operating the context menu and drag&dropping can be dragging actions, similar to how you can operate drop-down menus by dragging, then releasing over the correct menu entry.

Not true. Drag & Drop is only initiated if the cursor moves a specific amount of pixels on mouse down.

To further the OP's question: What if I don't have a mouse? What if I'm using a stylus on a tablet pc? Left click is by tapping the stylus on the screen, and right click is by holding the stylus button and tapping on the screen. Obviously, I cannot do both. So how do I middle click? Mapping the stylus button to a mouse middle button is no good, because then I can't right click.

---

### Post by OzzyFrank on 2007-12-17
OK, while it may be incosistent with Windows, it's easy enough to get used to. I personally haven't had any problems, and if the wheel rolls some, it doesn't seem to matter. Agreed that this way of "right-dragging" isn't a necessity, as I can name one other system that can differentiate between dragging with the right mouse button and just clicking it. It is obviously just the Linux way of doing things. And it really isn't that hard to get used to it.

---

### Post by Wolki on 2007-12-17
> **phenest said:**
> Not true. Drag & Drop is only initiated if the cursor moves a specific amount of pixels on mouse down.

Sure, you can distinguish a click from a drag. That's not what I'm saying. You can't really distinguish a right-click drag from a right-click hold, drag & release menu activation. Try it. You can hold down the right button, and the menu will instantly open. Move the cursor to the menu entry you want to activate, and release the cursor. That entry will be activated. Drop-down menus work the same way; obviously a two-click method is also possible in both cases.

---

### Post by phenest on 2007-12-18
> **Wolki said:**
> ...You can hold down the right button, and the menu will instantly open. Move the cursor to the menu entry you want to activate, and release the cursor. That entry will be activated. Drop-down menus work the same way; obviously a two-click method is also possible in both cases.

So when you right click, you are holding the button down? That's not how I do it. I right click and release, move the cursor over the menu and left click the option. Because of that method, it is perfectly possible to distinguish different actions.

---

### Post by phenest on 2007-12-18
> **OzzyFrank said:**
> It is obviously just the Linux way of doing things. And it really isn't that hard to get used to it.

Not the Linux way, more the Gnome way, as it is Gnome that is responsible for how you use the mouse. And it's not a question of getting used to it, because what if you don't have that many mouse buttons? See my post about using a stylus on a touch screen.

---

### Post by oomingmak on 2007-12-18
> **OzzyFrank said:**
> OK, while it may be incosistent with Windows, it's easy enough to get used to.
The problem is not that this behaviour is inconsistent with Windows, but that it is inconsistent with **itself**.

Allowing the use of the right mouse button to *activate *menu items, but not allowing it for other items (such as icons for example) is inconsistent. Likewise, requiring a right-click for context menu activation under certain circumstances but requiring a mid-click under other circumstances (e.g. when dragging) is not only counter-intuitive, but also not discoverable (which this thread is testament to).

Not that this surprises me, I mean Gnome can't even implement left clicking consistently through their interface. Single-click users are forced to repeatedly double-click in GTK dialogs and therefore have to remember to keep switching back and forth between one and two clicks (for no reason whatsoever). 

A bug was filed about this nearly 8 years ago (and a patch submitted in the interim) and yet the problem still exists because nobody with commit access will do anything about it.


> **phenest said:**
> Not the Linux way, more the Gnome way...
Exactly.

---

