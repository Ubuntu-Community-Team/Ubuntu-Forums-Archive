---
title: "Alacarte not working, compiz issues, etc"
date: 2008-12-25
forum: General Help
---

### Post by Ekeluo on 2008-12-25
Intrepid, alacarte (menu editor?) doesn't launch. I right click on the menu icon, select edit menus, nothing happens. Run dialog doesn't show either. In terminal: 

kels@kels-laptop:~$ alacarte 
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
kels@kels-laptop:~$ 

(Sorry don't know how to do the special code pasting thingy..)

Elisa and orca also give a similar kind of error. This is also occuring on a friend's laptop (Core2duo, gma 3100), fresh install, no extras whatsoever. Some thing wrong with locale en_NG?

Also, My laptop (on which the above is occuring) is a Pentium M 1.6 ghz with GM915 graphics, 768mb ram, 40gb hdd. On Hardy I had torcs, openarena and glest, and I could play them with compiz enabled (minor screen flickering was bearable. But now, torcs and openarena refused to behave themselves when compiz is on, treating me to various maladies. Yeah, I appreciate that totem now plays videos happily with compiz on, but the games are bad.

P.S. Anything like loose bindings for intel gfx? Compiz is kinda slow on my system.

Also What happened to displayconfig-gtk? I can't view my display drivers any more.

---

### Post by Ekeluo on 2008-12-28
Guys and Ladies please ANY help will be very appreciated.

---

### Post by drs305 on 2008-12-28
As for your first issue, try reinstalling alacarte via synaptic (mark for reinstallation) or via the command line :
```
sudo aptitude reinstall alacarte
```

If that doesn't fix it, try the same for "python2.5"

If it still doesn't work, try to completely uninstall alacarte and then reinstall it.

---

### Post by Ekeluo on 2008-12-28
Tried, didn't work.

---

### Post by Meow27 on 2009-01-10
wait... did you try sudo alacarte   ?

---

### Post by Ekeluo on 2009-01-23
> **Meow27 said:**
> wait... did you try sudo alacarte   ?
Don't work either

---

### Post by Ekeluo on 2009-01-26
I've found that the programs that crash on start up all have similar console outputs, "error in line xx in something.py" etc. Will put up a more detailed post tonight. Generally, I think python is completely screwed on my system. Need a lot of help please.

---

### Post by Ekeluo on 2009-01-26
bump. Hey guys (and girls) please look here, please

---

### Post by bigbrovar on 2009-02-21
This is a general bug that affect many python program on ubuntu Alacate and system-config-printer. its caused by some funky stuff that happens when you Lagos/Nigeria. during install .. which results in the system locale being set to en_NG a locate which python is not very happy with. the way to get round this problem is to change your default language from English (Nigeria) to English (United Kingdom) you can do this from /System/Administration/Language Support

am surprised the bug has not been fixed in Intrepid because it started in Hardy is reported as fixed.

---

### Post by Ekeluo on 2009-07-17
Thanks bigbrovar, worked ok.

---

