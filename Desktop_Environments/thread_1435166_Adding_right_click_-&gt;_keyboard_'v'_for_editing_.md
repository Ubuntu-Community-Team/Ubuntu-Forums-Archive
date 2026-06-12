---
title: "Adding right click -&gt; keyboard 'v' for editing a file with gvim in nautilus"
date: 2010-03-21
forum: Desktop Environments
---

### Post by madiyaan on 2010-03-21
Hello,

Kind of new to Ubuntu. In windows when I install gvim/vim, it automatically installs a context menu in explorer that lets me edit a file in gvim by simply right clicking and pressing v. 

For someone who edits a lot of files and is really used to vim, it is super-convenient. 

I want to do the same thing in nautilus. 

So I installed nautilus-actions and added to the context menu of editing with gvim. That wasn't hard. The hard part is getting that keyboard key to bind to that context menu item. Currently when I right click and press v, it sends the item to trash. I want it such that when I right click a file and press v, it edits the file in gvim. 

How can I do that? I want a good solution, and am willing to switch file managers/window managers if need be. This particular shortcut key is very important to my user experience.

Thanks,

---

### Post by Smylers on 2010-09-02
> **madiyaan said:**
> In windows when I install vim, it automatically installs a context menu in explorer that lets me edit a file in gvim by simply right clicking and pressing v. ... I want to do the same thing in nautilus. 

So I installed nautilus-actions and added to the context menu of editing with gvim. ... Currently when I right click and press v, it sends the item to trash. I want it such that when I right click a file and press v, it edits the file in gvim.

Thanks for that information; it helped me get as far as the above.

I guessed how to set the menu accelerator keystroke: put an underscore just before the relevant character in the menu title, such as ‘Edit with _Vim’. That underlines the ‘V’ in the context menu (press F5 to refresh an open window), but unfortunately because ‘Move to the Deleted Items folder’ already uses V as well, pressing V now cycles between these entries.

So launching Vim on a file requires right-click, then V V Enter.

Anybody know how to remove the menu item that already uses V? Or change its accelerator letter?

For the time being I'm going with ‘_Edit with Vim’, because E doesn't seem to conflict with any of the standard items' accelerators.

---

