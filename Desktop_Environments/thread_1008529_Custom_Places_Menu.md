---
title: "Custom Places Menu"
date: 2008-12-11
forum: Desktop Environments
---

### Post by Dangulica on 2008-12-11
Hello all,

How can I add a new entry in the Places Menu?
I don't need a simple bookmark.
I need something like this:

Places 
|
My Custom Folder 1 -> My custom file1 
|
My Custom Folder2  -> My custom file 2
.
.
.

In which My custom file x is a symlink to a local file.

I hope you understand what I need.

Thank you.

---

### Post by Dangulica on 2008-12-12
Anyone? Any ideea?

---

### Post by Wolki on 2008-12-12
As far as I know that's not possible yet.

---

### Post by derklempner on 2008-12-12
Just open Nautilus (any file browsing window) and drag the folder you want to add into the left pane.  Open your "Places" menu and you'll see the newly-added folder.

---

### Post by Wolki on 2008-12-12
> **derklempner said:**
> Just open Nautilus (any file browsing window) and drag the folder you want to add into the left pane.  Open your "Places" menu and you'll see the newly-added folder.

Sure, but he's asking about putting individual files in a submenu, which I don't think is possible.

---

### Post by Dangulica on 2008-12-12
Ok, forget about the "Places" menu.

Is it possible to create a custom menu, in which to put symlink to files?
I managed to create custom menus and submenus, but I don't know how to assign a file as an item in that menu. 
I can add a aplication to that custom menu, but not a file. 

Is this also not possible?

---

### Post by cb34 on 2008-12-12
i use awn(bzr), and there is a STACK applet in there where you have a list pop up that you can link any files u want in there for quick access. :)

---

### Post by Dangulica on 2008-12-12
Can I use AWN if I don't use (and don't want to use) Compiz or any Visual Effects?

---

### Post by cb34 on 2008-12-12
sorry man. wasn't thinkin. forgot not everyone uses compiz. :p

AWN needs 3d effects to work, you're right.

---

### Post by Dangulica on 2008-12-15
Any other ideea? I'm stuck and I really need this menu.

---

### Post by Wolki on 2008-12-16
> **Dangulica said:**
> Any other ideea? I'm stuck and I really need this menu.

You could try adding new applications to the menu, then use the filename as a parameter.

For example, to add an entry for an odt file called "test.odt" in your home, you add a new menu entry and use "oowriter /home/yourusername/test.odt". You need to be careful with spaces in file/directory names though, these have proven idfficult in my limited testing and you might need to encode the file name as an url.

---

### Post by Dangulica on 2008-12-23
Yes, it worked. :D

Thank you

---

