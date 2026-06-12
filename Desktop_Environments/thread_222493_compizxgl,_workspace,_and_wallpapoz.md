---
title: "compiz/xgl, workspace, and wallpapoz"
date: 2006-07-25
forum: Desktop Environments
---

### Post by merinda on 2006-07-25
Hi, I am the author of wallpapoz ( [http://wallpapoz.sf.net](http://wallpapoz.sf.net) ). Wallpapoz use technique checking output of a program with some parameters to know if user has changed workspace or not every one second. The name of the program is xprop if you want to know. Well, it is not efficient. I admit that but I don't know a better way. However somebody checked my code and told me that this is not good way to know if user has changed workspace or not which I already knew. He told me there is a thing called libwnck which I didn't know. Then in next version I will change the way so the daemon program will be less resource hungry which is a better thing. 

The problem start here. Some users send me email told me that wallpapoz does not work with compiz/xgl. After researching, I learned that compiz/xgl make gnome believe there is only one workspace which mean wallpapoz which depend ( in current version ) on output of program called xprop with some parameters and ( in next version ) libwnck library does not have a clue that user has changed workspace. 

However after researching again, I found there is a patch for libwnck for compiz. Here are the links:
[http://lists.freedesktop.org/archives/compiz/2006-April/000027.html](http://lists.freedesktop.org/archives/compiz/2006-April/000027.html)
[http://www.compiz.net/viewtopic.php?id=781](http://www.compiz.net/viewtopic.php?id=781)

I have simple program that will tell you what workspace you are in now if you change workspace written in python. Here it is.
```

import gtk
import wnck

def workspace_changed(screen):
  workspace =  screen.get_active_workspace()
  print workspace.get_name()

screen = wnck.screen_get_default()
screen.connect("active_workspace_changed", workspace_changed)

gtk.main()

```

Make sure you have this packaged installed: python2.4-gnome2-desktop. Apt-get it.

I do not have 3d card so I can not install compiz/xgl which means I am asking your help to test this simple program with compiz/xgl after patching the libwnck library. If it works, my next version of wallpapoz which I am currently working on will work with compiz. Vice versa, off course. 

Save the code to filename with extension .py. Then open gnome-terminal ( or whatever terminal emulator you like ). Run it with python:
$ python /you_directory_which_contains_the_script/your_script_name.py

Then try to change workspace. If it works, you will get the output similar with this:
$ python workspace.py
Workspace 2
Workspace 1
......

If it works, reply this thread how do you patch the libwnck and additional information that might useful.

Thank you.

---

