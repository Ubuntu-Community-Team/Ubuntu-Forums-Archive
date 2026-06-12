---
title: "User not authorized to run the X server"
date: 2006-06-09
forum: Desktop Environments
---

### Post by adam_kimber on 2006-06-09
I used to use a script on Breezy (where it worked fine) to create an xserver  and run mplayer on my TV. This was preferrable to using Twinview or any other option for me. All was well until I upgraded to 6.06 LTS and now when running the script I now get the following error:

X: user not authorized to run the X server

All I need to know really is how to make my user capable of running X servers as  I would like to be able to run the script from the right click menu in Gnome as I did in Breezy. 

Here is the script i use:

#!/bin/sh
exec /usr/bin/X11/xinit /usr/bin/xterm -ut -e \
  /usr/bin/mplayer -stop-xscreensaver -fs -vo sdl "$@" -- /usr/X11R6/bin/X :1 -layout tv

I hope someone can help! :) 

Adam

---

### Post by adam_kimber on 2007-04-22
I solved this problem by making my system less secure. I am still looking for a way to run the above script    without comprimiising the scurity of my Ubuntu box. 

To get the script working type the following into a console.
 
```
sudo dpkg-reconfigure x11-common
```

Then select Anybody and hit OK. On the next screen leave the default value and hit OK. 
The script will now run without any errors.

---

