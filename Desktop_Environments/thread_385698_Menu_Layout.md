---
title: "Menu Layout"
date: 2007-03-16
forum: Desktop Environments
---

### Post by xavier_r on 2007-03-16
System->Preferences->Menu Layout

I click that and its not working...
Nothing is opening up...

Any?

---

### Post by mcduck on 2007-03-16
What happens if you try running 'alacarte' from a terminal? Do you get any errors?

---

### Post by xavier_r on 2007-03-16
Yea...
I tried running alacarte and do get errors...

Not interesting but still i post it...

rpg@Dyaus:~$ alacarte
/var/lib/python-support/python2.4/gtk-2.0/bonobo/__init__.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in ?
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.4/site-packages/Alacarte/MainWindow.py", line 45, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.4/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.4/site-packages/Alacarte/MenuEditor.py", line 58, in __loadMenus
    self.save(True)
  File "/usr/lib/python2.4/site-packages/Alacarte/MenuEditor.py", line 62, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permission denied: '/home/rpg/.config/menus/applications.menu'


I changed the permissions...
$ sudo chmod 664 applications.menu

and ola it is working...
Thanks mcduck... i'll remember this name "alacarte"

---

### Post by dimeotane on 2007-03-18
I installed krecipes and didn't find the name added to the applications menu.  I ran alacarte (system-->preferences-->menu layout) and found that it won't let me add or remove a checkmark for "show" on anything.  Any suggestions?:confused:

---

### Post by Kwag on 2007-03-20
dimeotane ...

I feel your pain.  I can't configure my GNOME menus either.  I can add and remove menu items and menus, but I can't get the menus I add to appear.  (Ubuntu won't let me check that checkbox).   Restarting GNOME and doing all the standard tricks doesn't work.

I thought maybe it was some permissions thing so I did

sudo alacarte

That still didn't help.  

I think this is a pretty sad state of affairs for a Linux distribution.  Supposedly, Linux is an operating system that is flexible, where you can configure everything exactly to your liking.  BUT I CAN'T EVEN CONFIGURE THE APPLICATION MENUS!   If a distribution can't accomplish simple things, how can I trust it with more complex things?  I understand that Linux distributions aren't completely put together right out of the box, but something straight forward like this ought to work right out of the box before being publicly released.  We are not talking about hardware configuration, or third party software configuration, setting up a network, or other things where the need for some tinkering is understandable.  This is a basic operating system functionality that is defective.   

Well, if there are command lines that can accomplish these basic functions, fine, that's great, but then don't release the GUI front end if it is not ready.

Sorry everyone for the complaining and the fussing, but I am shocked from this discovery.  

Well, I need to calm down.  After all, Ubuntu is actually the first Linux distribution I have tried.  I know there tons more to consider.  

I think my next step is to try installing KDE within my current Ubuntu and see if that desktop environment works better.

---

