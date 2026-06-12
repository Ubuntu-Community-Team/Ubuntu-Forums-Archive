---
title: "Send to Terminal?"
date: 2009-04-03
forum: General Help
---

### Post by mdgrech on 2009-04-03
I want to be able to highlight terminal commands on a web page, right click and send those commands to terminal.  does anyone know of such a thing?  Thanks

---

### Post by Stoodle on 2009-04-03
Copy and paste? :D

---

### Post by mdgrech on 2009-04-03
lol copy and paste whats that?  No i just spend a ton of time in front of the computer and this would save me a lot of time!

---

### Post by mb_webguy on 2009-04-03
In the terminal, go to Edit->Keyboard Shortcuts.  Change Copy and Paste to Ctrl+C and Ctrl+V, respectively.  This is to make them the same as most every other program you'll encounter.

Now just select the text in your browser, press Ctrl+C to copy the text, then go to the terminal and press Ctrl+V to paste.

---

### Post by stumbleUpon on 2009-04-03
> **mdgrech said:**
> I want to be able to highlight terminal commands on a web page, right click and send those commands to terminal.  does anyone know of such a thing?  Thanks

This solution is not exactly what you want but close.

It is with help from these two threads

[1] [http://ubuntuforums.org/showthread.php?t=451587](http://ubuntuforums.org/showthread.php?t=451587) (How to access the Clipboard?)

[2] [http://ubuntuforums.org/showthread.php?t=1015654](http://ubuntuforums.org/showthread.php?t=1015654) (gnome-terminal command, keep window open - with prompt)


First  write the shell script 'keepopen' as suggested in [2]

```

#!/bin/sh
$1
bash

```

then write another python script called 'runInTerminal' with the following

```

#!/usr/bin/env python
import os
s=os.popen('xsel').read();
os.system('/usr/bin/gnome-terminal -e \"/path/to/script/keepopen '+s+'\"');

```

Make both the scripts executable and put them in your $PATH.

In the GNOME panel above, you can creat a new item and point to this python script. Now you can select any text and click on this item. It will be executed in gnome-terminal.

Modify the script to suit your exact needs (want the terminal to remain open after executing the command or not.. etc)


Perhaps one can use this idea to write a firefox extension and then one would get exactly what you are asking for, though i think this method will be useful to execute text selected from other applications as well.

---

### Post by maheshasolkar on 2009-04-03
Select text in the browser - it will be automatically copied.
Middle-click the mouse in the terminal - text will be pasted in the terminal.

I believe this is less clicks than 'send to terminal' context menu in a browser.

---

### Post by mdgrech on 2009-04-03
Thanks guys!  I didn't about the whole highlight middle click thing very cool

---

### Post by coffeecat on 2009-04-03
> **mb_webguy said:**
> In the terminal, go to Edit->Keyboard Shortcuts.  Change Copy and Paste to Ctrl+C and Ctrl+V, respectively.  This is to make them the same as most every other program you'll encounter.

I can understand why you would want to do this, but what happens when you want to kill a process that's running in the terminal? You press Ctrl-C and.... :(

---

### Post by mdgrech on 2009-04-03
Shout good thing you brought that up I just changed that too and didn't think about it.  I use Rails and that kind of the way to stop the server too..I'm sure there is another route though?

---

### Post by mb_webguy on 2009-04-03
> **coffeecat said:**
> I can understand why you would want to do this, but what happens when you want to kill a process that's running in the terminal? You press Ctrl-C and.... :(

If you have something selected in the terminal, Ctrl+C will copy.  If nothing is selected, Ctrl+C will kill a running process.  Since the functionality is situation-dependent in this case, I don't see any reason to use a non-standard keyboard shortcut for copy.

EDIT:  My statements above were referring to gnome-terminal, the default Ubuntu terminal.  While Ctrl+C works fine as both kill and copy, it's not the default keyboard shortcut for copy.  The default for copy and paste in xfce4-terminal (the Xubuntu default terminal) is the standard Ctrl+C and Ctrl+V, with Ctrl+C having the dual functionality mentioned above.

---

### Post by coffeecat on 2009-04-04
> **mb_webguy said:**
> If you have something selected in the terminal, Ctrl+C will copy.  If nothing is selected, Ctrl+C will kill a running process.  Since the functionality is situation-dependent in this case, I don't see any reason to use a non-standard keyboard shortcut for copy.

I've just tried it in gnome-terminal (v 2.26 - Jaunty) and this is not so - at least for gnome-terminal. I haven't tried it in other terminals. With ctrl-C setup as the shortcut for copy, and nothing selected for copy, ctrl-C does **not** kill a running process.

---

