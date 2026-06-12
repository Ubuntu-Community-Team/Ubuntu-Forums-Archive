---
title: "[SOLVED] Openbox and xdotool autostart problem"
date: 2008-09-21
forum: Desktop Environments
---

### Post by Jose Catre-Vandis on 2008-09-21
Setup:

Command line install of xubuntu, running openbox window manager

What I want to do:

Put a command in autostart.sh that will:

Start Firefox
Maximise it
Send it below (to the back of all other windows)

but only for this window and not for all firefox windows opened (otherwise I would be using the per-app settings in rc.xml).

I am trying to use xdotool for this. I have setup keybindings for "below" and "maximise" and these work.

If I use an xdotool command to activate the firefox window when openbox is already running I can use a script to do this.

```
xdotool windowactivate $(xdotool search "Mozilla Firefox" | head -1)
xdotool key super+F6
xdotool key alt+F6
```

and firefox does as I wish.

But if I then add firefox to the script and then put this script in autostart.sh all I get is firefox open.

```
#! /bin/bash

#open firefox
firefox
#activate/give focus to firefox window
xdotool windowactivate $(xdotool search "Mozilla Firefox" | head -1)
#send below
xdotool key super+F6
#maximise
xdotool key alt+F6
```

autostart.sh looks like this:

```
# This shell script is run before Openbox launches.
# Environment variables set here are passed to the Openbox session.

#numlock
numlockx on &

#run background
sh $HOME/.fehbg &

#open firefox and send to back and make fullscreen
sh /home/jose/testwin.sh &

#run xfce4 panel
xfce4-panel &
```

I have tried putting in some sleep time in the script and placing the commands directly into autostart.sh, but still get the same problem. If I run in a terminal it seems that firefox never actually "finishes" opening (if that makes any sense) even if I use ; or & or && at the end in the script)

Can anyone shed light on where I am going wrong?

---

### Post by urukrama on 2008-09-21
Why don't you use wmctrl for that? It seems like a much simpler approach, and one that should not give any trouble, I think.

You probably will have to use to commands. Try something like:

> wmctrl -r firefox -b add,maximized_vert,maximized_horz &
wmctrl -r firefox -b add,below &

---

### Post by Jose Catre-Vandis on 2008-09-21
Hi urukrama, thanks for the input.

Your method does as good a job as mine!

I have a launcher set up to run the commands and have change the script in autostart.sh. If I boot to desktop and open Firefox, then click the launcher, the commands work (mine or yours), but if I try to run the same script in autostart.sh from the login screen, then I only get Firefox to open. So I do not think there is a problem with either method, but more in what is happening when openbox starts up and runs the autostart.sh file, plus the order in which the commands are processed. Possibly firefox starts but while it is still starting, the other commands run, and becasue firefox isn't "there yet", they miss it?

If I put firefox in my launcher script the same happens, Firefox opens but the wmctrl / xdotool commands do not follow

---

### Post by Jose Catre-Vandis on 2008-09-22
Cracked it!

required a sleep command of 3 seconds before the wmctrl commands:

Script: runfox.sh
```
#! /bin/bash
firefox &
sleep 3
wmctrl -r firefox -b add,maximized_vert,maximized_horz &
wmctrl -r firefox -b add,below & 
```

autostart.sh:

```
# This shell script is run before Openbox launches.
# Environment variables set here are passed to the Openbox session.

#run background
sh $HOME/.fehbg &

#run xfce4 panel
xfce4-panel &

#open firefox and send to back and make fullscreen
sh /home/jose/testwin.sh &
```

My route works as well:

Script runfox2.sh:
```
#! /bin/bash
firefox &
sleep 3

xdotool windowactivate $(xdotool search "Mozilla Firefox" | head -1)
xdotool key super+F6
xdotool key alt+F6
```

---

### Post by urukrama on 2008-09-23
> **Jose Catre-Vandis said:**
> Cracked it!

required a sleep command of 3 seconds before the wmctrl commands:

That is what I expected, and I thought you had tried that already. I'm glad you solved the problem, though.

---

### Post by Jose Catre-Vandis on 2008-09-23
> **urukrama said:**
> That is what I expected, and I thought you had tried that already. I'm glad you solved the problem, though.


I had,... both inside the script and in autostart.sh. I guess it was just about finding the right combination of sleep and script! (I'll get more sleep now though, :))

---

