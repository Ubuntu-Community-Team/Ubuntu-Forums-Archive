---
title: "add a window manager entry to GDM"
date: 2005-01-10
forum: Desktop Environments
---

### Post by jaybee99 on 2005-01-10
I want to install windowlab as an option on the gdm login screen on ubuntu 4.10 - none of the advice I've found here or elsewhere seems to quite fit, cos it's referring to dirs etc that don't exist, eg /etc/gdm/Sessions - can anyone point me to an HOWTO or other ideas?

TIA

---

### Post by ulrich on 2005-01-10
as far as i understand gdm/sessions.. if these directories are not there:
simply create them and go ahead!

am i right in this?

---

### Post by #Greg on 2005-01-10
Yea, you create the required directories and files needed yourself, there was a great howto I saw on this a while ago but I can't find it now.

If all else fails, install via Synaptic, which'll do all that stuff for you, it's certainly more comfortable using Synaptic to install window managers than apt alone.

---

### Post by jaybee99 on 2005-01-10
well, I followed these instructions - [http://lists.debian.org/debian-user/2002/10/msg04622.html](http://lists.debian.org/debian-user/2002/10/msg04622.html) - but for windowlab not windowmaker, thought it might work as they're for debian, but I have no new entry on the gdm sessions menu...I think I also need to edit /etc/X11/gdm/Xsession but don't know how. Any ideas?

(I can't install via apt as AFAIK it's not in any repository...)

---

### Post by ladoga on 2005-01-10
[QUOTE=jaybee99]well, I followed these instructions - [http://lists.debian.org/debian-user/2002/10/msg04622.html](http://lists.debian.org/debian-user/2002/10/msg04622.html) - but for windowlab not windowmaker, thought it might work as they're for debian, but I have no new entry on the gdm sessions menu...I think I also need to edit /etc/X11/gdm/Xsession but don't know how. Any ideas?

(I can't install via apt as AFAIK it's not in any repository...)[/QUOTE]
Compiling is ok too. :) I just compiled flux and added it to GDM.


You need to add .xsession file to your users home folder.
Go to terminal and type: 
```
gedit .xsession
```

inside .xsession you should put something like:
```
exec windowlab
```  This should make windowlab your default session in GDM menu. (You can change it later there) If that doesnt work, then $ windowlab is probably a wrong command to start windowlab, just put there the correct one and it will work. (you can add path to it too).

Ps. If you want to use nautilus in windowlab like i do in fluxbox, just add following line to the beginning of your .xsession file:
```
gnome-settings-daemon &
```

---

### Post by jaybee99 on 2005-01-11
thx ladoga, I'll let you know how I get on

---

### Post by Danilo on 2005-01-11
[QUOTE=ladoga]
```
gnome-settings-daemon $
```[/QUOTE]
That probably ought to be: "gnome-settings-daemon &" (ampersand for background execution, instead of a dollar sign).

---

### Post by jaybee99 on 2005-01-11
[QUOTE=ladoga]Compiling is ok too. :) I just compiled flux and added it to GDM.


You need to add .xsession file to your users home folder.
Go to terminal and type: 
```
gedit .xsession
```

inside .xsession you should put something like:
```
exec windowlab
```  This should make windowlab your default session in GDM menu. (You can change it later there) If that doesnt work, then $ windowlab is probably a wrong command to start windowlab, just put there the correct one and it will work. (you can add path to it too).

Ps. If you want to use nautilus in windowlab like i do in fluxbox, just add following line to the beginning of your .xsession file:
```
gnome-settings-daemon $
```[/QUOTE]


adding an .xsession file has had no effect unfortunately - also, I want windowlab as an option from the gdm menu, not executed automatically. (That's the right command, I can log in to failsafe and start it that way...)

---

### Post by doni on 2005-01-12
locate a *.desktop file, susch as gnome.desktop or xfce.desktop and make a similiar file for your environment...

this will work

---

### Post by ladoga on 2005-01-12
[QUOTE=Danilo]That probably ought to be: "gnome-settings-daemon &" (ampersand for background execution, instead of a dollar sign).[/QUOTE]

yes ofcourse, sorry for typo / brain malfunction.  :oops:  
edited.

---

### Post by jaybee99 on 2005-01-12
[QUOTE=doni]locate a *.desktop file, susch as gnome.desktop or xfce.desktop and make a similiar file for your environment...

this will work[/QUOTE]

you're right, it does! :) Thanks for that. Anybody with the same problem, I created /usr/share/xsessions/windowlab.desktop as a cut down version of gnome.desktop and it looks like this:

```

[Desktop Entry]
Encoding=UTF-8
Name=WINDOWLAB
Comment=This session logs you into WINDOWLAB
Exec=/usr/X11R6/bin/windowlab
# no icon yet, only the top three are currently used
Icon=
Type=Application

```

---

