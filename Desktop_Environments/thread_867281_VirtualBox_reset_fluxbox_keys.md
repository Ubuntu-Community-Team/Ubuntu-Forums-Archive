---
title: "VirtualBox reset fluxbox keys"
date: 2008-07-22
forum: Desktop Environments
---

### Post by tanyeun on 2008-07-22
hey guys,
I recently found out that 
after I run VurtualBox
all my shortcut key settings on fluxbox 
doesn't work anymore
even if I stop running it
the only way is to relogin
other better ways?

thx,

David

---

### Post by markjensen on 2008-07-23
I don't recall running into this problem at all.

I am 100% fluxbox user, and use Virtualbox on rare occasion.   You would think I would have noticed that my assigments in the keys file were no longer working.

Let me re-verify this when I get back home tonight, and let you know.

How did you install virtualbox?  Did you use apt/synaptic?

As an interim test, you can try using the "restart" (I think it is called that, I hardly ever use it) option from your flux menus.  That will restart the flux part of your session.  Your window decorations will go away for a second, then be reloaded.  I think this will reload your keys file too, so this may be one step better than logging out/in.

---

### Post by tanyeun on 2008-07-23
I installed VirtualBox a while ago
I believed that I installed it using apt-get or aptitude

I usually use the 4th workspace to run VirtualBox
one thing very obvious is that I can't switch back
to say workspace 1 using alt+F1, I have to click it

I found out that
I can still use some other keys right after I started VirtualBox
but after I hit Win+E which is the shortcut to open filebrowser in XP
then almost every keys froze, including right/middle/left button of the mouse

then I found out that if I didn't run Virtualbox at all
simply hit win+E, same thing happens
but I didn't do key binding to win+E in my keys file
do you have the same situation?

btw, my machine is lenovoX61

thx,

David

---

### Post by markjensen on 2008-07-23
Ok, from your description, it seems you are having Virtualbox run in one of the sessions typically used for TTY access, found under CTRL+ALT+F2 and such?  I've not heard of doing such a thing.

I run Virtualbox as a windowed app on my current desktop.  It is not interfering with any of my ability to use keys, other than when Virtualbox has the input, and you have to press the right CTRL key to exit Virtuabox 'focus'.

Your problem with Win+E sounds odd.  I have a declartion for Mod4 E in my keys file in order to call up thunar as a file explorer of sorts (like you, I bounce between Windows and Linux, so I like some common keycommands).   You said you don't have a keybinding for it?

Could you post your keys file?

---

### Post by tanyeun on 2008-07-23
> **markjensen said:**
> 
Ok, from your description, it seems you are having Virtualbox run in one of the sessions typically used for TTY access, found under CTRL+ALT+F2 and such?  I've not heard of doing such a thing.

Oh, you misunderstood
I run virtualbox exactly as the way you did, I didn't run in different tty

here's my ~/.fluxbox/keys
my Win key is represented as Super_L not Mod4, that's pretty weird >"<
```
OnDesktop Mouse1 :HideMenus
OnDesktop Mouse2 :WorkspaceMenu
OnDesktop Mouse3 :RootMenu
OnDesktop Mouse4 :NextWorkspace
OnDesktop Mouse5 :PrevWorkspace

Mod1 Tab :NextWindow
Mod1 Shift Tab :PrevWindow
Mod1 F1 :Workspace 1
Mod1 F2 :Workspace 2
Mod1 F3 :Workspace 3
Mod1 F4 :Workspace 4
Mod1 F5 :Workspace 5
Mod1 F6 :Workspace 6
Mod1 F7 :Workspace 7
Mod1 F8 :Workspace 8
Mod1 F9 :Workspace 9
Mod1 F10 :Workspace 10
Mod1 F11 :Workspace 11
Mod1 F12 :Workspace 12
Mod1 F :execCommand /usr/bin/firefox 
Mod1 T :ExecCommand /usr/bin/tomboy
Mod1 D :ExecCommand /usr/bin/stardict 
Mod1 Z :ExecCommand /usr/bMod1 S :ExecCommand /usr/bin/xterm alsamixer
Mod1 N :ExecCommand /usr/bin/nm-applet
Mod1 E :ExecCommand /usr/bin/rox-filer .
Mod1 M :ShowDesktop
Super_L Q :Quit
Super_L R :Restart

```
I binded Mod4 E to open file explorer before
but it will result in a conflict in VirtualBox
and my right CTRL doesn't work very well too ToT
(the VirtualBox window will frozed)

thx,

David

---

### Post by markjensen on 2008-07-23
Well, I am at a loss.   All I know is that my keys work all the time - pre-Virtualbox.  During Virtualbox (as long as VB doesn't have 'focus').  And after I have used Virtualbox.

Are you sure it isn't related to the VB session having the input?

I can post my keys file for comparison, but really, other than the Super_L versus Mod4, there isn't any functional difference.
```
!mouse actions added by fluxbox-update_configs
OnDesktop Mouse1 :hideMenus
OnDesktop Mouse2 :workspaceMenu
OnDesktop Mouse3 :rootMenu

# Control, Shift, Mod1 (Alt), Mod4 (Windows)
# are valid modifiers to key commands
#
Mod1 Tab :NextWindow
Mod1 Shift Tab :PrevWindow
Mod1 F4 :KillWindow
Mod1 Print :Exec import -window root ~/print.png
Mod4 k :Exec xterm
Mod4 e :Exec thunar ~
Mod4 r :Exec fbrun -pos 100 100
Mod4 l :Exec gnome-screensaver-command --lock
Mod4 d :ToggleDecor
Mod4 Print :Exec ss_select
Mod4 1 :Exec aoss epiphany http://runescape.com
Alt Print :Exec import -window root ~/print.png
Control Mod1 x :Exec oocalc
Control Mod1 w :Exec oowriter
# Control Mod1 g :Exec fbsetbg -r ~/.fluxbox/backgrounds/g/1680x1050/
Control Mod1 g :Exec conkywall-g
# Control Mod1 r :Exec fbsetbg -r ~/.fluxbox/backgrounds/r/1680x1050/
Control Mod1 r :Exec conkywall-r
Control Mod1 p :Exec conkywall-pg
Mod4 F9 :Exec amixer set Master 5%-
Mod4 F10 :Exec amixer set Master 0%
Mod4 F11 :Exec amixer set Master 70%
Mod4 F12 :Exec amixer set Master 5%+
Mod4 Left :Exec 3ddesk --gotoleft
Mod4 Right :Exec 3ddesk --gotoright
Mod4 m :RootMenu
Control Shift Esc :Exec xkill
Mod4 a :Exec /bin/bash /home/mark/bin/dyn_avatar
Mod4 F1 :Exec xrandr -o 0
Mod4 F2 :Exec xrandr -o 1
Mod4 F3 :Exec xrandr -o 2
Mod4 F4 :Exec xrandr -o 3
# Logitech special keycodes through xev
None 162 :#cd play/pause
None 164 :#cd stop
None 144 :#cd skip back
None 153 :#cd skip fwd
None 160 :Exec amixer set PCM 0%
Mod4 160 :Exec amixer set PCM 70%
None 174 :Exec amixer set PCM 5%-
None 176 :Exec amixer set PCM 5%+
None 236 :Exec thunderbird
None 178 :Exec firefox
None 161 :Exec xcalc
None 175 :#KillWindow
None 134 :#browser back
#OnDesktop Mouse1 :hideMenus
#OnDesktop Mouse2 :workspaceMenu
#OnDesktop Mouse3 :rootMenu
#OnDesktop Mouse4 :nextWorkspace
#OnDesktop Mouse5 :prevWorkspace
```

---

### Post by tanyeun on 2008-07-23
thx anyway
and the restart suggestion is pretty good
^_^

---

### Post by markjensen on 2008-07-24
> **tanyeun said:**
> thx anyway
and the restart suggestion is pretty good
^_^
Does that mean that using the Fluxbox menu item to restart (which leaves all apps running, and just seems to re-init fluxbox) gets your keys working properly again?

This is an odd one, indeed.

---

### Post by tanyeun on 2008-07-27
yes all keys works properly again
except when you open up Virtualbox
I can't use alt+F1 to jump back to desktop [1-3]
(workspace [1-3], I usually use 4 deskdops(workspaces))

I reinstall Virtualbox again yesterday
I found that I can't install virtualbox using apt-get
due to permission forbidden
so I installed Virtualbox-ose version 1.5

but the problems are the same
and I found that it is not the problem of Win+E
in fact
if I press Win only, then all keys will be disabled

---

### Post by tanyeun on 2009-11-14
lately 
I found out a solution!
i.e.
add root to vboxusers
```
sudo adduser root vboxusers
```
then all keys works pretty well, no conflicts

---

### Post by markjensen on 2009-11-14
Wow!  A few releases of *buntu have occurred between this problem and your recent post!  :O

Glad you got your issue settled, though!

---

### Post by tanyeun on 2009-11-14
actually I already solved the problem
but always forgot to repost back here :P

---

