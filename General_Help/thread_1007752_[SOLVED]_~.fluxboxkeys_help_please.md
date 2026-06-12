---
title: "[SOLVED] ~/.fluxbox/keys help please"
date: 2008-12-10
forum: General Help
---

### Post by tjwoosta on 2008-12-10
i cant figure out how to set it so my tux key (windows key with a sticker over it) will launch fbrun in fluxbox

i have been trying to follow these two guides 
[http://ubuntuforums.org/showthread.php?t=617812]("http://ubuntuforums.org/showthread.php?t=617812")

[http://www.gentoo.org/doc/en/fluxbox-config.xml]("http://www.gentoo.org/doc/en/fluxbox-config.xml")


this is my keys file so far
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
None Mod4 :Exec fbrun

```

i have also tried changing it to..

None Mod4 :ExecCommand fbrun

Mod4 :ExecCommand fbrun

Mod4 :Exec fbrun

Mod4 Mod4 :Exec fbrun

Mod4 Mod4 :ExecCommand fbrun


what am i doing wrong?

---

### Post by kerry_s on 2008-12-10
how about:
Mod4 None :Exec fbrun

does the standard> alt+f2 work

---

### Post by tjwoosta on 2008-12-10
> 
how about:
Mod4 None :Exec fbrun

does the standard> alt+f2 work 


lol, yea i also tried Mod4 None :Exec fbrun

and no alt-f2 does not work, because i have set it so the alt F-(1-12) buttons change workspaces
(Mod1 is alt)

but the command fbrun does open a run dialouge because i have run it from the terminal just to make sure

also i have it as a menu enty and that works to open the run dialouge

---

### Post by kerry_s on 2008-12-10
> **tjwoosta said:**
> lol, yea i also tried Mod4 None :Exec fbrun

and no alt-f2 does not work, because i have set it so the alt F-(1-12) buttons change workspaces
(Mod1 is alt)

but the command fbrun does open a run dialouge because i have run it from the terminal just to make sure

also i have it as a menu enty and that works to open the run dialouge

it says here-> [http://fluxbox-wiki.org/index.php?title=Keyboard_shortcuts](http://fluxbox-wiki.org/index.php?title=Keyboard_shortcuts)

you can use the key code and fluxbox will understand, you should give that a try. run xev to get the key code.

---

### Post by tjwoosta on 2008-12-10
thats it!

thank you

ive been trying to figure this out for about an hour now

---

