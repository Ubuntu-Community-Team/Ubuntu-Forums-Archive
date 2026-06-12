---
title: "Mame Error"
date: 2009-02-01
forum: General Help
---

### Post by Rytron on 2009-02-01
Hi. Up till today all my Mame roms were working perfectly. Please see the attached picture for the error message. I did run a command I saw on an Ubuntu thread about fixing a no sound problem after I played Typhoon. I think that command is responsible for the Mame error. Strange is that some Mame roms work but others don't.
Has anyone an idea on fixing this?
Thanks.

---

### Post by Rytron on 2009-02-01
i started gxmame in the terminal and i got this:
```
:~$ gxmame 
** Message: Loading gamelist
** Message: Loaded 6166 roms by 720 manufacturers covering 32 years.
** Message: with 231 games supporting samples.
** Message: catver not loaded, using default values
/dev/js0: No such file or directory
** Message: No Joystick found
/home/myusername/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/myusername/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/myusername/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

** (gxmame:25159): WARNING **: Couldn't find themed icon for "gxmame-sound-toolbar"

** (gxmame:25159): WARNING **: Couldn't find themed icon for "gxmame-display-toolbar"

** (gxmame:25159): WARNING **: Couldn't find themed icon for "gxmame-rom"

** (gxmame:25159): WARNING **: Couldn't find themed icon for "gxmame-emblem-played"

** (gxmame:25159): WARNING **: Couldn't find themed icon for "gxmame-emblem-available"

** (gxmame:25159): WARNING **: Couldn't find themed icon for "gxmame-emblem-sound"
```

---

### Post by Rytron on 2009-02-03
I sorted my MAME error warning. I am not certain which one thing did it. Here's what I did:
Re added my Rom folder directory.
Made the Audio and Mixer device boxes blank.
Changed the resolution from 4 width and 4 height to 1 width and 1 height.

;)

---

