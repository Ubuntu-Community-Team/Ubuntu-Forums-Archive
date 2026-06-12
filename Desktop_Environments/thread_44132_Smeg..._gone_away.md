---
title: "Smeg... gone away"
date: 2005-06-24
forum: Desktop Environments
---

### Post by Nonno Bassotto on 2005-06-24
I don't know what happened, but yesterday Smeg menu editor sopped working. Simply when I launch the application, there remains for a while the writing "Starting Smeg menu editor", and then nothing, it disappears in a puff of logic. The last thing I had done was installing creox, so I tried to uninstall it, reinstall Smeg, but this wasn't of any use. I don't know what kind of information you need to understand what's going on, so please ask.
Thank you a lot
Andrea

---

### Post by flankk on 2005-06-24
Run it from a console, see what errors it gives you.. then head over to the -current- thread.. many issues have been discussed and resolved here.

[http://ubuntuforums.org/showthread.php?t=38183](http://ubuntuforums.org/showthread.php?t=38183)

Otherwise, my suggestion is to
```
sudo dpkg -P smeg
```

and get a new copy linked from that thread.

---

### Post by Nonno Bassotto on 2005-06-24
Ok, now I think I unuderstand the problem, but not the solution. I've called one of the entries "TeXmaker look 'n' feel" and now Smeg complaints. I surely would remove that entry, but I don't know how without starting Smeg itself. the output from smeg is

None
Traceback (most recent call last):
  File "/usr/bin/smeg", line 559, in ?
    main()
  File "/usr/bin/smeg", line 555, in main
    smeg = Smeg()
  File "/usr/bin/smeg", line 61, in __init__
    self.handler = MenuHandler(self, self.options)
  File "/usr/lib/smeg/MenuHandler.py", line 57, in __init__
    xdg.MenuEditor.MenuEditor.__init__(self, menu_path, root=options.root_mode)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 27, in __init__
    self.parse(menu, filename, root)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 41, in parse
    self.menu = parse()
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 516, in parse
    __parse(doc, filename, tmp["Root"])
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 537, in __parse
    __parseMenu(child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 691, in __parseMenu
    __parse(child, filename, m)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 537, in __parse
    __parseMenu(child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 691, in __parseMenu
    __parse(child, filename, m)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 571, in __parse
    parent.Rules.append(Rule(child.tagName, child))
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 284, in __init__
    self.compile()
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 290, in compile
    exec("""
  File "<string>", line 6
    elif menuentry.DesktopFileID == 'TeXmaker look'n'feel.desktop':
                                                                               ^
SyntaxError: invalid syntax


with the little hat ^ just under the n.

---

### Post by intangible on 2005-06-24
The easiest thing to do would be to reinstall Smeg and see if that fixes it.

sudo apt-get --reinstall install smeg

---

### Post by Nonno Bassotto on 2005-06-24
Ok, I answered too soon. In the post that you mention I heard of /usr/myname/.config/menus/application.menu, and editing that file I was able to regain control of Smeg. Thank you
Andrea

---

