---
title: "Unreal Tournament doesn't run"
date: 2006-02-18
forum: Gaming &amp; Leisure
---

### Post by Kobra on 2006-02-18
Ok, I just bought a new copy of UT2k4, and installed.  Ran beautiful after it installed, but now it doesn't.  I get this error when I try to start it:
```
will@kobra:~$ ut2004
Can't find 'ini:Engine.Engine.GameEngine' in configuration file

History:

Exiting due to error

```

---

### Post by Mikecore on 2006-02-18
Did you install as root? if you did then when you ran the game was it as root?
and now you are usings your user account? this can be a problem if you don't have the right permissions set. If not try reinstalling.

---

### Post by Kobra on 2006-02-18
I had to use sudo to install.  I install all my games to /usr/games/ and it won't let me under normal user installation.  I don't have to be using sudo to play my Quake 3 and Quake 4, same with ET.  I'll try reinstalling tonight I guess

EDIT:  Fixed.  Deleted the /.ut2004 folder and ran UT2004 again.  Works like a charm

---

### Post by obx-jdt on 2006-02-19
[QUOTE=Kobra]I had to use sudo to install.  I install all my games to /usr/games/ and it won't let me under normal user installation.  I don't have to be using sudo to play my Quake 3 and Quake 4, same with ET.  I'll try reinstalling tonight I guess

EDIT:  Fixed.  Deleted the /.ut2004 folder and ran UT2004 again.  Works like a charm[/QUOTE]
su in a term, then type "ut2004" Happy fragging ;-)
Nevermind, just saw the EDIT........LOL:-#

---

### Post by leech on 2006-02-20
Uhm, you shouldn't be running your software as root, that's just a bad idea in general (thank you windows!)  Probably the problem was caused by installing as root, then at the end of the installation, it asks "would you like to play now" or something to that effect.  More than likely you said yes, so it created the .ut2004 directory with root's permissions.  So it would not load unless you started it as super user.  Since you removed the directory and now it works as normal user because .ut2004 is now read/write for the normal user.

Leech

---

