---
title: "newbie"
date: 2007-05-25
forum: Desktop Effects &amp; Customization
---

### Post by windows hater on 2007-05-25
i want to install beryl but ever time type sudo and then the password screen comes up it totally locks up

---

### Post by adza on 2007-05-26
can you post a little more information? ie, what distro are you running, beryl is not supported with 6.06 for example. Also some info on your graphics config etc will help people try and help you... however you could try [this thread]("http://ubuntuforums.org/showthread.php?t=357501") as well for help :) Remember, when posting try to put as much info as possible to enable people to help you... the catz around here are wonderfully helpful, however they can't read minds! :)

---

### Post by windows hater on 2007-05-26
im runing ubuntu feisty ati x 1550

---

### Post by Cresho on 2007-05-26
drivers installed?  try glxgears in terminal and see if it all runs right.  If not, then you may need to do what you need to do and get it running.

---

### Post by locke.dragon on 2007-05-26
system>>administration>>synaptic package manager
install these packages.  if it tells you it needs to install other stuff in addition, let it.
either do a search for beryl and look for them on that list, or do an individual search for each one.  

> 
beryl
beryl-core
beryl-manager
beryl-plugins
beryl-plugins-data
beryl-settings
beryl-settings-bindings
emerald
libberyldecoration0
libberylsettings0
libemeraldengine0


after they're all installed, hit alt>>f2 and type "beryl-manager"
right click on the new icon "select window manager>>beryl"
it should work after that.  if it doesn't, post your problems.

---

### Post by windows hater on 2007-05-26
i installed these programs in synaptic package and i ran glxgears and it worked

beryl
beryl-core
beryl-manager
beryl-plugins
beryl-plugins-data
beryl-settings
beryl-settings-bindings
emerald
libberyldecoration0
libberylsettings0
libemeraldengine0


after they were installed i hit alt>>f2 and typed "beryl-manager" ethere my screen flickers or the manger pops up and then i select window manger and it just shuts off on me

---

### Post by locke.dragon on 2007-05-26
what shuts off on you?  and try this.

without turning on beryl manager, open a terminal and type
```

beyrl

```

post what it says.  you should get something similar to
```

link@aperturescience:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

Reloading options
link@aperturescience:~$ 

```

---

### Post by windows hater on 2007-05-26
Checking for XComposite extension               : failed 

thats all it said

---

### Post by locke.dragon on 2007-05-26
this may help

[http://ubuntuforums.org/showthread.php?p=2697784](http://ubuntuforums.org/showthread.php?p=2697784)

just make sure you're following the tutorial that deals with your video card.

---

### Post by windows hater on 2007-05-26
i have a trouble with sudo in terminal

---

### Post by locke.dragon on 2007-05-26
could you define trouble?

---

### Post by windows hater on 2007-05-26
i got the sudo pass thing working and i done the wikki link a few times it still didnt work

---

