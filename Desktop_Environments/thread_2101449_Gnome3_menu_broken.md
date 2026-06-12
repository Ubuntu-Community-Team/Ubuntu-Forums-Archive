---
title: "Gnome3 menu broken"
date: 2013-01-04
forum: Desktop Environments
---

### Post by linuxman72 on 2013-01-04
My computer (Ubuntu Gnome remix 12.10) recently refused to shut down. the OS seemed to shut down and the monitor turned off, but the fans and lights in the case stayed on. after about 15 minutes I held down the power button and forced it off. When I turned it back on in the morning everything seemed fine, but when I opened the Gnome overview all of my favorites applications were gone. this seemed odd. I then clicked the show all applications button- which showed nothing. zero programs and the only category was "all". I then tried typing "fire" to bring up Firefox, and, surprise, programs appeared, like firewall configuration, but not Firefox. after more typing it appears that most, but not all programs are missing and those that are still there are only accessible by searching for them????  I then ran alacarte (missing from menu) from the terminal (also missing, accessible from shortcut only) and got
```
~$ alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 37, in <module>
    main()
  File "/usr/bin/alacarte", line 33, in main
    app = MainWindow(datadir, version)
  File "/usr/share/alacarte/Alacarte/MainWindow.py", line 43, in __init__
    self.editor = MenuEditor()
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 31, in __init__
    self.load()
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 45, in load
    raise ValueError("can not load menu tree %r" % (self.name,))
ValueError: can not load menu tree 'applications.menu'
```I googled for a minute (launched firefox from terminal) and found that alacarte might work if I used sudo, this got alacarte started, at which point I tried turning programs on and off and clicking "restore system configuration", but nothing happened. In addition, programs I had previously added manually(and successfully) with alacarte were missing from alacarte, while programs the system had added showed up.

I tried logging in from another user account, which worked perfectly. no missing anything.

Please help, I don't want to launch everything from terminal!

(if someone knows why my computer did not turn off that would be helpful as well, it may be connected--corrupted file that was trying to save? my computer is fast, no file on my computer should take that long to save, but ???????)

---

### Post by linuxman72 on 2013-01-06
Update: 
I found a page that stated that the not shutting down problem is a bug and explained how to fix it by editing the GRUB configuration files. So far, it seems to have stopped repeat occurrences of this issue, but the main issue with Gnome still exists.

---

### Post by Frogs Hair on 2013-01-06
Try typing main menu .

---

### Post by linuxman72 on 2013-01-06
"main menu" is one of the programs that is missing, its terminal command/ system name is alacarte.

---

### Post by Frogs Hair on 2013-01-07
Sorry , I was thinking of dash name , but if it won't open in terminal it won't open from dash . If you have the synaptic package manager installed try reinstalling alacarte.

---

### Post by linuxman72 on 2013-01-07
I fixed it!
I deleted the .config/menus/applications.menu file and the .local/share/applications folder, (I suspected file corruption from alacarte's error output) and restarted- all icons are restored.

---

