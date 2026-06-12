---
title: "assign shortcut to nautilus script"
date: 2009-06-07
forum: Desktop Environments
---

### Post by karel1980 on 2009-06-07
Hi, is there a way to assign a shortcut to a nautilus script?
I know I can assign shortcuts to general commands using System -> Preferences -> Keyboard shortcuts, but that only works for launching commands which don't take an argument (e.g. the filename(s) currently selected in nautilus)

---

### Post by Bucky Ball on 2009-06-07
You could try creating a custom launcher. Right click on the top taskbar and 'Add to Panel'. Then 'Custom Application Launcher'.

I also installed something perfect for you but never use it so can't remember what it is called for the life of me. Hopefully someone does. When you right click on the desktop, one of the options is 'Scripts'. You can add your scripts to this folder and run 'em directly from that menu. Cool.

---

### Post by karel1980 on 2009-06-08
> **Bucky Ball said:**
> You could try creating a custom launcher. Right click on the top taskbar and 'Add to Panel'. Then 'Custom Application Launcher'.

I also installed something perfect for you but never use it so can't remember what it is called for the life of me. Hopefully someone does. When you right click on the desktop, one of the options is 'Scripts'. You can add your scripts to this folder and run 'em directly from that menu. Cool.

Custom Application Launcher's won't do the trick - perhaps my problem description wasn't clear enough - read on...

That last thing you described is called nautilus scripts - an example would be this:
```

----------- $HOME/.gnome2/nautilus-scripts/test ----------
#!/bin/bash

(echo "Script: $0"
 echo "Arguments: $@"
 echo "pwd: `pwd`";) | zenity --text-info
-----------------------------------------------------------

```

The point about these is that you can select a bunch of files in nautilus and then run the script on that selection (the selection is passed as arguments to the script)

So to repeat the question: is there a way to assign a shortcut to a nautilus-script?  I could use the key sequence [menu],s,[first letter of the script] (this would pop up the context menu, open the Scripts submenu and select the script, but I would like something more direct  (like Ctrl-F5 or another combination)

---

### Post by aliusn on 2010-09-06
My solution in Ubuntu 10.04:

1. Add executable script to ~/.gnome2/nautilus-scripts (in my case "Open terminal")
2. Wait some time - nautilus regenerates accels file (I'm not sure how often)
3. Edit file ~/.gnome2/accels/nautilus

4. Find line similar to this one:
; (gtk_accel_path "<Actions>/ScriptsGroup/script_file:\\s\\s\\shome\\salius\\s.gnome2\\snautilus-scripts\\sOpen%20terminal" "")

5. Remove comment (semicolon) and specify shortcut like this:
(gtk_accel_path "<Actions>/ScriptsGroup/script_file:\\s\\s\\shome\\salius\\s.gnome2\\snautilus-scripts\\sOpen%20terminal" "F12")

6. Save file.
7. Logout - login.

Now I can press F12 and nautilus opens terminal.

---

