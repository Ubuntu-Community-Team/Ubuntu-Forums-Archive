---
title: "Nvidia-settings for tv"
date: 2008-01-09
forum: Desktop Effects &amp; Customization
---

### Post by dysphasi on 2008-01-09
Using gutsy,just reinstalled, I've got the problem that any settings I change for my tv in nvidia-settings for the tv are applied as I want, but are never saved.

The only two settings I need changed are overscan and flicker reduction. But without these being as I set them in the settings panel it looks awful.

I'm using 'sudo nvidia-settings' when I alter them. I am also aware that nvidia-settings -l needs to be run at startup. But even doing this, the overscan returns to defualt, as do any of the other changes I make to the tv settings section.

Please help!

---

### Post by codesplice on 2008-01-09
Disregard my post in the other thread, I think the answer lies here: [http://linuxmint.com/wiki/index.php/Make_nvidia-settings_sticky](http://linuxmint.com/wiki/index.php/Make_nvidia-settings_sticky)

> In your ~ folder is a file called .xinitrc

~ is an "alias" for /home/your_name

A dot (.) first in a file name indicates it's a hidden file so you must turn on "Show hidden files" to see it. If it does not exist - create it (text file).

Then add the following

Code:

#!/usr/bin/env bash
/usr/bin/nvidia-settings --load-config-only &
exec gnome-session

For KDE use

Code:

exec startkde

The exec command must be the last command. Make the file executable

Code:

chmod chmod +x ~/.xinitrc

or use the GUI - right click>Properties>Permissions>Make this file executable

For the xserver to use xinitrc you must create a symlink Code:

ln -s ~/.xinitrc ~/.xsession

This starts nvidia-settings when you start gnome.

This is all that's needed. You will have your personal settings for color and more remaining session after session. 

---

### Post by codesplice on 2008-01-09
ha.  I'm an idiot.

-l == --load-config-only

*facepalm*

---

### Post by dysphasi on 2008-01-09
lol, that got me thinking earlier ;p 

grr still can't get this thing to work

Something must have been upgraded since I set everything up a couple of months back that has stopped things working for me properly.

nvidia-settings simply isn't accepting any changes to the tv. Everything works until reboot, then all the settings I changed are reset to default.
Is there a way of adjusting the default?

---

### Post by codesplice on 2008-01-09
Hmm.  I don't know.  It took me a bit of playing the other day to get the settings for my CRT to stick, even after creating t3h xinitrc script.  But I can't remember what I did.  i'll keep tinkering with my set up and see what I can figure out.

---

### Post by dysphasi on 2008-01-09
A huge thanks! Are you using any overscan/flicker settings? If not, could you and then any chance you could post your nvidia-settings-rc file. 

I read somewhere that someone added TVOverScan[TV-0]=<A number here> and that worked for them, but for me it just returns "No device TV-0"....even though there's a pic on the tv.

---

### Post by codesplice on 2008-01-09
I should note that my CRT is a monitor, not a TV.  I don't really know how much that changes things :p

---

### Post by dysphasi on 2008-01-09
Ahh k, so you wouldn't have the same overscan settings etc... it is odd though, considering I've done all that I did beforehand, everything did work then, it's just not now I've reformatted and set it up to what I thought I had before. :confused:


One other option I'm looking for is to be able to force tv-out. Currently I have one set of cables that's a bit of a devil, it won't allow me to autodetect that a display is attached. This means that whilst the cables work if I take out the working set and plug in this one, they will not keep working after a restart.

---

