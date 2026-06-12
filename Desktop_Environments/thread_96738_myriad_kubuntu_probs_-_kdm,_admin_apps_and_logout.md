---
title: "myriad kubuntu probs - kdm, admin apps and logout"
date: 2005-11-29
forum: Desktop Environments
---

### Post by qaqa on 2005-11-29
I installed kubuntu-desktop on breezy.

1) In KDE, I only get the logout option and DO NOT get the shutdown,restart and hibernate options which I get in gnome. I'm forced to logout first, and then shutdown through GDM. 

2)I'm using GDM right now..how do I change it to KDM?

3) None of the admin tools are working under KDE. When I click on "administrator mode", I just get the same blank screen with all the options grayed out!

4) How do I access the gnome admin tools under KDE?

I'd me mighty thankful if any of you can help me with this!

---

### Post by ace2005 on 2005-11-29
1. It only works if you use KDM

2. Run "$ sudo dpkg-reconfigure kdm"

3. Must be something to do with sudo, edit the sudoers file located here: "/etc/sudoers" and add

> qaqa      ALL = NOPASSWD: ALL

or whatever you're username on that computer is

4. No idea, never used gnome

---

### Post by qaqa on 2005-11-30
[QUOTE=ace2005]1. It only works if you use KDM

2. Run "$ sudo dpkg-reconfigure kdm"

3. Must be something to do with sudo, edit the sudoers file located here: "/etc/sudoers" and add



or whatever you're username on that computer is

4. No idea, never used gnome[/QUOTE]

I followed your instructions and enabled kdm! Thanks! I now have the shutdown and restart options. However, I still dont have the "hibernate" option which I get in gnome...Is there any way I can add it to the menu?


I'm still not able to start any KDE admin apps..KDE su pops up, asks for my password, accepts it, but the admin-level options in the app still remain grayed out! 

I checked my sudoers file - it's properly configured.I dont have any problems running the gnome admin apps..Synaptic et al run quite well even under KDE. It is only the KDE admin apps under "system settings" that misbehave..what could be the problem?

---

### Post by ace2005 on 2005-11-30
Not sure but "sudo kcontrol" will make them work, just make sure not to install something like an icon theme, because then the icon theme will be extracted to *your* home directory with *root* access only, so you have to go there in "sudo konqueror" and sort it out again, but other than that it should work fine

Well here's what my sudoers file looks like:

> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin	ALL=(ALL) ALL

ace           ALL = NOPASSWD: ALL


---

