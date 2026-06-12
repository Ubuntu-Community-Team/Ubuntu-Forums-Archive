---
title: "lost launcher desktop icons"
date: 2006-07-03
forum: Desktop Environments
---

### Post by troubleshootr on 2006-07-03
All my shortcut launcher icons now appear as .desktop generic icons.  If I double click I get:

The filename "nautilus-home.desktop" indicates that this file is of type "desktop document". The contents of the file indicate that the file is of type "desktop configuration file". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "desktop configuration file", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

If I create a new launcher, it also appears this way.  It is probable something stupid, but google and forum search came up empty.  Permissions are fine. Does anyone know what I may have done, and how I can get my shortcuts back?

Thanks,
Bob

---

### Post by mlind on 2006-07-03
Something must have hijacked .destop file type..  Does *~/.local/share/defaults.list* or *~/.mime.types* contain anything related to .desktop file?

---

### Post by troubleshootr on 2006-07-03
Both  ~/.local/share/defaults.list or ~/.mime.types do not exist.  I have in ~./local/share

[email]bob@bob-desktop:~/.loca[/email]l/share$ ls -a
.  ..  applications  mime

I do not have a ~/.mime.types

Perhaps this is the problem?

Thanks.

---

### Post by mlind on 2006-07-03
[QUOTE=troubleshootr]
Perhaps this is the problem?[/QUOTE]

No, I don't think so. Those files are just for overriding global settings.

.desktop files are very essential for gnome desktop, I wonder how this could have
happen. Can you describe what you did when you noticed that desktop launchers
were not working anymore? Do menu shortcuts still work?

---

### Post by troubleshootr on 2006-07-03
> Can you describe what you did when you noticed that desktop launchers
were not working anymore? Do menu shortcuts still work?

I had just set up a server connection (via Places > Connect to Server) to my Nokia 770 internet tablet and was transfering files.  When I exit SSH session icons were as generic .desktop.  Menu shortcuts still work.  When I drag shortcut from menu to desktop it then displays as generic .desktop icon.  The command in the launcher shortcuts are correct, they just do not launch.

EDIT: some additional info:  My other account (a guest account) the shortcuts still work.  It appears it is only my main account that is affected.  Where is the .desktop association stored?

---

### Post by mlind on 2006-07-03
[QUOTE=troubleshootr]I had just set up a server connection (via Places > Connect to Server) to my Nokia 770 internet tablet and was transfering files.  When I exit SSH session icons were as generic .desktop.  Menu shortcuts still work.  When I drag shortcut from menu to desktop it then displays as generic .desktop icon.  The command in the launcher shortcuts are correct, they just do not launch.

EDIT: some additional info:  My other account (a guest account) the shortcuts still work.  It appears it is only my main account that is affected.  Where is the .desktop association stored?[/QUOTE]

Those are on ~/Desktop folder. Could also be that some gconf key is fubar.
I suggest you go through all the .dot folders on your home folder, and see if there's anything strange.

---

### Post by troubleshootr on 2006-07-03
[QUOTE=mlind]Those are on ~/Desktop folder. Could also be that some gconf key is fubar.
I suggest you go through all the .dot folders on your home folder, and see if there's anything strange.[/QUOTE]

Thanks for the reply.  Using gconf-editor, I was not able to find the shortcuts (I did find the ones that are on the menu bar -these do work.  I will go through the .dot files and compare to the account that does work.  Worst comes to worse, I can create a new account, but I really would like to learn what went wrong.  Thanks for your help.

---

### Post by troubleshootr on 2006-07-03
OK I got it working.  It was something in ~/.local.

I renamed my home directory, and then created a new empty home directory.  Shortcuts worked.  I then copied the .dot files one by one till the problem resurfaced.  When .local was copied the problem came back.  I just deleted this directory.  Everything seems OK.

---

### Post by mlind on 2006-07-03
[QUOTE=troubleshootr]OK I got it working.  It was something in ~/.local.

I renamed my home directory, and then created a new empty home directory.  Shortcuts worked.  I then copied the .dot files one by one till the problem resurfaced.  When .local was copied the problem came back.  I just deleted this directory.  Everything seems OK.[/QUOTE]

okay, good you got it sorted out. Problems like these are pretty hard to trace.

---

### Post by junglee on 2007-08-25
This was difficult to trace indeed!! Thanks to this thread, i was able to fix this issue. In my case, I traced the problem to 2 files:
[LIST]
[*]~/.local/share/mime/globs
[*]~/.local/share/mime/XMLnamespaces/*
[/LIST]

These files had set the mime type for *.desktop files incorrectly. After i deleted these files, Gnome Desktop went back to its normal behaviour.  :guitar:

---

### Post by Wolki on 2007-08-26
> **junglee said:**
> This was difficult to trace indeed!! Thanks to this thread, i was able to fix this issue. In my case, I traced the problem to 2 files:
[LIST]
[*]~/.local/share/mime/globs
[*]~/.local/share/mime/XMLnamespaces/*
[/LIST]

These files had set the mime type for *.desktop files incorrectly. After i deleted these files, Gnome Desktop went back to its normal behaviour.  :guitar:

Don't do it like that. While it may fix the problem for now, it won't fix the cause, so the next time your mime customizations are updated, the same problem will resurface; also any filetypes you added yourself will be lost until then.

The correct way is finding the mime definition that's the culprit. If it is a problem that only affects one user (as yours obviously is), the problematic mimetype must be in the ~/.local/share/mime/packages directory. It is likely to be in a file called Override.xml (but could theoretically be in any other file in that directory), so look there first. If you found it, remove the wrong type (simply delete from the "<mime-type ...>" tag directly before a mention of .desktop files to the "</mime-type ...>" tag directly after it. Afterwards regenerate your mime cache using ```
update-mime-database ~/.local/share/mime/
```

If you didn't get any errors, everything should work fine now.

---

