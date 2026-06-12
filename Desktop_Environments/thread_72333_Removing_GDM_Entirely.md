---
title: "Removing GDM Entirely"
date: 2005-10-05
forum: Desktop Environments
---

### Post by duminas on 2005-10-05
Two parts to this question.
First and foremost, how do I remove **gdm** and stop it from acting as my login shell (to where the terminal will be my login shell)? I would like it this way in case my video ever wonks out so I don't get horribly out of luck with that install (debugging X).

[size=1]I realize I can **aptitude remove gdm**, but I want to avoid that for the time being in case Fluxbox freaks out or doesn't work right.[/size]

That being said, once GDM is removed, how do I go about making the X server pop Fluxbox when I issue *startx*? At present, it runs **gdm**, and I've got a feeling the _/etc/X11/default-display-manager_ file has something to do with this. However, when I changed this file (to */usr/local/bin/startfluxbox* instead of */usr/bin/gdm*, which is default), the X server wouldn't start, possibly since GDM was still around (it said it could not start due to GDM not being the default).

Any help would be appreciated.
Thanks.

---

### Post by asterix404 on 2005-10-06
Okay, well... you commented on mine so I am going to try to get yours assuming that gentoo and ubuntu and unix are not totally horrably different things and don't hate me if this doesn't work. You should have a file called /etc/rc.conf. If this is not documented then umm... well.. here:

> # /etc/rc.conf: Global startup script configuration settings
# $Header: /home/cvsroot/gentoo-src/rc-scripts/etc/rc.conf,v 1.22 2003/10/21 06:09:42 vapier Exp $

# Use KEYMAP to specify the default console keymap.  There is a complete tree
# of keymaps in /usr/share/keymaps to choose from.  This setting is used by the
# /etc/init.d/keymaps script.

KEYMAP="us"

# Should we first load the 'windowkeys' console keymap?  Most x86 users will
# say "yes" here.  Note that non-x86 users should leave it as "no".

SET_WINDOWKEYS="yes"

# The maps to load for extended keyboards.  Most users will leave this as is.

EXTENDED_KEYMAPS=
#EXTENDED_KEYMAPS="backspace keypad"

# CONSOLEFONT specifies the default font that you'd like Linux to use on the
# console.  You can find a good selection of fonts in /usr/share/consolefonts;
# you shouldn't specify the trailing ".psf.gz", just the font name below.
# To use the default console font, comment out the CONSOLEFONT setting below.
# This setting is used by the /etc/init.d/consolefont script (NOTE: if you do
# not want to use it, run "rc-update del consolefont" as root).

CONSOLEFONT="default8x16"

# CONSOLETRANSALTION is the charset map file to use.  Leave commented to use
# the default one.  Have a look in /usr/share/consoletrans for a selection of
# map files you can use.

#CONSOLETRANSLATION="8859-1_to_uni"

# Set CLOCK to "UTC" if your system clock is set to UTC (also known as
# Greenwich Mean Time).  If your clock is set to the local time, then set CLOCK
# to "local".  This setting is used by the /etc/init.d/clock script.

CLOCK="local"

# Set EDITOR to your preferred editor.

EDITOR="/bin/nano"
#EDITOR="/usr/bin/vim"
#EDITOR="/usr/bin/emacs"

# Set PROTOCOLS to the protocols that you plan to use.  Gentoo Linux will only
# enable module auto-loading for these protocols, eliminating annoying module
# not found errors.
#
# NOTE: Do NOT uncomment the next lines, but add them to 'PROTOCOLS=...' line!!
#
# Num   Protocol
# 1:    Unix
# 2:    IPv4
# 3:    Amateur Radio AX.25
# 4:    IPX
# 5:    DDP / appletalk
# 6:    Amateur Radio NET/ROM
# 9:    X.25
# 10:   IPv6
# 11:   ROSE / Amateur Radio X.25 PLP
# 19:   Acorn Econet

# Most users want this:
PROTOCOLS="1 2"

#For IPv6 support:
#PROTOCOLS="1 2 10"

# What display manager do you use ?  [ xdm | gdm | kdm | entrance ]
DISPLAYMANAGER="gdm"

# XSESSION is a new variable to control what window manager to start
# default with X if run with xdm, startx or xinit.  The default behavior
# is to look in /etc/X11/Sessions/ and run the script in matching the
# value that XSESSION is set to.  The support scripts is smart enouth to
# look in all bin directories if it cant find a match in /etc/X11/Sessions/,
# so setting it to "enligtenment" can also work.  This is basically used
# as a way for the system admin to configure a default system wide WM,
# allthough it will work if the user export XSESSION in his .bash_profile, etc.
#
# NOTE:  1) this behaviour is overridden when a ~/.xinitrc exists, and startx
#           is called.
#        2) even if a ~/.xsession exist, if XSESSION can be resolved, it will
#           be executed rather than ~/.xsession, else KDM breaks ...
#
# Defaults depending on what you install currently include:
#
# Gnome - will start gnome-session
# kde-<version> - will start startkde (ex: kde-3.0.2)
# Xsession - will start a terminal and a few other nice apps

XSESSION="fluxbox"


This is what you must change to get gdm to not be your login manager. From here though you should also do

> rc-update del xdm default

as this will remove the xdm command from starting up a windows manager. I like gdm btw, it's a good login manager and very easy to use. Is there any reason why you don't want to use it?

---

### Post by duminas on 2005-10-06
Sadly, it is not that easy in Ubuntu. We lack the awesome **rc.conf** file for setting things like that. We also totally lack **rc-update**.

Also, I thought there'd be an Xsession variable somewhere in Ubuntu, but... I'm having absolutely no luck finding one. The closest I can come is the file I reference in my first post, but even then, that just stops X from loading if I change it.

There's a couple reasons I don't want to use GDM.
1) I strongly dislike graphical login clients of any kind, and avoid them as much as I can.
2) In case of video breakage or if I just need to be in the terminal--If I only need the terminal, why load X and GDM?

---

### Post by zAo on 2005-10-06
Why not set the default init-level to 2 (I guess; on AIX right now, so :) )

---

### Post by duminas on 2005-10-06
No idea how to do that?
I also want GDM *gone*.

Well, doing some testing:
If I:
- **init 2**,
- Change the **default-display-manager** file to reflect /usr/local/bin/fluxbox (not /usr/bin/gdm)

X starts, buuuuuuuuuuuut Gnome instantly pops up (even though the GDM login process is skipped). Additionally, my desktop background is really, really weird, and I lose ALL my settings (seems like it logs in directly as root, even though I am, at the time, running as my normal user).

So... yeah.
Weird, and I'm lost, here.

If someone could provide a *definitive* way to get this done, or some docs outlying a *definitive* (again) way to get it done on Ubuntu, it'd be helpful, since I do NOT want to be running everything as root (among other concerns, that one is just the most pressing).

---

### Post by Buffalo Soldier on 2005-10-06
[quote=duminas]I also want GDM *gone*.[/quote]Why not just uninstall GDM then? **sudo apt-get remove gdm**

---

### Post by duminas on 2005-10-06
At this time, without it, I'd be logging in to Fluxbox as root, which is really, really bad. I need to figure a way around that little nuisance. Also, I'd like to prove to myself that I can run Fluxbox on its own before I remove GDM fully. Do you know of the old phrase about burning bridges? That is what I am applying, here.

If I lose all my WM's functionality, it's over for this install.

---

### Post by Hairy_Palms on 2005-10-06
surely if it doesnt work you can just apt-get install and put gdm back?

---

### Post by duminas on 2005-10-06
Yeah, it can, but that's sidestepping the point.
I want to figure out **why** I can't get Fluxbox working on its own when GDM coexists.

Hence, I shant uninstall GDM until I can prove Fluxbox can run on its own. I want to figure out the internals, here, not just let apt handle things *I should know about*. That's kinda defeating the point of one being able to configure things on one's own.

---

### Post by vruum on 2005-10-06
I'm not on ubuntu right now, so some things might differ, but as for starting flubox when executing starx (not as root), something in your ~/.xinitrc or ~/.xsession (both in your home directory,), might be interfering(they should say something along the lines of "exec fluxbox/exec startfluxbox (i don't know if startfluxbox is specific to arch, if it isn't you should execute that instead of just fluxbox)  If you want to log in via the terminal, you should look at the file /etc/inittab, and change the  default runlevel (the file is probably rather well commented) 
I dunno if any of this helps, but it's what I would do anyway, good luck

---

### Post by duminas on 2005-10-06
Well, the .xsession file in my home directory didn't even exist.

- So first, I ran a *locate xinitrc*, and then nano'd the result (/etc/X11/xinit/xinitrc, I think it was).
- Next, I scanned that file, and it turns out it points to /etc/X11/Xsession. More hopping I go, and in that file, I see it wanting [home path]/.xsession.
- Created that file and threw in **exec startfluxbox**.
- Changed the default-display-manager file to reflect **/usr/local/bin/fluxbox**.

And now it works, my fonts are just a tad ugly, but that might be more theme-related. Byebye, GDM~

---

