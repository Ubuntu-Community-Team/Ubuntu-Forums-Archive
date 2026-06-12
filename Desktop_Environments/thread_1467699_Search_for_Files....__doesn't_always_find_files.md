---
title: "Search for Files....  doesn't always find files"
date: 2010-05-01
forum: Desktop Environments
---

### Post by VanillaMozilla on 2010-05-01
That's right.  The file search menu entry misses files.  It's supposed to run the "locate" command, and then the "find" command, but by default the "find" command is effectively disabled.  Huh?  It turns out that "locate" only finds your file if it happens to be in a special database.  If that file is recently created, it might not be in the database, and the file is not found even if it exists.  The "find" command will not look in the root directory or any subdirectories--in other words, it won't look anywhere.

If you think this is treacherous and ought to be fixed, I'd appreciate a vote for the bug.  As a carrot I can offer you a simple workaround.  Read on.  (And if the bug affects no one, I'll move on.)

It's all described here, so you can try it out:
[https://bugzilla.gnome.org/show_bug.cgi?id=606993](https://bugzilla.gnome.org/show_bug.cgi?id=606993)
and here:  [https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/506219](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/506219) .

A workaround is described in the second link, comment 3.  In terminal type
gconf-editor
and find gnome-search-tool in the Apps.  Then look for the field quick_search_second_scan_excluded_paths and change the slash to nothing, i.e. delete the "/".

This problem has been going on for years, but the bug report seems to be rotting.  Gnome has had the report for several months, but they have shown no signs of life.  I don't know if it will help, but you can vote for the bug on the Ubuntu side by registering in Launchpad, then go to the second link and press the "This bug affects me" button.  That way it's not just me that's the squeaky wheel.

It's probably better not to comment in the bug report, though.  Those guys really don't like to be pressed.

---

### Post by VanillaMozilla on 2010-05-03
OK, let me try something different.

Let me know if you understood what I wrote.  I'm trying to find out, in my own way, how many people this affects.  Thanks.

---

