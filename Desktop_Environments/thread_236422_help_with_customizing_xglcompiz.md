---
title: "help with customizing xgl/compiz"
date: 2006-08-14
forum: Desktop Environments
---

### Post by thepoeticdragon on 2006-08-14
hey all, i have a question regarding compiz customization. i followed the guide here for installing xgl, and it worked flawlessly: 

[http://tazforum.thetazzone.com/viewtopic.php?t=2189](http://tazforum.thetazzone.com/viewtopic.php?t=2189)

however, i noticed that installing themes in the system 'Theme' doesn't work anymore. plus, i did some research and found that i need a gcompizthemer/cgwd in order to do such things. but with this particular setup (as supposed to the other guides for xgl around here), i don't know how to activate those programs over the gnome-window-decorator. plus, since my xgl is in a different session, i would like the xgl configuration to be separate from ym gnome session (if this isn't possible, that's okay, though). basically, i'm looking for a little guidance on how to begin customization of compiz, using the above TAZ guide as a base.

thanks.

---

### Post by Cable on 2006-08-14
To enable theming:

Open your terminal.  Type the following command
```

sudo gedit /usr/bin/startcompiz

``` 
Change the contents of the file from this...
```

[COLOR=Black][COLOR=#000099]#!/bin/sh  
killall gnome-window-decorator  
wait 
 
gnome-window-decorator &  
compiz --replace gconf &[/COLOR] 
[/COLOR]
```[COLOR=Black]
To this...
[/COLOR]```

[COLOR=#000099]#!/bin/sh  
killall cgwd  
wait 
 
cgwd &  
compiz --replace gconf &[/COLOR] 

``` Save the file and exit gedit.

Now, in the terminal, type this...
```

sudo apt-get install cgwd cgwd-themes

``` Now reboot.  After rebooting, log into your XGL session.  Go to System>Preferences>CGWD Themer.  The themer program should open, and you should have a large list of themes to choose from.

---

### Post by thepoeticdragon on 2006-08-14
THANK YOU

i've seen these steps in a couple other tutorials, but without the editing 'startcompiz' file. you're a real lifesaver, cable.

---

