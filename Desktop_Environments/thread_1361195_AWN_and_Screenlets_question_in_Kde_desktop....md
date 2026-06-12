---
title: "AWN and Screenlets question in Kde desktop..."
date: 2009-12-21
forum: Desktop Environments
---

### Post by Struki on 2009-12-21
I'm running ubuntu but I wanna try out kde enviroment, so I installed kubuntu desktop. When I switch to kde AWN and all the widgets load up and they overlap with my kde panels so I was wondering is there a way to stop them from running in kde but still keep them running in gnome.

---

### Post by Andysan on 2009-12-24
I too would be interested in a solution to this please!

Cheers,

Andy

---

### Post by Andysan on 2009-12-30
I've knocked together what I think is a solution to this.

Copy and paste the following into a text file, name it whatever you like.  I called mine awnscript.sh.  Then make it executable (chmod x awnscript.sh) and copy to /usr/bin.  Finally, click System>Preferences>Startup Applications and change the entry for AWN to point at the bash file.

```
#A bash file to launch awn only if the desktop environment is GNOME
#By Andrew Fletcher
MYPROCESS='gnome-session'

#if gnome-session running
if ps ax | grep -v grep | grep $MYPROCESS > /dev/null
then
#launch awn
awn
fi
```

---

### Post by pritamps on 2009-12-30
You could go to ~/.config/autostart

And in the file awn.desktop, add this line

```
OnlyShowIn=GNOME;
```

This will make sure this only loads in Gnome...Do the same for the other files as well, of course. NotShowIn=KDE; will work as well.

---

### Post by Andysan on 2009-12-30
> **pritamps said:**
> You could go to ~/.config/autostart

And in the file awn.desktop, add this line

```
OnlyShowIn=GNOME;
```

This will make sure this only loads in Gnome...Do the same for the other files as well, of course. NotShowIn=KDE; will work as well.

Hey thanks, thats a much better solution!:guitar:

---

### Post by pritamps on 2009-12-30
Well, I got it off the forums a year back I think :P

---

### Post by demontranoth on 2010-12-02
how do I edit the .desktop files?

---

