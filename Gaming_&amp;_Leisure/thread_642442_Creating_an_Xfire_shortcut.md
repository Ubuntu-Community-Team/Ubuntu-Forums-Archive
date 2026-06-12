---
title: "Creating an Xfire shortcut?"
date: 2007-12-16
forum: Gaming &amp; Leisure
---

### Post by Squeek on 2007-12-16
Did a search for this, couldn't find anything.

I am trying to create a shortcut to Xfire for my system launcher panel (the equivalent to the Windows taskbar shortcuts).  However, I can't add a shortcut to the Xfire location (/home/dax/.wine/drive_c/Program Files/xfire.exe) because of the .space. in Program Files.  How can I get around this?

---

### Post by rukuartic on 2007-12-16
The space can be handled by escaping it with a forward slash.

For example, 

```

/home/rukuartic/My Folder

```

can be accessed as

```

cd /home/rukuartic/My\ Folder

```

---

### Post by Squeek on 2007-12-16
Perfect, thank you sir.

Unfortunately it's still saying the .exe doesn't exist, perhaps it has something to do with the .wine?  The system browser doesn't see it either, I can only get to the folder through Wine.

/home/dax/.wine/drive_c/Program Files/xfire.exe

---

### Post by Squeek on 2007-12-17
bump

---

### Post by Squeek on 2007-12-17
Nobody?

---

### Post by Zylar on 2007-12-19
I'm not familiar with XFire in linux/wine, but some apps require being run from the program directory.  Also, I'm pretty sure the XFire executable will be in it's own directory, not in Program Files.  Create a script:

#/bin/bash
cd ~/.wine/drive_c/Program\ Files/XFire/
wine xfire.exe

and then point to the script when you create the Panel Launcher.

This will also give you the ability to troubleshoot it using the terminal.

To see your .wine directory, you have to open your home folder.  Click View -> Show Hidden Files, or hit ctrl-H.  Then you'll be able to see the folders that start with a period (.), which are considered hidden.

Edit: When you installed XFire it should have given you a shortcut in the Applications -> Wine Panel. You should be able to right-click the XFire icon and click 'Add this launcher to panel'.
Edit2: You can also handle spaces with double-quotes.  Ex: $>wine "c:\program files\xfire\xfire.exe"

---

