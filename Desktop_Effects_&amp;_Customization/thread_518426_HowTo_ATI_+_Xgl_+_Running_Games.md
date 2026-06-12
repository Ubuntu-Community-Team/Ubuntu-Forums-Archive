---
title: "HowTo: ATI + Xgl + Running Games"
date: 2007-08-05
forum: Desktop Effects &amp; Customization
---

### Post by jpereira on 2007-08-05
Hi,

If you own an ATI card and want to use the latest in desktop effects (like Compiz Fusion), you have basically two options: AIGLX with the Open Source drivers or Xgl with ATI's proprietary drivers.

If you go with the AIGLX and the Open Source drivers on some cards you'll still experience several problems. As these drivers mature, those will likely go away. 
In the meantime, if you stick with Xgl, then you'll face a number of other problems. I'm not an expert, but that seems mainly related to the fact that ATI's official drivers don't support Direct Rendering or a number of OpenGL extensions. This makes running many games impossible under Xgl.

One solution for this is launching a basic X server, just for the game you intend to run. For this, you first have to a regular user to launch a X server. Insofar, the only way I found to do this was by editing the XWrapper.config file. 
```

gksudo gedit /etc/X11/Xwrapper.config

```

Replace the line that says
```
allowed_users=console
```
with
```
allowed_users=anybody
```

Now you'll be able to launch an X server as a regular user. You can then use a script like this to run your game. As an example, let's create a script to run Unreal Tournament 2004:
```
gksudo gedit /usr/local/bin/ut2004
```

And put the following:
```

#!/bin/sh
# Requirements:
#   user must be able to run X terminal. Suggestion: set allowed_users=anybody
#   on /etc/X11/Xwrapper.config

# Run this application
#  change this to whatever you wanna run
CMD="cd /usr/share/games/ut2004/System && ./ut2004-bin && cd -"

# Temporary screen number (anything will do)
SCREEN=5

# Launch the X server
X -br -nolisten tcp -terminate :$SCREEN &

# Get xauth for the current display and set new display
cookie="$(xauth -i nextract - $DISPLAY | cut -d ' ' -f 9)"
xauth -i add :$SCREEN . "$cookie"

#Launch xterm with the supplied command
export DISPLAY=:$SCREEN.0
xterm -geometry 1x1+-100-100 -e "$CMD"

```

And make the script executable:
```
sudo chmod a+x /usr/local/bin/ut2004
```

You can then run /usr/local/bin/ut2004 from a terminal in order to launch the game, or even place a shortcut in the panel. It should launch a separate X server, switch to it, and once you leave the game, it'll shutdown and return to the Xgl server.

I'd love to get input and know if it works for you, and other ideas on how to improve this method. Namedly, alternatives to allowing every user to run an X server.

Cheers

---

### Post by aethermade on 2007-09-07
Is there a way to get the second X server to be rotated 90 degrees? I have a tablet, and if I could start up a new X server, rotated 90degrees, with a note-taking program, that would be amazing. I can't get any other method to work.

---

### Post by shaggy999 on 2007-09-07
Wow! This is great advice! I'm going to have to try this tonight when I get home. :)

Oh! And thanks for the comments in your script... you just answered my other thread. :)

---

### Post by Ant_Merlin on 2007-09-23
Hi, Thanks for the advice, however I have come across an even easier solution. XGL creates a second display (DISPLAY:1) on top of Xserver to use its 3d effects and this is why 3d games fail in XGL. all you need to do is use the command DISPLAY=:0.

I created a simple script for each of my games eg Sauerbraten

> 
gksudo edit /usr/local/bin/sauerbraten

#!/bin/sh
DISPLAY=:0
/usr/games/sauerbraten

save this then:

sudo chmod a+x /usr/local/bin/sauerbraten



I then edit the launcher in the menu to this path and hey presto, the game works with direct rendering and no crashes. To prove this try:

> 

DISPLAY=:0 glxinfo
returns direct rendering on etc..

me@computer:~$ DISPLAY=:0 glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2



you can also use it for testing other things like glxgears etc.

It has taken me weeks to learn this, maybe we should make a sticky for others, what do you think?

---

### Post by denisliber on 2007-12-17
Well many thanks. that worked very well!
Still this is a problem any game (lbreakout2 for example ) need to be launched in that way!

---

### Post by Truefire on 2008-05-10
Thanks guys! How do we get this stickied? Also, where do I find other program files, like Stellarium and Elisa MCE? Thanks in advance!

Rock on. :guitar:

---

### Post by Truefire on 2008-05-10
> **Truefire said:**
> Thanks guys! How do we get this stickied? Also, where do I find other program files, like Stellarium and Elisa MCE? Thanks in advance!

Rock on. :guitar:

Never mind, I found them. However, I'm still looking for a way to create a nonXGL session in the login window dropdown menu for Wine and the like.

---

### Post by Truefire on 2008-05-10
> **Truefire said:**
> Thanks guys! How do we get this stickied? Also, where do I find other program files, like Stellarium and Elisa MCE? Thanks in advance!

Rock on. :guitar:

EDIT: I figured it out. Just pick 'FailSafe GNOME' in the sessions menu,
and make windows installers executable.

All games work now :D Thanks everybody!

---

