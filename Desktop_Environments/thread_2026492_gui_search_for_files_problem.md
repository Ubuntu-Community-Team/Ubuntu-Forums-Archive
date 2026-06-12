---
title: "gui search for files problem"
date: 2012-07-15
forum: Desktop Environments
---

### Post by goodbye-windows(tm) on 2012-07-15
Hi All,

I have a new (12.04) Xubuntu installation. In the old install (which is gone now), I used a search for files program called 'kfind'. 

I installed kfind, but it seems to be lost/missing. It does not appear in the listings for programs and the application finder does not find it.

I uninstalled it and reinstalled it, no joy.

I need a replacement for catfish which comes with Xubuntu. But, it leaves allot to be desired, once the files are found, you can't move, open or delete them-argh!

If kfind won't work, I need an alternative file search utility.

TY.

Art

---

### Post by oldos2er on 2012-07-15
Can you run kfind from a terminal? Perhaps you need to manually create a menu entry for it.

---

### Post by goodbye-windows(tm) on 2012-07-15
Yes, that was it!!! I typed kfind into the terminal, a bunch of text immediately appeared in the window, and then the gui window for kfind popped up!!!

I did a quick search and it found entries. I was able to drag and drop them, which is the major issue with catfish search software.

I think I can just drag the open kfind window to the launcher to create a shortcut there.

I'll poke around a little and see if i can figure out how to do it. 

TY,

Art

---

### Post by black veils on 2012-07-15
you can manually create a panel launcher easily enough, like you would any other app, but put the right command in.

---

### Post by jmfal on 2012-07-15
When you open app check in right side of menu bar (tool bar
across top of screen) for icon, and click on it

---

### Post by goodbye-windows(tm) on 2012-07-16
I've tried andtried, even readinghte docs (at file:///usr/share/doc/xfce4-panel/html/C/index.html ) 

The closest I came to success was finding an entry in synaptic package manager (see below for the info given by synaptic).

> file search utility 
 
KFind can be used to find files and directories on your system.

This package is part of the KDE base applications module.

I wonder if this utility will run in xubuntu. It looks like I need to  install the entire base applications module.  While kfind might run by  itself, can the entire base applications module coexist in xubuntu?

I found some info about creating custom menu entries with google, but it's strictly for unity only.

A search of this forum found nothing about creating custom menu or launcher items in Xubuntu.

At this point, I'm stuck.

All suggestions are welcome.

Regards,

Art

---

### Post by LewisTM on 2012-07-16
kfind needs the KDE libraries to run. This means it might take a bit more memory and launch slower because many libs need to load. It will run just as fast if not faster in Xubuntu, no worries.

I'm surprised you haven't found how to create a custom launcher, it's kind of self-evident. You can right-click on the desktop and select 'Create Launcher' or you can right-click a panel, select Panel->Add New Items->Launcher.

Cheers!

---

### Post by goodbye-windows(tm) on 2012-07-16
> I'm surprised you haven't found how to create a custom launcher, it's  kind of self-evident. You can right-click on the desktop and select  'Create Launcher' or you can right-click a panel, select Panel->Add  New Items->Launcher

OK, the desktop right click works, and I used it to make a shortcut. I used the icon from catfish.

The right click on panel doesn't work, you have to select the application from a list that the system supplies and 'kfind' isn't on it.

I spent most of my time researching how to add a menu item to the list of programs available. But, the messages on this forum state that the menu editor is no longer provided, so I gave up. I concentrated on searching for how to create custom menu items because the entry in the programs menu can simply be dragged and dropped onto the panel.

Will xubuntu work ok if I install the entire KDE libraries?? To me it sounded like the library might not be compatible with xubuntu. Synaptic can install all the prerequisites along with kfind.

TY.

Art

---

### Post by LewisTM on 2012-07-16
To edit the Menu right-click you Applications Menu, select Properties and click the Edit Menu button. Then add a new item specifying kfind as the command. Same idea for panel launchers but the easiest for you would be to drag and drop your desktop launcher inside your panel.

Installing KDE libraries will not install the KDE desktop environment, only what is required to run programs written to use the KDE resources (dialog boxes, icons, widgets, file I/O, multimedia layer, etc.). You can run any KDE app in any flavor of Ubuntu without impacting on your desktop experience.

I think the reason Kfind has no menu item is that it is typically used from within the KDE file manager, but as you can see it can be used standalone.

---

### Post by goodbye-windows(tm) on 2012-07-18
I managed to create the launcher, but kfind always finds no files when it searches. So, I gave up on kfind.

I did find a much better search program than catfish, and it runs great. 

So, I am marking this thread 'solved'.

Art

---

### Post by LewisTM on 2012-07-23
Art,

Sorry for the late reply.
Unlike catfish and gnome-search-tool, kfind uses old-style wildcards for name matching.

For example to find a name that starts with 'foo' you enter [FONT="Courier New"]foo*[/FONT] in the search box. 
To restrict to jpegs : [FONT="Courier New"]foo*.jpg[/FONT]
For files with foo anywhere in their name: [FONT="Courier New"]*foo*[/FONT]

---

