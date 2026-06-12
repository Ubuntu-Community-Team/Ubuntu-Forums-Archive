---
title: "Anyone know of JUST a Word Processing Desktop??"
date: 2008-03-03
forum: Desktop Environments
---

### Post by martnus on 2008-03-03
Hey People,

   I know that this is kind of a strange question, but when I explain why, I think it'll make more sense....

   I am a Computer Technician and I work in a school system in the Intermediate School.  We have a 30 Workstation lab that was designed a few years ago using 12-14 year old computers with the sole use as a "Keyboarding Lab" (someones fancy way of saying "typing"...lol).  Anyway, the way it is set up now, most of the workstations boot off of a Fedora Server and the students open up the OpenOffice Word Processor Program and start typing.  Since these computers are old and starting to fail, I have since started to replace them little by little with free-standing Xubuntu installs, getting them off the server-boot.

    What would make most sense here is a Linux install that bypassed all of the regular installation stuff and ONLY booted right to the Word Processing Program (like AbiWord or something).  I seriously doubt that anyone has written anything for just this use since this is a very specific need, but I thought I would ask anyway.

    I appreciate you all reading......Martnus

---

### Post by aysiu on 2008-03-03
You could boot a minimalist window manager like IceWM or Fluxbox, not run any services, and include *oowrite* as the startup command.

---

### Post by MONODA on 2008-03-03
well... you could try using arch linux. You would have to configure some stuff and install xorg but you could do it. What you would do is install abi-word with pacman and then in the .xinitrc (i think thats what its called...) file you should add a line saying:
> exec abiword
i have tried this with firefox and it works ok but not so great since there isnt a window manager to be able to move around popup windows. I think you should try my idea out. if you need clearification on how to do this or what I mean, feel free to ask.
EDIT: Ahh.. I think asyiu's solution is simpler than mine...

---

### Post by fracturedmorals on 2008-03-03
I have no real experience in this area, but I thought I would make an attempt at some input.

Perhaps you could create a python script (Or your language of choice)  that utilizes the os module to execute a minimal window manager (like openbox) and have it automatically execute abiword.

Something like.
```

import os
os.system('/usr/bin/openbox &')
os.system('/usr/bin/abiword')

```

then chmod a+x it...

Then you could create a new session in /usr/share/xsessions like "abisession.desktop".
which could be something similar to:
```
[Desktop Entry]
Encoding=UTF-8
Name=Abibox Session
Comment=Use this session to run a word processor in a minimal environment
Exec=/usr/local/bin/yourpythonscript
Icon=
Type=Application

```

Then from GDM you could set it as the default session (If you're using GDM)....just an Idea.

---

### Post by jeffus_il on 2008-03-03
You  autologin xubuntu by setting it up in ```
gdmsetup
``` and then setting up xfce to autostart a word processor. This will open the Word processor straight after boot. There are many other ways to do this to autologin using inittab and using startx instead of gdm. but the simplest is the first.

---

### Post by martnus on 2008-03-04
I like Aysui's idea, the minimalist install would work.  The idea of installing and having it boot right into AbiWord is something I thought of, but then you are still installing the ENTIRE Linux program instead of just a Word Processor.

Still, all are great suggestions and I thank you ALL for taking time to help out a newcomer!!  This is basically why I keep coming back to this forum (besides the great information that is!!)

---

