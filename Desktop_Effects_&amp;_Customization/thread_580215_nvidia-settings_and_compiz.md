---
title: "nvidia-settings and compiz"
date: 2007-10-18
forum: Desktop Effects &amp; Customization
---

### Post by fart_flower on 2007-10-18
I'm trying to get my nvidia-settings to load at start up so I can have anti-aliasing enabled with Compiz Fusion.  Ye olde method was to insert the command "nividia-settings --load-config-only" into System > Preferences > Sessions.  However, in Gutsy Gibbon, this rarely works properly.

I suspect the problem is compiz fusion normally loads before nvidia-settings, but for whatever reason, sometimes nvidia-settings loads first.  Only then do I finally get my beloved anti-aliasing.

Is their some way to fix this?  My current "work around" is to press Ctrl+Alt+Backspace a few times until the anti-aliasing magically appears.  A pretty poor methodology, to be sure.

---

### Post by psybreeze on 2007-10-20
Hi!

I just started using Ubuntu and Linux with Gutsy, so we can say I'm an official noob in the field. [COLOR="Red"]But![/COLOR] 

I will give a noob-friendly tutorial:

I have found a quick and easy solution, although old veterans of the Ubuntu and Linux community might find this harsh and brutal. Beginner's luck! :)

(if anyone has a better solution, please post!!!!)

Ok, so there is a script, which is called by gnome-wm. (That is  the program, which starts your preferred window manager.)

The script is in "/usr/bin/" and it is simply called "compiz".

To be able to save the file, you need admin rights, so to start editing, type this in a terminal:

sudo gedit '/usr/bin/compiz'

This script checks, how it should start compiz, and there is a line near the end, which looks like this:

####################
# Execution begins here.

BEFORE this part, just simply add the line: 

nvidia-settings -l

(if you want to change the nvidia settings, or haven't set them yet, simply enter "nvidia-settings" without the quotes into a terminal, and the nvidia settings window will appear, make the changes you want there)

That is all, now if you log in, you should have all the settings that you set in nvidia-settings loaded up, before compiz.

Have fun!

---

### Post by c.dric on 2007-10-23
Thanks for the tip psybreeze.

i applied your fix and it seemed to work for a day or two ... but it doesn't anymore :(

everytime the screen fades out, my nvidia-settings are reset and i have to run 'nvidia-settings -l' manually to get my settings back.

in Feisty all i had to do was to add 'nvidia-settings -l' to the start-up programs but that doesn't help anymore either ...

anymore ideas ?

---

### Post by c.dric on 2007-10-24
bump

---

### Post by chriss_crooze on 2007-10-27
if you update compitz, this entry may be errazed i think. so maybe you add this entry to the "/usr/share/xsessions/gnome.desktop" file. ofcourse its only working in gnome then.  
 sudo gedit /usr/share/xsessions/gnome.desktop
now change line "Exec=/usr/bin/gnome-session" to "Exec=nvidia-settings -l && /usr/bin/gnome-session"

---

