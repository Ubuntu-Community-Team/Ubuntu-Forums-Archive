---
title: "Gnome Applications menu killed by Main Menu editor (alacarte)"
date: 2007-12-13
forum: Desktop Environments
---

### Post by jollo on 2007-12-13
Hi everybody.

I ran across a problem with Ubuntu 7.04 (feisty) gnome desktop: while temporarily out of disk space, right clicked on Applications menu, clicked on Edit Menus, got a "Starting Main Menu" tab in the panel (bottom) for a few seconds but the Main Menu window did *not* open and since the Applications menu is *broken*: clicking on the menu title nothing drops down, just a small dot appears under the left side of the "Applications" title, where the menu should appear.

Alt-F1: same story. On reboot the desktop wallpaper disappeared (got reset to "no wallpaper"). The Run Application window (Alt-F2) shows an *empty* list of known applications! :( Adding a Main Menu to any panel creates a duplicate Applications menu with exactly the same problem: it looks "empty" - nothing drops down.

Other users are unaffected: their Applications menus show just fine. New users created after the 'incident' are given a perfectly good menu bar as well. Synaptic reports all packages are ok, though, and all applications work fine for all users (either through launchers of from the command line).

Rigth-clicking on the Applications menu and Edit Menus gets a "Starting Main Menu" tab in the panel (bottom) for a few seconds but the Main Menu editor does *not* open. Trying *sudo alacarte* from a terminal gives this error:

[I]Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 46, in __loadMenus
    self.applications.dom = xml.dom.minidom.parse(self.applications.path)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/minidom.py", line 1915, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py", line 926, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0[/I]

which seems to suggest that it failed to load some menu configuration (from where?). Trying to run alacarte as root gives:

[I]/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:69: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py:50: GtkWarning: cannot open display:  
  self.gnome_program = gnome.init('alacarte', version)[/I]

Following advice found in other threads, I tried to delete the .gconf and .gconfd directories in the home of the affected user and reboot: lost all launchers but the Applications menu remains empty. Also tried to reinstall the gnome panel (*sudo apt-get --reinstall install gnome-panel gnome-panel-data*) but only got back the default wallpaper.

My - uninformed - opinion is that the Main Menu editor (alacarte) corrupted the menu configuration while out of disk space and is since unable to start. Since the system looks otherwise sound, I would like to try and restore just that: can anyone advise where is the menu configuration stored (I would have thought within the affectd user's home, but not in .gconf or .gconfd) and how to - if possible - rebuild, copy (from another user) or revert to a "default" Applications menu?

Thanks in advance!

---

### Post by jollo on 2007-12-14
Ok, I got it back in working order.

The corrupted (empty) file was:

/home/*affecteduser*/.config/menus/applications.menu

Just copy the same file from a newly created user's home, edit it to show the *affecteduser* home path anywhere the original user's path is used (should be two places) and save: the Applications menu should now be now showing fine (no need to reboot).

While fixing this, I also learned that the individual user's menu dynamically includes a common file (*/etc/xdg/menus/applications.menu*): that's how all users get the same Applications menu.

Just a couple things:

1) IMHO alacarte is seriously flawed: a piece of software that corrupts a configuration file because the system is out of disk space (not a very exotic exception), *and* then silently fails to start because of the corrupted file (and no other way to fix it) is to be considered broken, and should be fixed. Ok, it's just a very simple ultility, but screwing the main menu can be distressing for inexperienced users or plain 'human beings', which is all Ubuntu is about, isn't it? :)

2) I am not impressed with the replies to this post: as a new member of this forum, I tried hard to follow the 'be as descriptive as possibile' guideline. Perhaps too much: looking around I noticed way too generic posts (like 'gnome menus are a pain in the a**') that got extensive assistance, discussion and so forth... Next time I'll try to be a little more misterious... :)

Thanks anyway for the forum administration: good job and useful info.

Take care

---

### Post by i_TheDevil_i on 2008-02-21
Thanks! Really helped =) Had the same problem =)

---

### Post by jollo on 2008-03-05
Glad it helped! In fact, in another thread some clever soul suggested an easier solution: you can simply remove the corrupted file ```
~/.config/menus/application.menu
``` and everything works again; the file gets automatically regenerated to default the first time that you invoke the menu editor. 

Also, you may want to look for backup files (if any, in the same directory) to get back to you next-to-latest personalized menu.

---

### Post by jazzman65 on 2008-04-11
Thanks jollo!  I had the exact same problem and your solution worked perfectly.  Thanks again!  :grin:

---

### Post by Xizorbg on 2008-04-21
Dear All-

I have tried all that you have suggested, including adding a new user and copying that file.  To no avail, I get the same event when I click on the "Applications" tab - nothing, but  tiny white dot that appears just below on the left of the tool bar.  I also cannot start alacarte from the command line as a normal user or as root......

Also, when I create a new user, his applications menu is also broken....

any ideas?

Thanks much,
X:)

---

### Post by ladjack on 2008-05-16
**jollo**, thnx a lot. it really helps. ))

---

### Post by Peter Great on 2008-06-02
I had the same problem. I tried to delete a menu entry created by Wine, but alacarte magically deleted the whole menu, and nothing comes out when I click on 'Applications'...Thank you for the post, I'll try to fix it by your method.

---

### Post by seuzy13 on 2008-06-21
None of my other users had an "applications.menu" file, but I was able to solve the problem by deleting the file. This thread helped a great deal. Thanks a billion. :-)

So, I suppose I should avoid the menu editor? Is there perhaps a better way to do things that doesn't put one through this whole fiasco?

---

