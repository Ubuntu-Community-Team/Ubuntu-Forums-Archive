---
title: "Where are the keyboard layots?"
date: 2005-04-05
forum: Desktop Environments
---

### Post by Eproxus on 2005-04-05
Hi,

I'm currently running Ubuntu with a swedish dvorak keyboard. Unfortunately it is not the same layout as the swedish dvorak layout found in Ubuntu (or Gnome, I don't really know). Thus, I want to modify the swedish layout to fit my keyboard (and the layout I'm familiar with) and I've looked around a bit in the system to find where layouts are stored but I only seem to find the english dvorak files. Where are the swedish files stored?

Thanks in advance!
//Adam

---

### Post by penguinwarrior on 2005-04-05
not sure if or how this might help, but i'll dive in...
...hmm...
under /usr/share/keymaps/i386/qwerty/ 
there is alot of keymaps.  would swedish be  se-fi-**.keymap.gz? (swedish-finnish??)

under my /etc/X11/XF86Config-4, my
Selection "Inputdevice" has Option "Xkblayout" "defkeymap"
would yours be Option "Xkblayout" "se-fi-**" ??

I know, thanks for no help... oh well, have to look a bit harder i guess... sorry.

the only thing i can think of is doing an xf86config and re-defining your keyboard that way.

again, sorry. 8-[

---

### Post by Eproxus on 2005-04-06
[QUOTE=penguinwarrior]under /usr/share/keymaps/i386/qwerty/ 
there is alot of keymaps.  would swedish be  se-fi-**.keymap.gz? (swedish-finnish??) [/QUOTE]
Well, those are only qwerty layouts, and in /usr/share/keymaps/dvorak/ there is no swedish keyboard layout.
 [QUOTE=penguinwarrior]under my /etc/X11/XF86Config-4, my
Selection "Inputdevice" has Option "Xkblayout" "defkeymap"
would yours be Option "Xkblayout" "se-fi-**" ??[/QUOTE]
I use Hoary and therefore the X.org X server and in xorg.conf (in the same directory) I only have:
 ```
Section "InputDevice"
		Identifier	  "Generic Keyboard"
		Driver		  "keyboard"
		Option		  "CoreKeyboard"
	    Option		  "XkbRules"	  "xorg"
	    Option		  "XkbModel"	  "pc105"
	    Option		  "XkbLayout"	 "dvorak"
EndSection
``` 
So my question is, where is that map or, preferably, the Gnome swedish dvorak keymap?

---

### Post by sinaen on 2005-10-10
the one thing you need to do is to do/make your swedish dvorak file  and then you need to get that into the folder, i didnt read what directory you said, but then anyway you get to rename the old one and replace it with the new one problem solved aint it?


[http://www.mwbrooks.com/dvorak/](http://www.mwbrooks.com/dvorak/)

---

### Post by sinaen on 2005-10-10
[http://users.one.se/liket/svorak/](http://users.one.se/liket/svorak/)


check out this, this one has instructions on how to install, and its a pretty good layout to write in also much nicer than the default

---

