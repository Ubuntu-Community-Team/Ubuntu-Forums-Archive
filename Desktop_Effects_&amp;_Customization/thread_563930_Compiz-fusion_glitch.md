---
title: "Compiz-fusion glitch"
date: 2007-09-30
forum: Desktop Effects &amp; Customization
---

### Post by Masterizaak on 2007-09-30
I put it compiz and I dont have a border, and when I start compiz it goes, I go compiz --replace and it says /usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libccp.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'ccp'

I have a pic, for more info, but other than that..what should I do?

---

### Post by broncavfan on 2007-10-01
I'm getting that same error.  Compiz tries to load, but I don't get any window borders and I don't notice  ANY compiz-fusion effects running.  I also cannot run CCSM.  It gives me the following:

```

Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

```

I wish I had compiz again :(

---

### Post by Presto123 on 2007-10-01
[http://forum.beryl-project.org/viewtopic.php?f=35&t=1631](http://forum.beryl-project.org/viewtopic.php?f=35&t=1631)

Try that and see if that helps.

I searched through the forums here and found the answer to my problem earlier today because I had the same problem. I cannot for the life of me find out the simple line I used in terminal.

Basically, all I did was change the depth and it works totally fine now.

If you know the code to change the depth, change it to "24". Otherwise, someone who knows that simple code will have to help, or you can find it on these forums if you search long enough.

---

### Post by JARHEAD on 2007-10-02
same problem here..
after updating my compiz -october 2nd

here's my error message
```

me@blast:~$ compiz --replace
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libccp.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'ccp'

```

and here is the result from **dpkg -l | grep compiz**
```

me@blast:~$ dpkg -l | grep compiz
ii  compiz                                     0.5.5~git20070928+3v1ubuntu0           OpenGL window and compositing manager
ii  compiz-core                                0.5.5~git20070928+3v1ubuntu0           OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070817-0ubuntu1~ppa1        Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2-0ubuntu2~ppa1                    Collection of plugins from OpenCompositing f
ii  compiz-gnome                               0.5.5~git20070928+3v1ubuntu0           OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 0.3.6-1ubuntu13                        OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             0.5.5~git20070928+3v1ubuntu0           OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.6.99~git20070926+3v1ubuntu0          Plugin and configuration tool - Compiz Fusio
ii  libcompizconfig-backend-gconf              0.5.2+git20070813-0ubuntu1~ppa1        Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2-0ubuntu1~ppa2                    Settings library for plugins - OpenCompositi
ii  python-compizconfig                        0.5.2-0ubuntu1~ppa1                    Compiz configuration system bindings

```

thanks

---

### Post by kthakore on 2007-10-03
JARHEAD: it looks like your are mixing up your compiz repositories. 

go into /etc/apt/sources.list

and remove these ones

```

deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

```

or if you have amd

remove these

```

deb http://download.tuxfamily.org/3v1deb feisty eyecandy-amd64
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy-amd64

```

and add only these one

[CODE
deb http://ppa.launchpad.net/amaranth/ubuntu feisty main
deb-src http://ppa.launchpad.net/amaranth/ubuntu feisty main
[/CODE]

do 

```

sudo apt-get update

```

remove and purge previous install

```

sudo apt-get remove --purge compiz*

```

note this will delete ubuntu-desktop and desktop-effects but thats fine as long as u don't restart before doing the next step

```

sudo apt-get install compiz compizconfig-settings-manager desktop-effects ubuntu-desktop 

```

---

### Post by broncavfan on 2007-10-03
I tried adding the new compiz repository, but I still get the same errors after installing again.  When I do a sudo apt-get remove --purge compiz* I get the error message:

E: Couldn't find package compiz-fusion-debian-builder

I tried installing the compiz-fusion-debian-builder but I get the same error.  I'm using an AMD 64 if that helps.  Any help is greatly appreciated everybody.  My RAM is feeling lonely without compiz :(

---

### Post by kthakore on 2007-10-04
you don't need to compiz-fusion-debian-builder
Just follow those instructions and alt+f2

compiz --replace

---

