---
title: "Cannot edit main menu"
date: 2009-05-03
forum: General Help
---

### Post by etienne@Rofti on 2009-05-03
Hi! I could not find a post with exactly the same problem, so here goes:

I am using Jaunty, but I cannot edit my main menu. When I right-click on the menu, and select "Edit Menus" then nothing happens.

I do have permission to edit my ~/.local folder, but apart from that, I cannot figure out why I cannot edit my menu

Thanks in advance for any help!

Etienne

---

### Post by geirha on 2009-05-03
Open a terminal and run ```
alacarte
``` Does it give any error messages, or any messages at all?

---

### Post by etienne@Rofti on 2009-05-03
Hi! Thanks for the quick reply!

When I type that into my command line, the output is:
```
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
ImportError: No module named Alacarte.MainWindow

```
Does that mean anything to you?

---

### Post by geirha on 2009-05-03
Yes, it says it can't find certain files that are part of alacarte. Not sure how or why they could be gone, but try reinstalling alacarte to make sure the files are installed.

In a terminal, type this to reinstall alacarte.
```
sudo aptitude reinstall alacarte
```

Then try running alacarte again and see if you get the same error.

---

### Post by etienne@Rofti on 2009-05-03
Thanks geirha!

Who would've known, such a simple solution...
Works fine now, thank you!

---

### Post by msbrandhorst on 2009-05-04
I seem to be having the same issue.  When I right click on Applications and select edit menus noting seems to happen.    

When I enter:  alacarte I get the following:

Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 50, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 59, in __loadMenus
    self.save(True)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 63, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permission denied: '/home/michael/.config/menus/applications.menu'
michael@michael-ubuntu:~$ cd ~/.config/menus
bash: cd: /home/michael/.config/menus: Permission denied
michael@michael-ubuntu:~$ sudo cd ~/.config/menus
sudo: cd: command not found
michael@michael-ubuntu:~$ sudo cd ~/.config/menus
sudo: cd: command not found
michael@michael-ubuntu:~$ cd ~/.config/menus
bash: cd: /home/michael/.config/menus: Permission denied
michael@michael-ubuntu:~$ ~/.config/menus
bash: /home/michael/.config/menus: is a directory
michael@michael-ubuntu:~$ cd /~/.local folder
bash: cd: /~/.local: No such file or directory
michael@michael-ubuntu:~$ ~/.local folder
bash: /home/michael/.local: is a directory
michael@michael-ubuntu:~$ alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 50, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 59, in __loadMenus
    self.save(True)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 63, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permission denied: '/home/michael/.config/menus/applications.menu'


Everthing else seems to be working as it should.  Forgive me as I am a newbie to ubuntu / linuxs.

Any and all ideas would b be helpful.

Thanks
MSB

---

### Post by geirha on 2009-05-04
Seems the permissions and/or ownerships are wrong on those files/folders.

This should set yourself as owner on .config and all files and directories it contains
```
sudo chown -R $USER:$USER ~/.config
```

And these two commands should set some decent permissions
```

find ~/.config/menus -type d -exec chmod 755 {} \;
find ~/.config/menus -type f -exec chmod 644 {} \;

```

---

### Post by shane2peru on 2009-05-04
Never mind, use geirha's advice, that is better.

Shane

---

### Post by drbrando007 on 2009-05-05
-

---

### Post by drbrando007 on 2009-05-05
Thank you much geirha!!!
solid


> **geirha said:**
> Seems the permissions and/or ownerships are wrong on those files/folders.

This should set yourself as owner on .config and all files and directories it contains
```
sudo chown -R $USER:$USER ~/.config
```

And these two commands should set some decent permissions
```

find ~/.config/menus -type d -exec chmod 755 {} \;
find ~/.config/menus -type f -exec chmod 644 {} \;

```

---

### Post by bcrudo on 2009-05-06
your a genius.... worked like a charm in Jaunty

---

### Post by didshukaj on 2009-06-09
What if i have following? I already tried both methods but neither worked( on Ubuntu Jaunty)

smth@smwhere:~$ alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 50, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 46, in __loadMenus
    self.applications.dom = xml.dom.minidom.parse(self.applications.path)
  File "/usr/lib/python2.6/xml/dom/minidom.py", line 1918, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 924, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0

---

### Post by zeyacry on 2009-07-25
> **drbrando007 said:**
> Thank you much geirha!!!
solid

Hi, when i typed "alacarte" in the terminal, the main menu opened. But after i tick the submenu and i closed the main menu, i didnt see any changes. Am i on the right track to edit the menus?

---

### Post by steeny124 on 2009-10-19
I am having a similar problem as msbrandhorst had.  This is my error message: 

```
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 50, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 59, in __loadMenus
    self.save(True)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 63, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permission denied: '/home/steeny124/.config/menus/applications.menu'

```
However, when I tried this:

> Seems the permissions and/or ownerships are wrong on those files/folders.

This should set yourself as owner on .config and all files and directories it contains
Code:

sudo chown -R $USER:$USER ~/.config

And these two commands should set some decent permissions
Code:

find ~/.config/menus -type d -exec chmod 755 {} \;
find ~/.config/menus -type f -exec chmod 644 {} \;



it didn't work, particularly this here
```

find ~/.config/menus -type d -exec chmod 755 {} \;
find ~/.config/menus -type f -exec chmod 644 {} \;
```

I get this error message:

```
find: `/home/steeny124/.config/menu': No such file or directory

```

Not sure where to go from here.  Any help would be appreciated. I'm pretty dumb when it comes to these things. :p

---

### Post by brisingrkill on 2011-03-07
I get a error when I try to tick/untick a menue item.

```
Traceback (most recent call last):
  File "/usr/share/alacarte/Alacarte/MainWindow.py", line 437, in on_item_tree_show_toggled
    self.editor.setVisible(item, True)
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 209, in setVisible
    self.__addUndo([self.__getMenu(item), item])
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 428, in __addUndo
    open(undo_path, 'w').write(data)
IOError: [Errno 21] Is a directory: '/home/james/.config/menus/applications.menu.undo-0
```'

does anyone know how to fix or why it does it.

---

