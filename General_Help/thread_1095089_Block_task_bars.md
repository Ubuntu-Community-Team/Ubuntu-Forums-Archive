---
title: "Block task bars"
date: 2009-03-13
forum: General Help
---

### Post by Campitor on 2009-03-13
Hello All:

  I've managed to convice the IT folks at the University I work at in Costa Rica, to switch all computers to Ubuntu (8.04 and 8.10).  The change was received with mixed emotions by faculty, students and staff; but we haven't gone back to windows.  We do have a problem and I don't know how to fix it. Here it is:

Some of the students keep moving the menu bar (with the ubuntu menu) and task bars to different places on the desktop.  Sometimes they switch on the auto-hide function, or change the color to make them difficult to see.  The most unexperienced users get confused by this and start complaining about ubuntu and requesting help from the IT department.

  Although we have given a bunch of lectures to teach them about Ubuntu, most students never show up.  My specific question is:

1.  Is there a way to freeze or block the task bars so they don't get modified by students? (requiere admin priveleges).

2. Is there a way to "freeze" the entire desktop, so students cannot change the icons, desktop background, shortcuts, etc.?  This question relates to the fact that on the desktop we placed three icons that say: Word, Excel and Powerpoint; which point to the respective OpenOffice applications (help students with the transition).  If these icons get removed and the menu bar gets moved to other locations, then some of the students can't find the applications and the complaining begins.

Any help or suggestion would be appreciated.  We use gnome as our WM and it has been tweaked to resemble Windoze as much as possible to ease with the transition.

Thank you all in advance for you help.

Camp.

---

### Post by UbuntuNerd on 2009-03-13
you can lock down all the panels at once. Just install Ubuntu Tweak. You can find it from in Synaptic Package Manager (ubuntu-tweak) after you install it a launcher will be in Applications > System Tools.
after you run the program, click on System. There is a checkbox for "Complete lockdown of the panels".

or hit Alt-F2 and run "gconf-editor"

when it starts navigate to:
apps > panel > global

where it says "lock_down" click the checkbox and restart gnome with Ctrl-Alt-Backspace

you can also right click on the "Icons" to lock them to the panel. if they deleted the panels for some reason you can restore them with this code to the default settings:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

### Post by heindsight on 2009-03-13
I'm not sure if it is possible to completely prevent users from changing the panels and desktop icons as they please.

You can lock the panel configuration by opening the gconf editor (Applications>System Tools>Configuration Editor) and enabling the /apps/panel/global/locked_down option - however, it should still be easy enough for some user to figure out how to unlock it again.

I think it would be a much better option to give each user their own login account, that way any changes one particular user makes to his/her desktop configuration won't affect anyone else.

Alternatively, it should be possible to reset all the desktop configuration each time a user logs out. Simply set up the desktop the way you want it and make a backup of all the desktop configuration files. Now each time a user logs out, you delete all those configuration files from their home directory and restore the backed up configuration.

---

### Post by UbuntuNerd on 2009-03-13
"Campitor" is there any way you can post a screen shot of what the students desktop's look like? thank you.

---

### Post by Campitor on 2009-03-13
> **UbuntuNerd said:**
> "Campitor" is there any way you can post a screen shot of what the students desktop's look like? thank you.

The following image is a common example where they have moved the taksbars to the top.

I will try the lock-down option and see if it works.  Most of our students will not be able to find the gconf-editor > apps > panel > global fix.  I think this is simple enough and might do the trick.  It will take too much time to give all students a login, but I really like the option of returning to a base configuration everytime the computer restarts, which they are set to do automatically.  I don't know how to do this, but I'm sure the IT guys will.
 
Thank you for the quick reply!!!

Camp

---

