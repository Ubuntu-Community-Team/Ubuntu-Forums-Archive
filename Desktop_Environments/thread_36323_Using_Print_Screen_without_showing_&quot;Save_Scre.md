---
title: "Using Print Screen without showing &quot;Save Screenshot&quot; dialogue?"
date: 2005-05-22
forum: Desktop Environments
---

### Post by picpak on 2005-05-22
Hi,

Is there a way to be able to take a picture of the desktop, without the pesky "Save Screenshot" window popping up? It seems to pop up on other buttons too, because I rarely use Print Screen.

If I disable it through System > Preferences > Keyboard Shortcuts, then I disable Print Screen altogether. Is there a way to uninstall the "Save Screenshot" application? I don't want to change my keyboard shortcut to something else - I want to keep it as Print Screen.

---

### Post by vaskark on 2005-05-23
[QUOTE=picpak]Hi,

Is there a way to be able to take a picture of the desktop, without the pesky "Save Screenshot" window popping up? It seems to pop up on other buttons too, because I rarely use Print Screen.

If I disable it through System > Preferences > Keyboard Shortcuts, then I disable Print Screen altogether. Is there a way to uninstall the "Save Screenshot" application? I don't want to change my keyboard shortcut to something else - I want to keep it as Print Screen.[/QUOTE]

I think I might have a solution for you. Here's what I did:

1) Install 'scrot', a command-line screenshot utility (from universe).

2) Make a text file with the following, save it as /usr/bin/screenshot, and make it executable:
 ```
#!/bin/bash
scrot '%Y%m%d_%H%M%S_shot.jpg' -e 'mv $f ~/screenshots/' -q 80
``` 
See the scrot man page for details about the various options. My example will take a screenshot and name it with a timestamp, move it to a folder called ~/screenshots, and save it at a quality of 80%. An error will occur if that folder doesn't already exist.

3) Open Applications > System > Configuration Editor. Go to */apps/metacity/keybinding_commands* and change *command_screenshot *to /usr/bin/screenshot.

Now the Print Screen key will take the screenshot without the save dialog.

Hope this helps!

P.S. I imagine you can also change Alt-PrintScreen to use 'scrot -s' for taking a shot of an open window or draggable area.

---

### Post by picpak on 2005-05-23
This may sound stupid, but how do you make a text file executable? I tried using chmod u+x screenshot (and pretty much every other combination of letters and x's) and it still doesn't work. Help?

---

### Post by vaskark on 2005-05-24
A text file can be made executable like any other file. If you saved the file in /usr/bin do the following to match the permissions I have (from the command line):
 ```
$ sudo chmod u+rwx /usr/bin/screenshot
$ sudo chmod g+rx /usr/bin/screenshot
$ sudo chmod o+rx /usr/bin/screenshot
```
That should do it. You did install scrot, right?

---

### Post by picpak on 2005-05-24
Yep! And now it works :)

---

