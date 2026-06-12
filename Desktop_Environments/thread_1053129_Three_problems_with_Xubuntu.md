---
title: "Three problems with Xubuntu"
date: 2009-01-28
forum: Desktop Environments
---

### Post by Tomás Ó hÉilidhe on 2009-01-28
1: When I drag-and-drop a file from one directory to another, it gets copied instead of moved. How to I change it so that it gets moved? (Don't offer me a solution of holding down shift, I want "move" to be the default behaviour)

2: The clipboard gets wiped when I exit an application. Let's say I open up mousepad and write "I like the dog". I select the text and hit copy. Then I close mousepad. Next I open a new instance of mousepad, and I go to paste the text, but the clipboard is empty. How to I stop this mysterious behaviour? I don't want the clipboard to get wiped when a program exits.

3: DVD playback is sluggish and choppy, both in VLC and Totem (though I suspect this is something indepedent of the desktop environment). Any ideas on how to fix DVD playback?

Sorry, one more thing I forgot to add:

4: OpenOffice looks horrible, as if it were running on Win 3.11 for Workgroups. How should I go about having it "skinned"? Is it something to do with enabling skinning for KDE applications? By the way I'm using Compiz and Emerald at the moment on my Xubuntu installation.

---

### Post by adamlau on 2009-01-28
1. Ctrl+x, Ctrl+v (versus d&d)
2. sudo apt-get install xfce4-clipman-plugin
3. SMPlayer w/ 2-4MB of DVD cache
4. sudo apt-get install openoffice.org-gtk

---

### Post by Tomás Ó hÉilidhe on 2009-01-28
> **adamlau said:**
> 1. Ctrl+x, Ctrl+v (versus d&d)

Is there really no settings file that can be edited? I've heard that Mint Xfce can do "move" on drag-on-drop, but I can't find out where the setting is.

> 2. sudo apt-get install xfce4-clipman-plugin

I've already got it installed, and I'm having the same clipboard problems.

> 3. SMPlayer w/ 2-4MB of DVD cache

Downloading it right now, I'll let you know how it goes :)

> 4. sudo apt-get install openoffice.org-gtk

This worked a charm, thanks :)

---

### Post by Tomás Ó hÉilidhe on 2009-01-29
I solved the clipboard problem.

1: Right-click a panel and click "Add New Item".
2: Select "Clipman" and hit Add.
3: Check the box that says "Save Clipboard contents on exit".
4: Hit OK.

Done. Not only that, but you've got a handy little icon that shows the history of your clipboard, I love it.

---

