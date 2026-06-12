---
title: "alacarte is  broken"
date: 2009-04-29
forum: Desktop Environments
---

### Post by nssone on 2009-04-29
OK, I'm just posting this hoping there is somebody out there who maybe has an idea of what I can do to fix or change this. Basically, alacarte has determined it is necessary to resurrect and prefix old wine folder with wine-Programs-*. This is very annoying and it takes up unnecessary space. When I load alacarte (Edit menus) and select to remove or change the properties of the item, I simply can not. I am also having a hard time finding any help Googling or anything of the sort.

So, does anybody know of a fix for this? It's getting PDA. Thanks.

Forgot to mention Ubuntu Jaunty 9.04

---

### Post by cariboo on 2009-04-30
Could you not just uncheck the menu item and not have it show?

---

### Post by Redundant Username on 2009-04-30
```
rm -f ~/.config/menus/applications.menu
```
 so that it will reload it the menu?

---

### Post by nssone on 2009-04-30
I tried what was just posted before here, I'm assuming it deletes an older alacarte config, but that didn't help. I'm posting the lines that shows up when i run alacarte from terminal.

```
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 324, in on_properties_button_clicked
    self.on_edit_properties_activate(None)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 372, in on_edit_properties_activate
    parser.write(open(file_path))
IOError: [Errno 2] No such file or directory: 'alacarte-made.directory'
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 435, in on_item_tree_show_toggled
    self.editor.setVisible(item, False)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 215, in setVisible
    self.__writeMenu(item, no_display=True)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 576, in __writeMenu
    file_id = os.path.split(menu.get_desktop_file_path())[1]
  File "/usr/lib/python2.6/posixpath.py", line 82, in split
    i = p.rfind('/') + 1
AttributeError: 'NoneType' object has no attribute 'rfind'


```

That's all I can add that I know of to help illustrate the problem.

Thanks.

---

### Post by nssone on 2009-05-05
Bump. I would still like to see if there's a solution to this.

---

### Post by drs305 on 2009-05-05
I've played around with this for a while and can't really duplicate it. I have some "alacarte-made.directory" files that were created when I made custom folders to hold some of my shortcuts.

You might try opening gconf-editor and doing a search for "alacarte-made.directory". Open "gconf-editor", then Edit, Find, tick both boxes and type "alacarte-made.directory" in the search window. If it exists, it will probably come up as an entry in /apps/panel/objects . If you only have one or can identify it in some way as being the problem entry you could just try deleting it.

Good luck - hope you find a solution.

---

