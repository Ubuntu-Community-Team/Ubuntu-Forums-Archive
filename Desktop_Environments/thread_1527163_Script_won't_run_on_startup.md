---
title: "Script won't run on startup"
date: 2010-07-09
forum: Desktop Environments
---

### Post by v1nsai on 2010-07-09
I've got a script that I always have run on startup that enables two finger scrolling on my laptop touchpad.  However, it has randomly stopped being run on startup.  I have it listed in Preferences > Startup Applications, and copying and pasting the command into the command line works just fine, but it still won't run automatically.

All my other entries in the list seem to run just fine, its just that one that won't for some reason.  I'll post it below, it isn't long, hopefully someone can shed some light on this.

Here's the script itself
```

#!/bin/sh
#
# Use xinput --list-props "SynPS/2 Synaptics TouchPad" to extract data
#

# Set multi-touch emulation parameters
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1

# Disable edge scrolling
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 8 1 0 0

# This will make cursor not to jump if you have two fingers on the touchpad and you list one
# (which you usually do after two-finger scrolling)
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 32 110


```

and to run it I do
```
sh /home/v1nsai/Documents/fixtwofinger.sh
```

Any help appreciated, I'm stumped.

---

### Post by arsenic23 on 2010-07-09
I'm have a similar problem in lucid.  Suddenly none of my startup scripts are working.  The one is just a one liner that starts pms-linux.  I can run it manually fine but it doesn't work when I log in like it should.

I'll mess with it over the weekend.

---

### Post by v1nsai on 2010-07-10
Isn't there a script called .profile or something that runs on startup?  You can call a script from inside another script, right?

---

### Post by jbo5112 on 2010-07-10
Your .profile runs whenever a terminal window is started.  I don't think it runs when you log in to Gnome or KDE.

---

### Post by mcduck on 2010-07-10
> **jbo5112 said:**
> Your .profile runs whenever a terminal window is started.  I don't think it runs when you log in to Gnome or KDE.

Actually ~/.profile is executed when you log in, and ~/.bashrc is executed when you open a terminal.

For example I need to add a couple of directories to my path variable. Since I need them to be available from the moment I log in, and not just in terminals, I need to define them in ~/.profile. on the other hand, I want to get a fortune on each terminal I open (or when I log into a TTY), so I need to add the fortune command to ~/.bashrc. If I added it into ~/.profile instead it wouldn't have any noticeable effect, I'd never see the actual output anywhere. (If I used zenity to display the fortune output in a graphical window I could of course add that command to ~/.profile and I'd get a popup window with a fortune every time I log into my desktop)

---

### Post by d3v1150m471c on 2010-07-10
> **jbo5112 said:**
> Your .profile runs whenever a terminal window is started.  I don't think it runs when you log in to Gnome or KDE.

yes, it does. and a strong suggestion, if you add commands to bash.rc or .profile is to append a "&" to the end of those commands.

---

### Post by v1nsai on 2010-09-07
Well, adding it to .profile worked but it freezes up my system while booting.  I switched over to a terminal and it said that the x server couldn't be found, so the script was loading but it was loading before the x server was running -_-

I'm gonna try putting "sleep 30" in front of it to give it time, I'll report back if it works.

---

