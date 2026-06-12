---
title: "change behavior of XF86AudioLowerVolume and XF86AudioRaiseVolume"
date: 2010-11-18
forum: Desktop Environments
---

### Post by fabianneke on 2010-11-18
Dear Forum friends,

i recently installed a new ubuntu system (10.10) as media center. 
I am running Gnome and xbmc on it. Until here, everything perfect!

I bought one of those cheapass media center keyboards with multimediakeys. Except for one, they all work out of the box. 

My problem:
When i press the volume down key, gnome lowers the volume of my mediacenter. This might be good for most users, but i have a surround receiver/amplifier (Denon AVR3310) that should handle the sound.


In fact, i am looking for this:
When i press the volume up/down key, instead of changing the volume of my mediacenter, gnome should execute a script i wrote. This script sends commands to my receiver (using the serial port or the network connection) to lower/raise the volume.
I've been googling around for many hours but don't seem to find the solution for this

Small additional question: 
I would like to get the one button that doesn't work yet to work. I have a 'mc' (mediacenter) button on my keyboard. I would like to make this launch xbmc. 
When running 'xev', i don't see any output when i press the button. Any idea?

Thanks in advance for your help!

---

### Post by kostkon on 2010-11-18
You could try setting the shortcuts for the volume up and volume down actions to disabled in *System &#8594; Preferences &#8594; Keyboard Shortcuts* and then making two new custom ones that will have your script(s) as action and XF86AudioLowerVolume and XF86AudioRaiseVolume as shortcuts respectively.

---

### Post by fabianneke on 2010-11-19
Helo,

Thanks for your reply. I tried doing that:
I disabled it in keyboard shortcuts (this works fine) and then added a custom shortcut in apps -> metacity -> global_keybindings in gconf-editor but it didn't work: when i press the button, nothing happens at all.  
To make sure my script didn't have any errors, i set up an other shortcut via gconf-editor (<Ctrl>U) that launches my script. After pressing Ctrl U, i was able to change the volume (execute the script). The problem seems to be that i am unable to use the specific shortcut XF86... in apps -> metacity -> keybindings. Any idea how i can configure them over there?

Thanks,

Fabian

---

### Post by fabianneke on 2010-11-28
bump

---

### Post by fabianneke on 2010-12-05
found it:
system - preferences - keyboard shortcuts
add a new custom shortcut with command and key you want

---

