---
title: "warcraft3 issue"
date: 2007-04-24
forum: Gaming &amp; Leisure
---

### Post by mazingaz on 2007-04-24
I have 7.04 xbuntu installed with wine.  (Installed Warcraft 3 original & FT)
The I input the " wine War3 -opengl" command on the terminal the screen goes back to the login.  
If I input the command "wine War3" (without opengl) it will start the game screen there is too much framing and cannot even move my mouse.  I have looked for the solutions in winehq and there is no suggested solution with this type of problem. 
Does any one encountered similar problem?

---

### Post by mazingaz on 2007-04-24
NE one?

---

### Post by sebas.rhcp on 2007-04-24
you have beryl running?

---

### Post by Drezliok on 2007-04-24
I use ```

wine /home/drezliok/.wine/drive_c/games/Warcraft\ III/war3.exe
```

To start mine.

are your 3D drivers working?

---

### Post by klerfayt on 2007-04-24
Could be Composite issue that is enabled by default, try disabling it in xorg.conf

```
Section "Extensions"
    Option         "Composite" "Disable"
EndSection
```

---

### Post by crimsontide on 2007-04-24
I have the same problem playin wow using wine too. I'm not using Composite. My 3d drivers are working. It only lasts until i sign in (takes a min). I also notice the same thing in the beginning of bf1942 using cedega 6.0 and playing tc:e native.:(

O yea I'm using Ubuntu 7.04.

---

### Post by mazingaz on 2007-04-25
i  uninstalled the xbuntu and reinstalled the ubuntu  I will tryout the suggested solution and wiil let you all know..

---

### Post by mazingaz on 2007-04-26
hmmm...
I don't get it. With the ubuntu 7.04 result is same.  The screen goes back to the login when I executed "wine /~path/War3.exe -opengl.  Without "-opengl" game will start but there is extreme framing and unable to play the game.  Maybe a driver issue?  I have nvidia 6800xt installed.

---

### Post by sloggerkhan on 2007-04-26
I have ati and war3 works fine IF I use proprietary and not open source driver....
Otherwise no ideas.

---

### Post by mazingaz on 2007-04-26
do I need to install the newest driver for the videocard from nvidia inorder to install 3d drivers?
i am  new to using wine to play window games.  anyword of an advice would be appreciated.

---

### Post by mazingaz on 2007-04-26
glxinfo | grep direct <-- when i inputed this command i got following error msg

```
david@david-desktop:~$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

Do i have to download nvidia driver from the nvidia?

---

### Post by mazingaz on 2007-04-26
I finally got it up and running.. All i had to do was turn on the 3D randering from the restricted driver manager and install the game with "sudo wine /media/cdrom0/install.exe" it is now up and running.  Does anyone know how to do an update connected to the battlenet?

---

### Post by sloggerkhan on 2007-04-27
Mine autoupdates. (when I try to connect to b-net.)

---

### Post by mazingaz on 2007-04-27
when I click on the b-net button it tell me to freeup some space when it has more then plenty free spaces avail..

---

### Post by sloggerkhan on 2007-04-27
maybe it doesn't have write permissions or folder is size limited?

---

### Post by mazingaz on 2007-04-27
You were absolutely right.
i had to execute the game with following

```
sudo wine /usr/bin/Warcraft\ iii/War3.exe -opengl
```

and it ran and updated... 

how can i make the short cut on the desktop with the "sudo" at front?

---

### Post by sloggerkhan on 2007-04-27
I don't know what you did, but wine should install stuff into your home directory by default, not your /usr/bin... at least mine does. That makes it so wine has read/write access to all of its directories without sudo.

---

