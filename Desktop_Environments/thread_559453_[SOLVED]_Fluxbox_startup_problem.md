---
title: "[SOLVED] Fluxbox startup problem"
date: 2007-09-25
forum: Desktop Environments
---

### Post by ghandi69_ on 2007-09-25
Hey guys,

I'm trying to make a system where upon startup, it goes straight to the terminal, and to get into my desktop I just type 'startx'.

I have installed x-window-system-core , fluxbox, and thunar to the base server system.

When I just type in startx, fluxbox will startup, but it will not run the startup script located in .fluxbox/.

If afterwards, I type in startfluxbox, it will then run the script and all the things I would like to happen in the startup folder actually do happen.

I checked out my xinitrc file in etc/X11/xinit, and it just runs Xsessions.  If I put a & afterthat, and then run startfluxbox, it starts to run the startup file but then cancels out saying that it cannot find an xscreen to use, and that there is already a window manager open.

I know this is not the best explantation, but does anyone have any ideas?

---

### Post by kerry_s on 2007-09-25
if your using startx it's better to use .xsession or .xinit to start stuff
i usually use xinit

xedit ~/.xinit
put

~/.fluxbox/startup &

then you could still use the regular file

here's my script to auto start x when you log in

xedit ~/.bash_profile
put
```
if [ `tty` = "/dev/tty1" ]; then
startx
fi

```
on the bottom

---

### Post by RedSquirrel on 2007-09-25
> **ghandi69_ said:**
> Hey guys,

I'm trying to make a system where upon startup, it goes straight to the terminal, and to get into my desktop I just type 'startx'.

I know this is not the best explantation, but does anyone have any ideas?

I use ~/.xinitrc:

```
#!/bin/sh

userresources=$HOME/.Xresources
userdefaults=$HOME/.Xdefaults
usermodmap=$HOME/.Xmodmap

# merge in defaults and keymaps

if [ -f $userresources ]; then
    xrdb -merge $userresources
fi

if [ -f $userdefaults ]; then
    xrdb -merge $userdefaults
fi

if [ -f $usermodmap ]; then
    xmodmap $usermodmap
fi

# this is needed to make OpenOffice take the gtk theme
# we specify in ~/.gtkrc-2.0
export OOO_FORCE_DESKTOP=gnome

# start some nice programs
numlockx on

# start the window manager
exec startfluxbox
```I also make it executable:

```
chmod  +x ~/.xinitrc
```"startfluxbox" is the script you want to run when you start Fluxbox. It will create the ~/.fluxbox directory tree (if it did not already exist) and run ~/.fluxbox/startup. 

"startfluxbox" is what the Fluxbox devs expect you to use.

I also use an alias for startx so that it will create a log:
```
alias startx='startx -- -br > $HOME/.startx-log 2>&1'
```The '-br' just makes the screen black instead of that crossweave pattern you see before Fluxbox starts.

---

### Post by kerry_s on 2007-09-25
lol, i was half a sleep on that 1. :)

---

### Post by RedSquirrel on 2007-09-25
> **kerry_s said:**
> lol, i was half a sleep on that 1. :)
No worries. I like your little trick to run startx automatically. I won't need it myself because I often make little changes to things on the console before I run startx. However, I'll tuck it away just in case. :)

---

### Post by kerry_s on 2007-09-25
> **RedSquirrel said:**
> No worries. I like your little trick to run startx automatically. I won't need it myself because I often make little changes to things on the console before I run startx. However, I'll tuck it away just in case. :)

thanks RedSquirrel, see what happens when i don't use fluxbox, i forget what the files are called. i been using xfce4 and it's gui start app for my startup programs.

hey did you see the script for killing zombie process's you might want to tuck that away to, that way i can just ask you if i lose it, took me forever to find 1 that works.

```

#!/bin/sh
 kill -HUP `ps -A -ostat,ppid,pid,cmd | grep -e '^[Zz]' | awk '{print $2}'` 


```

i put it in /etc/cron.hourly

i still had that mousepad zombie problem, some times it zombies and sometimes it doesn't, but i leave my computer on most of the time and they start to add up, 1 time i looked and there was 30 of them, so i figured i better fix that. :lolflag:

take care.

---

### Post by RedSquirrel on 2007-09-25
Thanks for the zombie killer. I don't know if I have that many zombie processes, but I'll have a look.

Funny, even when I used Xubuntu I switched to leafpad right away because the Save As dialog for mousepad wouldn't allow me to type in a file name and then just press Enter; I had to click the Save button. Pain in the neck. :mad:

---

### Post by ghandi69_ on 2007-09-25
Hey Kerry and Squirrel, thanks for the help.

Squirrel, would you mind running through your little script there and let me know what it is going on?  It works like a charm, but, I just do not know why.

Thanks,
Ghandi

---

### Post by RedSquirrel on 2007-09-26
> **ghandi69_ said:**
> Squirrel, would you mind running through your little script there and let me know what it is going on? It works like a charm, but, I just do not know why.

Have a look at the man pages for startx and bash

```
man startx
man bash
```The guides at [http://tldp.org](http://tldp.org) are pretty good too.

When you run startx, it checks to see if you have the file ~/.xinitrc. If you do have that file, startx runs it.

```
userresources=$HOME/.Xresources
userdefaults=$HOME/.Xdefaults
usermodmap=$HOME/.Xmodmap

```These lines just define some variables for use later in the script. The variables are assigned the locations of some standard configuration files.

```
# merge in defaults and keymaps

if [ -f $userresources ]; then
    xrdb -merge $userresources
fi

if [ -f $userdefaults ]; then
    xrdb -merge $userdefaults
fi

if [ -f $usermodmap ]; then
    xmodmap $usermodmap
fi
```These if statements test to see if you have the configuration files listed and will apply them if they exist.


```
# this is needed to make OpenOffice take the gtk theme
# we specify in ~/.gtkrc-2.0
export OOO_FORCE_DESKTOP=gnome

```When I have used OpenOffice, I have found that it won't use the GTK theme (Clearlooks, IndustrialTango, etc.) I choose unless I set that environment variable. All of my other programs pick up the theme automatically, but OpenOffice doesn't without that variable set.


```
# start some nice programs
numlockx on

```'numlockx' just activates the NUMLOCK key on my keyboard so I don't have to do it myself. It's in the repositories:

```
sudo apt-get install numlockx
```

```
# start the window manager
exec startfluxbox

```Without getting too technical, this runs the script 'startfluxbox'. The idea is that when you exit Fluxbox (for example, from the menu), X shuts down too and you're back at the console. 

I hope that helps. :)

---

### Post by ghandi69_ on 2007-09-26
Thanks squirrel,

However, I just realized something...

I copied that information you gave me into my /etc/X11/xinit/xinitrc file, not the one in my home directory.

It works fine the way it is, but are there any possible complications doing it this way?

---

### Post by RedSquirrel on 2007-09-26
It would probably be OK, but I would be inclined to use ~/.xinitrc just to be on the safe side. It's also easier to make changes to ~/.xinitrc because you don't need sudo.

EDIT: If you decide to use the file in your home directory, make sure you put a dot "." in front of "xinitrc", like this [COLOR=Magenta].[/COLOR]xinitrc. ;)

---

### Post by kerry_s on 2007-09-26
> **ghandi69_ said:**
> Thanks squirrel,

However, I just realized something...

I copied that information you gave me into my /etc/X11/xinit/xinitrc file, not the one in my home directory.

It works fine the way it is, but are there any possible complications doing it this way?

if xinit gets updated you get boned, you'll have to do it all over again.

---

### Post by ghandi69_ on 2007-09-27
Ok guys... I'm going to create a .xinitrc file in my home directory, one question..

What do I put back in the original /etc/X11/xint/xinitrc file, and how will it know to reference the new file?

---

### Post by RedSquirrel on 2007-09-27
> **ghandi69_ said:**
> Ok guys... I'm going to create a .xinitrc file in my home directory, one question..

What do I put back in the original /etc/X11/xint/xinitrc file, and how will it know to reference the new file?

Here's my stock /etc/X11/xinit/xinitrc file:

```
#!/bin/sh
# $Xorg: xinitrc.cpp,v 1.3 2000/08/17 19:54:30 cpqbld Exp $

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
. /etc/X11/Xsession

```

startx will look for ~/.xinitrc and run it if it exists.

---

### Post by RedSquirrel on 2007-09-27
> **kerry_s said:**
> if xinit gets updated you get boned, you'll have to do it all over again.

It will just overwrite that file? Well, that's :evil:.

---

