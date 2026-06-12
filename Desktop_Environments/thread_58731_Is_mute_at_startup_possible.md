---
title: "Is mute at startup possible?"
date: 2005-08-21
forum: Desktop Environments
---

### Post by pizzach on 2005-08-21
I know you can at least do something like this with Apple laptops.  If you hold the mute button while turning them on, they don't do the startup chime and maybe mute for the whole setup.

Now while I like the login screen sound effects and such of Hoary, I really don't want to be another one of those idiots in the library who have their computers constantly making noises.  

So in the end, I'm asking for at least way to get the login screen to to not do it's sound effect and no log in sound.  It would be prefferable to mute the whole system though.  Is this possible?

---

### Post by arnieboy on 2005-08-21
[QUOTE=pizzach]I know you can at least do something like this with Apple laptops.  If you hold the mute button while turning them on, they don't do the startup chime and maybe mute for the whole setup.

Now while I like the login screen sound effects and such of Hoary, I really don't want to be another one of those idiots in the library who have their computers constantly making noises.  

So in the end, I'm asking for at least way to get the login screen to to not do it's sound effect and no log in sound.  It would be prefferable to mute the whole system though.  Is this possible?[/QUOTE]
Go to System-->Preferences--> Sound and **uncheck** "sound for events" and "enable sound serveratstartup". Now go to sound and video-->volume control and mute all. save and logout.

---

### Post by jorgealfonso on 2007-03-14
This line on a terminal seems to work:

[INDENT][COLOR="Navy"]amixer set 'Master' mute
[/COLOR][/INDENT]

Now I have to figure out how to put it on the startup script (I am a complete newbie, just installed the whole thing ;))

I'm trying adding it here:
System -> Preferences -> Sessions -> Startup programs tab

...and will further read about the possibility to edit rc.local and rc.boot files ;)

---

### Post by ComplexNumber on 2007-03-14
or you could just switch the volume applet on your panel right down.

---

### Post by jorgealfonso on 2007-03-15
> or you could just switch the volume applet on your panel right down.

Right, but many people forget to mute the volume before turning the computer off (at least I do....). So, when you turn your computer back on, you could be ashamed with the startup sounds if you are in a quiet place, specially if the volume was loud on your last session.

If the sound is muted at startup, of course, you will have the choice to turn it on whenever you want (but in this case, the choice is yours).

By the way, the solution in my last post seems to be working fine :)

---

### Post by jorgealfonso on 2007-05-13
One final detail; go to...

[INDENT]System -> Preferences -> Audio -> Sounds tab
[/INDENT]
... and change the "login" sound, to "no sound" (otherwise, this audio could play before the Mute command described above makes its :-# job)

---

### Post by _ja_bob_ on 2008-05-16
I just found out how to do this with my laptop, but it should work just fine for probably any computer. 

First, you have to know if your mixer has any weird settings. For my laptop, audio output is actually run on three different mixers, one for headphones, one for the speakers, and another for the 'subwoofer.' This is the procedure I used to mute them on startup

-----------------------------------------------------
*open up a terminal and go to the directory where the script will be put:

cd /etc/init.d

*now you need to make the script itself... I use gnome and therefore
*Gedit, but you can use vi or whatever you're comfortable with

sudo gedit mute.sh

*When the editor opens up, type this out and then save it
*just remember that you need to add a line for every mixer 
*that you need muted and ones that are multiple words need ""
*most people can probably get away with just the "Master" channel

#!/bin/sh
amixer -q sset Master mute
amixer -q sset Headphone mute
amixer -q sset "Master Mono" mute

*Save the file and exit Gedit and make the script executable by typing

sudo chmod +x mute.sh

*Now to put it in the major startup catagories

sudo update-rc.d mute.sh defaults
-----------------------------------------------------

It worked for me and I hope it works for you. I am a beginner too, so no promises.

---

