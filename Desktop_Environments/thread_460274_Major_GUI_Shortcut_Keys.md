---
title: "Major GUI Shortcut Keys"
date: 2007-05-31
forum: Desktop Environments
---

### Post by teejay17 on 2007-05-31
On a daily basis I use Gnome, Kubuntu, Fluxbox, IceWM, and Xubuntu.
Where is the best place to find shortcut keys for these respective GUIs?

---

### Post by merlinus on 2007-05-31
This is not an answer to your question, but how did you get your apps to appear on IceWM menus?  

I can open Thunar and click on the executables in /usr/bin to get them to run, but cannot figure out how to place them in the menus, rather than an icon on the desktop.

Also do you use the VirtualX script to switch between these? ([http://doc.gwos.org/index.php/VirtualX](http://doc.gwos.org/index.php/VirtualX))

I am a bit leery of installing it, together with the other things needed to run it.

Thanks!

-merlin

---

### Post by teejay17 on 2007-05-31
> **merlinus said:**
> This is not an answer to your question, but how did you get your apps to appear on IceWM menus?  Or run a file manager like Thunar?

Also do you use the VirtualX script to switch between these? ([http://doc.gwos.org/index.php/VirtualX](http://doc.gwos.org/index.php/VirtualX))

Thanks!

-merlin
Most of the apps just appeared on their own. Whatever doesn't appear, I usually use Win + Spacebar (it opens a textbox to type the program you'd like to launch). 
To switch between GUI, I usually log out and switch session at the log in screen. 
If I have a machine with a lot of RAM, I usually use either Gnome or KDE. It's when I run into memory problems that I either use Xubuntu, IceWM, and Fluxbox.

---

### Post by RedSquirrel on 2007-05-31
> **teejay17 said:**
> On a daily basis I use Gnome, Kubuntu, Fluxbox, IceWM, and Xubuntu.
Where is the best place to find shortcut keys for these respective GUIs?


For Fluxbox, you can create any shortcut keys you want. They are stored in the file **~/.fluxbox/keys**. 

Here's mine:

```
Control Mod1 Left :PrevWorkspace
Control Mod1 Right :NextWorkspace
Mod1 Tab :MacroCmd {Deiconify LastWorkspace} {NextWindow 0}
Mod1 F1 :Workspace 1
Mod1 F2 :Workspace 2
Mod1 F3 :Workspace 3
Mod1 F4 :Workspace 4
Mod1 F5 :ExecCommand xterm
Mod1 F6 :ExecCommand leafpad
Mod1 F7 :ExecCommand abiword 
Mod1 F8 :ExecCommand oowriter
None XF86HomePage :ExecCommand firefox
None XF86Mail     :ExecCommand mozilla-thunderbird
None XF86Search   :ExecCommand gksudo synaptic
Print :Execute import -pause 7 -window root ~/misc/screenshots/screenshot-`date +%Y-%m-%d_%T`.jpg
Mod1 Sys_Req :Execute import -frame ~/misc/screenshots/window-`date +%Y-%m-%d_%T`.jpg
Super_L :RootMenu
Super_R :RootMenu


```
Here are two links:

1) From the [Fluxbox wiki]("http://fluxbox-wiki.org/index.php/Howto_edit_the_keys_file").

2) From the main [Fluxbox docs]("http://fluxbox.sourceforge.net/docbook/en/html/c300.html").


As an alternative to editing the keys file manually, you might want to try fluxconf, which is a gui tool that you can use to make keyboard shortcuts. I haven't tried it though, so I can't say how useful it is. fluxconf is in the repositories.

---

### Post by yabbadabbadont on 2007-05-31
> **RedSquirrel said:**
> ....

Looks like your keyboard has multimedia keys.  (or is it a laptop with them?)

---

### Post by RedSquirrel on 2007-05-31
> **yabbadabbadont said:**
> Looks like your keyboard has multimedia keys.  (or is it a laptop with them?)

It's a Logitech Access keyboard. For a while I was using xmodmap to setup the keys, but now I have it setup so that Xorg does it for me without too much fuss. ;)

```
       Option          "XkbModel"      "logiaccess"
```

---

### Post by teejay17 on 2007-05-31
> **RedSquirrel said:**
> For Fluxbox, you can create any shortcut keys you want. They are stored in the file **~/.fluxbox/keys**. 

Here's mine:

```
Control Mod1 Left :PrevWorkspace
Control Mod1 Right :NextWorkspace
Mod1 Tab :MacroCmd {Deiconify LastWorkspace} {NextWindow 0}
Mod1 F1 :Workspace 1
Mod1 F2 :Workspace 2
Mod1 F3 :Workspace 3
Mod1 F4 :Workspace 4
Mod1 F5 :ExecCommand xterm
Mod1 F6 :ExecCommand leafpad
Mod1 F7 :ExecCommand abiword 
Mod1 F8 :ExecCommand oowriter
None XF86HomePage :ExecCommand firefox
None XF86Mail     :ExecCommand mozilla-thunderbird
None XF86Search   :ExecCommand gksudo synaptic
Print :Execute import -pause 7 -window root ~/misc/screenshots/screenshot-`date +%Y-%m-%d_%T`.jpg
Mod1 Sys_Req :Execute import -frame ~/misc/screenshots/window-`date +%Y-%m-%d_%T`.jpg
Super_L :RootMenu
Super_R :RootMenu


```Here are two links:

1) From the [Fluxbox wiki]("http://fluxbox-wiki.org/index.php/Howto_edit_the_keys_file").

2) From the main [Fluxbox docs]("http://fluxbox.sourceforge.net/docbook/en/html/c300.html").


As an alternative to editing the keys file manually, you might want to try fluxconf, which is a gui tool that you can use to make keyboard shortcuts. I haven't tried it though, so I can't say how useful it is. fluxconf is in the repositories.

As always, RedSquirrel, you've provided awesome info! Thanks. 
Every time I see your icon I know I'll learn something--regardless of the thread.

---

### Post by RedSquirrel on 2007-05-31
> **teejay17 said:**
> As always, RedSquirrel, you've provided awesome info! Thanks. 
Every time I see your icon I know I'll learn something--regardless of the thread.

Glad to help. Happy keyboarding! :D

---

