---
title: "custom Desktop Environment"
date: 2005-06-14
forum: Desktop Environments
---

### Post by Lechio on 2005-06-14
Wanted to make a script to run some applications on X startup, to be able to run it
on a slow machine. It would only have XFCE Window  Manager and a lightweight panel.
Here's the ideia:
```
#!/bin/bash
## KICKX ultra-small desktop
xinit -- :1.0 | xfwm4 | Esetroot /mnt/Style/wallpapers/tux.png | pypanel | 
/usr/bin/Etermer
``` 

It's not correct as xfwm4 needs X running before it starts.
Can anyone help on how to do a script that checks if X is running on display 0 (and if
it is changes to the next one) and when it's done loading X loads the next commands?
Tanx :)

---

### Post by hw-tph on 2005-06-14
Look into using .xinitrc instead. This allows for starting any number of applications and your window manager of choice. Here is the .xinitrc (actually it's my ~/.xsession but ~/.xinitrc is symlinked to it so I have the same environment no matter if I log in from GDM or use startx):

```
eval $(cat ~/.fehbg) &
lineakd &
fbpanel &
torsmo &
xrootconsole -fn *lime* -fg Grey -geometry 140x6+320+738 /var/log/messages &
exec openbox
```

Note that all commands before the last one end with an ampersand character - "&". This kicks the process into the background and continues with the next one. If you don't do this the script will wait until execution of the program has ended -  fbpanel won't launch until lineakd has terminated (and we do want them running all at once, right?) and so on. Finally, the exec statement (note the absence of ampersand) replaces the script with the named program - in my case openbox. This means that when that program ends, the script ends and thus your X session.

Hope that gets you started.


Håkan

---

### Post by Lechio on 2005-06-14
Tank you that's what i was looking for. Only have one small problem, didn't
really wanted to execute something like openbox, as it replaces XFCE window manager  :-? 
And if the exec part is omited, then the X server just goes down :( . Guess i'll have to live
with openbox menus and window decorations. Tank you.

---

### Post by Equanimity on 2005-06-14
Your .xsession file would look something like this:

[INDENT][FONT=Courier New]Esetroot /mnt/Style/wallpapers/tux.png &
pypanel &
Etermer &
exec xfwm4[/FONT][/INDENT]
BTW, I'd suggest using a symlink for your background, so if you ever decide to change the background only the symlink would need changing, not this config file. That is, replace the first command with "Esetroot ~/.background", and use "ln -sf ... ..." to link ~/.background to tux.png.

---

### Post by Lechio on 2005-06-15
Works!  :smile: 
Guess it was missing the .xsession file.
Tank you, best regards.

---

### Post by daacosta on 2006-02-18
Sorry for intruding but where do I find the .xinitrc configuration file?  I just want to start conky (a program similar to torsmo) on the background.

Thanks!


-D-

---

