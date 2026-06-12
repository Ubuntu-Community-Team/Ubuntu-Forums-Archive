---
title: "Menu doesn't update when changes are made, until you log out and in..."
date: 2006-09-10
forum: Desktop Environments
---

### Post by kendals on 2006-09-10
Hiya guys.

Running 6.06 Dapper Drake, and I've found that when I edit the menu with Alacarte, it doesn't update unless I log out and back in again. This is a tad annoying.

An example would be adding some programs that are in the list in the Alacarte Menu Editor, they don't appear in my list sometimes, without logging out and back in.

Any ideas? :-\"

---

### Post by mhancoc7 on 2006-09-10
You could try this:

Open Terminal and run this command:

sudo killall gnome-panel

This will restart the gnome-panel. I have found that it updates my menu as well.

Jereme

---

### Post by kendals on 2006-09-10
Hey, I tried that, and although it refreshed my panel, it also took away things like checkgmail, network manager, etc., in my panel area, and it did not refresh my menus :(

Thanks though :)

---

### Post by kendals on 2006-09-10
While I've got you, is there a way to open programs from the terminal, and then close the terminal without the program closing as well?

---

### Post by mhancoc7 on 2006-09-10
You know, I saw the answer to this a while back. I will have to look for it again. :)
Jereme

---

### Post by kendals on 2006-09-10
Thanks. I couldn't find anything, so any help would be great :)

---

### Post by mhancoc7 on 2006-09-10
Well, you could just use Alt-F2 to run the program without the terminal.

I am still looking for the solution though.

Jereme

---

### Post by mhancoc7 on 2006-09-10
Ok, I think I found it.

Just add nohup before the command.

Example:

nohup gedit

This will open gedit, and when you close the terminal gedit is still open.

Hope that helps, Jereme

---

