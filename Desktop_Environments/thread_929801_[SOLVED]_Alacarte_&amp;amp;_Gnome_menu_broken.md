---
title: "[SOLVED] Alacarte &amp;amp; Gnome menu broken"
date: 2008-09-25
forum: Desktop Environments
---

### Post by BrendanM on 2008-09-25
A little background: I was having some hard drive troubles and after much fscking that seems to have been resolved. However, some files were corrupted/lost, apparently including my "Applications" and "System" menus which now contain no entires. I can still launch almost all apps from the terminal with no problems.

However, when I try to launch alacarte, hoping to re-generate my gnome menu, I get this:

```
$alacarte
/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 46, in __loadMenus
    self.applications.dom = xml.dom.minidom.parse(self.applications.path)
  File "/usr/lib/python2.5/xml/dom/minidom.py", line 1915, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 924, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 207, in parseFile
    parser.Parse(buffer, 0)
xml.parsers.expat.ExpatError: not well-formed (invalid token): line 1, column 1
```

Re-installing alacarte doesn't fix the issue. Could somebody tell me what the problem might be, or how to fix it? If I wanted to manually re-generate the menu, rather than using alacarte, how could I do that? Where does GNOME keep the files that define the menu?

---

### Post by zingo on 2008-09-25
It seem to be a reported here:
[https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/274077]("https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/274077")
(e.g. it seem to be common problem and might had something to do with you other problems)
I also found this old thread
[http://ubuntuforums.org/showthread.php?p=5855034#post5855034]("http://ubuntuforums.org/showthread.php?p=5855034#post5855034")
But there was no fix...

---

### Post by zingo on 2008-09-25
I found this old bugreport

[https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/61340]("https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/61340")

The following solved it for me....
-------------------
BTW, to recreate the menus, simply remove the personalised menu file like so:

$ rm -f ~/.config/menus/applications.menu

And rerun alacarte:

$ alacarte

It will hopefully recreate your menus from the system-wide defaults.

If the system-wide defaults are broken too, try reinstalling the gnome-menus package.

---

### Post by BrendanM on 2008-09-30
Thanks for the help. Deleting the custom menu file restored the menus from the system-wide defaults as suggested.

---

