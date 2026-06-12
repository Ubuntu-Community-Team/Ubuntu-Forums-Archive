---
title: "Main Menu Edit (alacarte) not working"
date: 2009-03-21
forum: Desktop Environments
---

### Post by bbgman on 2009-03-21
I have a problem with editing main menu (Systems->Preference->Main Menu), when i click it nothing happens. I tried running it directly from the terminal, i got the following message.

> 
/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 35, in __init__
    self.locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.5/locale.py", line 443, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.5/locale.py", line 375, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
ValueError: unknown locale: en_NG


Please help. Thank you.

---

### Post by aquateen.carl on 2009-08-10
I just had the same issue and found another forum that explained how to fix it.

You have to change the owner of the hidden .config folder in your home directory to your user account.

sudo chown -hR yourusername /home/yourusername/.config

That fixed this issue for me.

---

