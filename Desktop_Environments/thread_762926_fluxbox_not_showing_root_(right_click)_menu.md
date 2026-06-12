---
title: "fluxbox not showing root (right click) menu"
date: 2008-04-22
forum: Desktop Environments
---

### Post by eidam655 on 2008-04-22
hello,

i have ubuntu gutsy installed on my notebook. i wanted to try fluxbox, so i typed

sudo aptitude install fluxbox

and it installed fluxbox & some dependant library. when at the logging screen, i can choose the fluxbox session.

the problem is, when i log in to the fluxbox, i cannot access the Root (right click) Menu.

any advices on how to get in? :)

thx in advance.

---

### Post by p_quarles on 2008-04-22
Can you post the contents of your ~/.fluxbox/keys file? In my experience, that is most often the issue with things like this.

---

### Post by tuanduc on 2008-04-22
Run this command in terminal:
sudo update-menus

---

### Post by eidam655 on 2008-04-23
contents of ~/.fluxbox/keys

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
```

and to the other post: i would love to run ANY application, but Alt+F2 does not run the Run Application applet as in gnome :)

---

### Post by eriqjaffe on 2008-04-23
> **eidam655 said:**
> and to the other post: i would love to run ANY application, but Alt+F2 does not run the Run Application applet as in gnome :)You actually want to run "sudo update-menus" from your GNOME session, so it'll create the base Fluxbox menu for you.

Alternately, you could just CTRL-ALT-F1 to bail out to a command-line and enter it there, I suppose.  You'd need to restart your Fluxbox session to make it take effect, though.

---

