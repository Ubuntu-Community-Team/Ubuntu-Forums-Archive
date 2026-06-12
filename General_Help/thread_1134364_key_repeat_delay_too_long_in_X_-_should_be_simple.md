---
title: "key repeat delay too long in X - should be simple?"
date: 2009-04-23
forum: General Help
---

### Post by mrowth on 2009-04-23
The problem: Ever since upgrading to 9.04, key repeat kicks in a little late in X... starting with the graphical login. So it doesn't seem to depend on the desktop environment/window manager. I get it in KDE and Fluxbox.

From xorg.conf:
```
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#  Identifier "Generic Keyboard"
#  Driver "kbd"
#  Option "XkbRules" "xorg"
#  Option "XkbModel" "pc105"
#  Option "XkbLayout" "de"
#EndSection
```

I uncommented it again and inserted     
Option         "AutoRepeat"    "250 5"  

Earlier, I had found a file called /etc/kbd/config and uncommented
KEYBOARD_RATE="30"
KEYBOARD_DELAY="250"

And then I played with the kbdrate command:
```
[~]$ sudo kbdrate -r 10 -d 250









Typematic Rate set to 10.0 cps (delay = 250 ms)
```

But none of that seemed to have any effect whatsoever. 

So... where do people configure keyboards these days?


PS: I also used to have my own keyboard layout. The German layout is rather painful if you use many curly/square braces. How does it even know that it's supposed to use a German layout? It sure isn't due to xorg.conf.

---

### Post by m_2009 on 2009-04-23
You can set the keyboard rate from within the terminal window using a the kbdrate command. eg:
 
```
sudo kbdrate -d 500 -r 20
```
 
Or whichever values you want to use use which you are happy with, then test the keyboard rate in any text window or gedit etc to see if the delay is somethin you are happy with.
 
When you have found a value that you like, you need to edit the following file.
 
/etc/rc.local 
You wil need route acess so use the following depending if you use ubuntu or kubuntu. 
 
Ubuntu
```
gksudo gedit /etc/rc.local
```
 
Kubuntu
```
kdesudo kate /etc/rc.local
```
 
When the file loads you should see something similar to this.
 
```
 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
exit 0

```
 
Add the following line substituting the values that you were happy with when you used the kbdrate command in the terminal window. The file should now look like this.
 
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
kbdrate -d 500 -r 20
exit 0

```
 
This will cause the keyboard rate to be set everytime ubuntu starts up.

---

### Post by mrowth on 2009-04-23
...

---

### Post by mrowth on 2009-04-23
I had already tried kbdrate in vain. Still put it in rc.local, went to run level 1, then 2 again. Still no effect. To verify I'm not imagining things, I also tried the two characters per second/one second delay in a terminal window... that didn't change a thing, either. Everything's fine "outside" X (tty1 etc.), so I don't think it's my hardware or BIOS setup. It's just X and just since the Intrepid->Jaunty upgrade. I even let nvidia-xconfig write me a whole new xorg.conf.

Thanks, though. 

Hope there's an answer... out there.

---

### Post by m_2009 on 2009-04-23
I know in ubuntu if you go to SYSYEM > PREFERENCES > KEYBOARD there is a slider which you can adjust for the keyboard delay rate etc.. Does kubuntu have anything similar?
 
Also in your first post you mentioned that you commented out various lines in files, did you try changing the values of them lines also to see if that changed anything?

---

### Post by mrowth on 2009-04-23
> **m_2009 said:**
> I know in ubuntu if you go to SYSYEM > PREFERENCES > KEYBOARD there is a slider which you can adjust for the keyboard delay rate etc.. Does kubuntu have anything similar?
Apparently, some distributions of KDE 4 do. My Kubuntu lacks that control panel, and so does some version of Mandriva it seems. (I don't know if it's there for people who did a fresh install; I've been upgrading in place from Heron.) 

All I can find is a whole bunch of Accessibility options (I had initially hoped they were responsible for the slowness).

> Also in your first post you mentioned that you commented out various lines in files, did you try changing the values of them lines also to see if that changed anything?
I didn't comment out anything; the xorg.conf lines were commented out during the upgrade to either Intrepid or Jaunty (I only upgraded to Intrepid this month), and the /etc/kbd/config stuff was commented out by default. I **un**commented them to see if they'd change anything, which they didn't...

PS: Yes, I did change the values, too, to something absurdly slow so I'd notice...

PPS: /etc/kbd/config and kbdrate actually work - but at the console, not in X!

---

### Post by mrowth on 2009-04-24
Bump?

---

### Post by mehturt on 2009-04-28
I'm seeing this problem as well..
When running KDE, there is not problem to change this rate & delay to whatever I like, via systemsettings.
However, when not running KDE, I can't start systemsettings:

<unknown program name>(8881)/: KUniqueApplication: Cannot find the D-Bus session server

<unknown program name>(8880)/: KUniqueApplication: Pipe closed unexpectedly.


The kbdrate gives me:
Typematic Rate set to 10,9 cps (delay = 250 ms)

I'd like to change the delay to something smaller than 250, but according to man page, this is not possible.. But I'm sure this was possible via systemsettings :(

---

### Post by mrowth on 2009-04-28
> **mehturt said:**
> I'm seeing this problem as well..
When running KDE, there is not problem to change this rate & delay to whatever I like, via systemsettings.
However, when not running KDE, I can't start systemsettings:

<unknown program name>(8881)/: KUniqueApplication: Cannot find the D-Bus session server

<unknown program name>(8880)/: KUniqueApplication: Pipe closed unexpectedly.


The kbdrate gives me:
Typematic Rate set to 10,9 cps (delay = 250 ms)

I'd like to change the delay to something smaller than 250, but according to man page, this is not possible.. But I'm sure this was possible via systemsettings :(
I don't think I even have that option in System Settings! It seems something's missing (or I haven't found it).

250 ms would be fine. It's fine in the console. But what I get in X is longer...

---

### Post by sgiessl on 2009-05-02
mrowth, I experienced the same problem as you did on my thinkpad T41 after an upgrade to jaunty: annoyingly slow keyboard repeat delay; kbdrate only having an effect outside of X; no config option found in KDE4 system settings.

The only thing that works for me is using xset (which even allows a repeat delay below 250ms):
> xset r rate 150 50

I didn't yet find out about the proper way to make this setting permanent for each X restart, though.

---

### Post by raptor386 on 2009-05-05
I'm having the same problem in Gnome as well. The key repeat delay seems to be twice as long as it should be. I've tried changing it in gnome's control panel, but after a reboot it reverts back to it's original setting. There doesn't seem to be a way to make it 'stick'. I can reproduce this behavior in both a clean install, and an upgraded install from intrepid.

---

### Post by mrowth on 2009-05-10
> **sgiessl said:**
> mrowth, I experienced the same problem as you did on my thinkpad T41 after an upgrade to jaunty: annoyingly slow keyboard repeat delay; kbdrate only having an effect outside of X; no config option found in KDE4 system settings.

The only thing that works for me is using xset (which even allows a repeat delay below 250ms):


I didn't yet find out about the proper way to make this setting permanent for each X restart, though.

I no longer have this problem in KDE. I suspect the update to KDE 4.2.3 did it. It seems to have added a "Keyboard" section to the "Keyboard & Mouse" System Settings module, with delay/rate sliders.

(But "X in general" isn't affected by this. It's just KDE.)

---

### Post by coverup1128 on 2009-07-09
> **raptor386 said:**
> I'm having the same problem in Gnome as well. The key repeat delay seems to be twice as long as it should be. I've tried changing it in gnome's control panel, but after a reboot it reverts back to it's original setting. There doesn't seem to be a way to make it 'stick'. I can reproduce this behavior in both a clean install, and an upgraded install from intrepid.
I have the same problem in Gnome. Can't make the keyboard delay and repeat rate stick.

---

### Post by triclops200 on 2012-07-20
I know this is a necro post, but in case anyone stumbles upon this looking for a solution, add
```
xset r rate 500 30
``` or whatever settings you want, into '~/.xinitrc', that worked for me.
However, if that does not work, put it in /etc/X11/xinit/xinitrc ```
 echo "xset r rate 500 30" | sudo tee -a  /etc/X11/xinit/xinitrc 
```

---

