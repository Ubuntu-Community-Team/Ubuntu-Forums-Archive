---
title: "Compiz SegFault Randomly in 11.04"
date: 2011-05-06
forum: Desktop Environments
---

### Post by [YF] Daniel on 2011-05-06
I am on a fresh install of Narwal. I've switched to classic because unity wasn't mature enough IMO. Just installed ccsm and now my display will crash randomly after running for a short while.

```
daniel@orange:~$ compiz --replace --debug
compiz (core) - Debug: Could not stat() file /home/daniel/.compiz-1/plugins/libcore.so : No such file or directory
compiz (core) - Debug: Could not stat() file /usr/lib/compiz/libcore.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/daniel/.compiz-1/plugins/libccp.so : No such file or directory
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
compiz (core) - Debug: Could not stat() file /home/daniel/.compiz-1/plugins/libbailer.so : No such file or directory
Initializing bailer options...done
compiz (core) - Debug: Could not stat() file /home/daniel/.compiz-1/plugins/libdetection.so : No such file or directory
Initializing detection options...done
compiz (core) - Debug: Could not stat() file /home/daniel/.compiz-1/plugins/libcomposite.so : No such file or directory
Initializing composite options...done
compiz (core) - Debug: Could not stat() file /home/daniel/.compiz-1/plugins/libopengl.so : No such file or directory
Initializing opengl options...done
compiz (core) - Debug: Could not stat() file /home/daniel/.compiz-1/plugins/libdebugspew.so : No such file or directory
Initializing debugspew options...done
compiz (core) - Debug: Could not stat() file /home/daniel/.compiz-1/plugins/libdecor.so : No such file or directory
Initializing decor options...done
compiz (core) - Debug: Could not stat() file /home/daniel/.compiz-1/plugins/libgrid.so : No such file or directory
Initializing grid options...done
compiz (core) - Debug: Could not stat() file /home/daniel/.compiz-1/plugins/libcompiztoolbox.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/daniel/.compiz-1/plugins/libsnap.so : No such file or directory
Initializing snap options...done
compiz (core) - Debug: Could not stat() file /home/daniel/.compiz-1/plugins/libtext.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/daniel/.compiz-1/plugins/libregex.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/daniel/.compiz-1/plugins/libresize.so : No such file or directory
Initializing resize options...done
compiz (core) - Debug: Could not stat() file /home/daniel/.compiz-1/plugins/libmousepoll.so : No such file or directory
Initializing mousepoll options...done
compiz (core) - Debug: Could not stat() file /home/daniel/.compiz-1/plugins/libmove.so : No such file or directory
Initializing move options...done
compiz (core) - Debug: Could not stat() file /home/daniel/.compiz-1/plugins/libimgpng.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/daniel/.compiz-1/plugins/libplace.so : No such file or directory
Initializing place options...done
compiz (core) - Debug: Could not stat() file /home/daniel/.compiz-1/plugins/libgnomecompat.so : No such file or directory
Initializing gnomecompat options...done
compiz (core) - Debug: Could not stat() file /home/daniel/.compiz-1/plugins/libsession.so : No such file or directory
Initializing session options...done
Setting Update "shadow_match"
Setting Update "run_command_terminal_key"
Segmentation fault
```

```
daniel@orange:~$ dpkg -l | grep compiz
ii  compiz                                1:0.9.4+bzr20110415-0ubuntu2               OpenGL window and compositing manager
ii  compiz-core                           1:0.9.4+bzr20110415-0ubuntu2               OpenGL window and compositing manager
ii  compiz-gnome                          1:0.9.4+bzr20110415-0ubuntu2               OpenGL window and compositing manager - GNOME window decorator
ii  compiz-plugins                        1:0.9.4+bzr20110415-0ubuntu2               OpenGL window and compositing manager - plugins
ii  compiz-plugins-main                   0.9.4+bzr20110406-0ubuntu2                 Compiz Fusion plugins - main collection
ii  compizconfig-backend-gconf            0.9.2.4-0ubuntu1                           Compiz Fusion configuration system - gconf backend
ii  compizconfig-settings-manager         0.9.4-0ubuntu2                             Compiz configuration settings manager
ii  libcompizconfig0                      0.9.4-0ubuntu2                             Settings library for plugins - OpenCompositing Project
ii  python-compizconfig                   0.9.4-0ubuntu1                             Compizconfig bindings for python
```
```
daniel@orange:~$ tail /etc/apt/sources.list
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main
```

---

### Post by PatrickVogeli on 2011-05-14
same here...

---

### Post by Alexis Wilke on 2011-10-03
Same here, I also posted on that other thread:

[http://ubuntuforums.org/showthread.php?p=11306520#post11306520](http://ubuntuforums.org/showthread.php?p=11306520#post11306520)

Although, when I started compiz on the command line like Daniel, I did not get the crash...

---

### Post by system11 on 2011-10-19
Did anyone ever fix this?  I've got a bunch of users saying 'me too'.

---

