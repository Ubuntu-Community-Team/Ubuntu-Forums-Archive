---
title: "I need some help getting Openbox up and running."
date: 2009-04-16
forum: Desktop Environments
---

### Post by Jordan777 on 2009-04-16
So I've installed openbox and I want to use it just by itself.  I've installed thunar and the pypanel but here is the thing, I'm still really new to this sort of task.  I just use ubuntu with gnome so I'm not familiar with how to get other things like this up and running.  I can start an openbox session just fine but I don't know how to add links to things like applications, places and system in gnome or just programs in general.  I don't need everything but it would be useful to create a drop down menu (or up) for those things in the right-click menu.  And also when I start openbox it's truly bare bones (as it is supposed to be).  But I want some things to autostart like pypanel, thunar and just basic elements like my wireless internet.  I realize this is a lot to ask for help on but any help is really appreciated! ;)

---

### Post by Ace1989 on 2009-06-03
I would like some help with this too! I just installed the openbox packages, and I need to get internet working. It works just fine in Gnome, I don't even have to enable a propitiatory driver...

---

### Post by Locutus_of_Borg on 2009-06-03
openbox, yay

the file to put all your autostart applications in is:
```
~/.config/openbox/autostart.sh
```
jut put each application on its own line and end each line with a &

i use pypanel as well, and i have found that i have to delay it a few seconds to wait for X to fully load up otherwise pypanel does not start, to do this just make the line for pypanel look something like:
```
(sleep 2 && pypanel)&
```
some other apps i like to have start up are
thunar --daemon (for automounting drives and disks)
feh --bg-scale ~/background.png (for giving me a desktop background image)
and
xcompmgr (for some compositing effects)

for your wireless, i highly recommend wicd
wicd itself should be run as root, so put into /etc/rc.d/rc.local a new line containing just wicd (ubuntu might have it's *.local script in another location, but it should be in the /etc/ directory if it's not exactly where it is on mine)
then you can either, as normal user, run 'wicd-client' to have an icon in your system tray to manage wireless signals, or, like i prefer, run 'wicd-client -n' to just open up a window to select your wireless signal and then you can close the window to not have excessive icons and running applications

one of the best things about openbox is the level of configurability, read through the ~/.config/openbox/rc.xml file to see just how much stuff you can do with it

i find its good to set a keybinding in that file to open up all your commonly used applications rather than having to select from menus which is much more time consuming (for example i can open firefox with super+f, a terminal with super+z, midnight commander with super+h, and rtorrent with super+t  you of course can set it to whatever you want but its a lot faster than clicking on buttons with your mouse)

you are going to want to install obconf, obmenu, and lxappearance
obconf lets you easily select openbox themes and appearances, obmenu lets you easily edit the right-click menu, and lxappearnce can control your gtk themes, you might also be interested in menumaker which can automatically generate an applications menu by scanning your entire file system for executables and organizing them (after installation just run 'mmaker -vf OpenBox3' to generate a new more thorough menu)

also, you can use gnome-panel in place of pypanel if you want, but gnome-panel is a huge application, i prefer pypanel myself.

feel free to ask me anything else in regards to openbox

---

