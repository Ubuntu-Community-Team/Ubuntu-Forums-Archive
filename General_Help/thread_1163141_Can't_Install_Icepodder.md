---
title: "Can't Install Icepodder"
date: 2009-05-18
forum: General Help
---

### Post by brian_hayward on 2009-05-18
I've been trying to install Icepodder in my new install of Ubuntu 9.04 and i can't get it to install.  I try to install the .deb but the gdeb installer tells me i need python-xmms but i can't install the python-xmms.  From my understanding python-xmms isn't being used anymore.  Any help or suggestions are greatly appreciated.  


P.S. I don't want to use gpodder, i have used it and i don't like the way it names the folders containing the audio tracks.

---

### Post by khelben1979 on 2009-05-18
Have you tried to install it [from source code]("http://www.icepodder.com/wp-content/uploads/2007/02/IcePodder-5.4.tar.bz2")?

(Tried it myself a few minutes ago and it worked for me, compiling from source that is.)

---

### Post by brian_hayward on 2009-05-18
> **khelben1979 said:**
> Have you tried to install it [from source code]("http://www.icepodder.com/wp-content/uploads/2007/02/IcePodder-5.4.tar.bz2")?

(Tried it myself a few minutes ago and it worked for me, compiling from source that is.)

I am pretty new to linux, I've read the ubuntu book, and i've done some research on the net about how to compile code from source but i have no luck whenever i try it.  When you did it did you use the ever popular

./configure (this is the line that I ALWAYS fail at, the shell always tells me there is no such directory)
make
sudo make install

I also tried to read the README which came with the .tar file but i was with my daughter this weekend and she commands so damn much attention (what is up with that?) so i wasn't able to sit down and read it as thoroughly as i wanted to so if you could offer up some hints that would be great.  thanks.

---

### Post by khelben1979 on 2009-05-18
Doing it the usual way, well.. not this time. Do like I've written below:

cd [where you unpacked the source]
```
sudo ./install.sh
```

Execute it by typing this from a graphical shell like xterm for example:
```
/usr/bin/icepodder
```

You can also go into that directory structure and just make a soft link to the desktop by drag and drop.

---

### Post by brian_hayward on 2009-05-18
> **khelben1979 said:**
> Doing it the usual way, well.. not this time. Do like I've written below:

cd [where you unpacked the source]
```
sudo ./install.sh
```

Execute it by typing this from a graphical shell like xterm for example:
```
/usr/bin/icepodder
```

You can also go into that directory structure and just make a soft link to the desktop by drag and drop.

Ok, i installed icepodder the way you explained and then i tried to launch it and i got the output below.  Any suggestions?    

> CastPodderGui.py:48: DeprecationWarning: The wxPython compatibility package is no longer automatically generated or actively maintained.  Please switch to the wx package as soon as possible.
  from   wxPython.wx import *
/usr/share/icepodder/ipodder/core.py:31: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  from   sha import *
xmms couldn't be imported
Beep-Media-Player couldn't be imported
/usr/share/icepodder/ipodder/history.py:23: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import logging,md5,time,os,threading,time
Traceback (most recent call last):
  File "CastPodderGui.py", line 3623, in <module>
    main()
  File "CastPodderGui.py", line 3614, in main
    ipodder = core.iPodder(config,state)
  File "/usr/share/icepodder/ipodder/core.py", line 1155, in __init__
    self.feeds = feeds.Feeds(self.config, self.state)
  File "/usr/share/icepodder/ipodder/feeds.py", line 359, in __init__
    self.clean_state_database()
  File "/usr/share/icepodder/ipodder/feeds.py", line 789, in clean_state_database
    for key in state.iterkeys(): 
  File "/usr/share/icepodder/ipodder/state.py", line 228, in iterkeys
    return self.__shelf.iterkeys()
  File "/usr/lib/python2.6/_abcoll.py", line 336, in iterkeys
    return iter(self)
  File "/usr/lib/python2.6/bsddb/dbshelve.py", line 167, in __iter__
    return self.db.__iter__()
AttributeError: 'DB' object has no attribute '__iter__'

---

