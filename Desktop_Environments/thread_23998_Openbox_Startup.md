---
title: "Openbox Startup"
date: 2005-04-05
forum: Desktop Environments
---

### Post by Equanimity on 2005-04-05
I am using Openbox as my Desktop Environment, because of it's speed, menu pipes and, well, I just like it. With this, I run feh (to set my desktop background), torsmo and a few desklets. For the moment, I have to open a terminal myself to run them. Openbox doesn't feature a session manager, so what would be the best way of having them start automatically?

I recently converted from Gentoo Linux, where these things were automatically executed with an ~/.xsession file. Very happy with Ubuntu thus far :)

---

### Post by maddox on 2005-04-05
Openbox is running smoothy here.

if you use KDM or GDM just edit/create ~/.xsession (and run your session type as "default" in kdm/gdm menu, if you choose "openbox" instead of "default" i think it doesnt look for your ~./.xsession)
  
if u run "startx" edit ~./.xinitrc

for the apps like torsmo etc, you have to run them with & at the end before "exec openbox".... here goes a copy of my ~./.xsession 

---------- CUT HERE -----

# X WINDOW SYSTEM STARTUP SCRIPT
#

# The following X clients are started up
# as part of the initial window system
# environment. Users can change or add
# to these default clients in order to
# set up a custom environment. All
# clients started up in this script
# should be run in the background,
# except for the window manager, which
# should be last.

# epist is the recommended way to bind keys
# to actions in Openbox.
#epist &

# gkrellm is a system monitoring tool.
# -w puts it in the "Slit".
gkrellm -w &

# bbpager is a pager which uses blackbox
# themes to decorate itself.
# -w puts it in the "Slit".
#bbpager -w &

# gnome-panel is the panel for GNOME desktop environment.
#gnome-panel &

# ROX is a fast, user friendly desktop which makes extensive use of drag-and-drop
rox --pinboard=PIN &

# run the window manager
exec openbox

^-------------------------------- CUT HERE ---------------------^

---

### Post by Equanimity on 2005-04-05
Thank you very much, I totally missed the "default" option in GDM. Works well.

---

