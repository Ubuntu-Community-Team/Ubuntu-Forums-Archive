---
title: "Need a howto on switching from gnome to icewm."
date: 2009-09-16
forum: Desktop Environments
---

### Post by dvdljns on 2009-09-16
I have been trying to upgrade from 5.10 and need to change gnome. I have 6.06 LTS on now but I want to put on icewm before going up to 8.04. I downloaded icewm and installed it but can not change from gnome to icewm. I would also like to replace nautilas with something else but do not know what.

---

### Post by Ibidem on 2009-12-29
I (vaguely) remember doing that...~2 years ago.
Option 1: Upgrading
1. (installing): 
install IceWM and some basic things:
(In terminal)
sudo apt-get install icewm
#(accept the dependencies)
sudo apt-get install menu
sudo apt-get install grun
sudo apt-get install rox-filer

(OR)
in Synaptic:
select icewm, menu, grun, & rox-filer
apply

2.  (switching)
You MUST logout, 
then select session type icewm-session,
then login
If it complains "You have selected session type Icewm, but default session type is "default""
or some such thing, click OK.

You should be in IceWM now.

Select the "start" button or right click, goto Programs>Applications>System>Administration>Synaptic

OR click the "terminal" icon & run "sudo synaptic" 
If you _want_ to remove Gnome & a lot more, remove package ubuntu_desktop and the dependencies

To get desktop icons back, run 
grun nautilus 
(runs GNOME file manager, extremely slow)

"grun rox" runs rox-filer

Now update/do what you want.


Option 2: Migrating
Install 8.04 from CD, selecting to migrate accounts & data.
Install IceWM first thing, as described above.
Logout, switch session type, login

Replace Rox-filer with PCmanFM
Open PCmanFM, go to
Edit>Preferences (at bottom)
Desktop
Select "Manage Desktop"

And that is it.
I hope this helps.

---

### Post by yoi on 2010-01-21
I have written an article on a simple way to enable IceWm without relying on Ubuntu's default gdm login manager.  This method should be valid for a broad range of releases of Ubuntu or any other Unix-like systems.

[http://mostlyunix.com/?q=node/16](http://mostlyunix.com/?q=node/16)

---

