---
title: "Fluxbox hotkeys -- Problem with NextGroup"
date: 2009-09-20
forum: Desktop Environments
---

### Post by Buce on 2009-09-20
I want to be able to use Super+Up and Super+Down to switch between grouped windows, and Super+Right and Super+Left to switch between tabs within those groups. Here's the section of my .fluxbox/keys file I'm using to achieve this effect:

```
Mod4 Up         :PrevGroup 0
Mod4 Down       :NextGroup 0
Mod4 Left       :PrevTab
Mod4 Right      :NextTab
```

Problem is, if I use Super+Up to bring a group forward, clicking on a group behind it won't raise the clicked-on group unless I click on the group I just raised first.

So if, for example, I have an xterm behind firefox, then use Super+Up to bring xterm to the front, then click on firefox, the xterm will still appear to be in front of firefox -- although, firefox will have focus.

However, if I have an xterm behind firefox, then use Super+Up to bring xterm to the front, and then *click on the xterm or type a key* before clicking on firefox, everything works normally and the xterm won't hide firefox. I don't want to have to do the part in italics, though.

On a possibly related note, when I bring an application forward using the same Super_Up key combo, the application won't capture the first keystroke or two.

Does anyone know how I can fix this? Here's my full keys file:

```
#### QUICK REFERENCE #####
# Super+Fn              -- Minimize, maximize, etc
# Ctrl+Alt+Back/Esc/Del -- Destructive commands
# Alt/Super+1,2,3,...0  -- Workspaces
# Super+Char            -- Launch application
# Super+Alt+Char        -- Launch secondary application

##### BASIC FUNCTIONALITY #####
# Fluxbox menus & toolbar
OnDesktop Mouse1 :HideMenus
OnDesktop Mouse2 :WorkspaceMenu
OnDesktop Mouse3 :RootMenu
Mod4 Menu :ToggleCmd {RootMenu} {HideMenus}
Menu :ToggleCmd {MacroCmd {SetResourceValue session.screen0.toolbar.visible false} {Reconfigure}} {MacroCmd {SetResourceValue session.screen0.toolbar.visible true} {Reconfigure}}
# Kill X, restart fluxbox
Control Mod1 BackSpace :Exit
Control Mod1 Escape    :Reconfigure
#Control Mod1 Delete : #Careful -- very close to Ctrl Alt Backspace
# Function keys
Mod4 F1  :Exec xterm -fg green
Mod4 F2  :Exec fbrun
Mod4 F3  :Minimize
Mod4 F4  :Close
#Mod4 F5  :
#Mod4 F6  :
#Mod4 F7  :
Mod4 F8  :MaximizeVertical
Mod4 F9  :Minimize
Mod4 F10 :Maximize
Mod4 F11 :Fullscreen
Mod4 F12 :ToggleDecor

##### WORKSPACES & WINDOWS #####
# Workspace navigation
Mod4 1      :Workspace 1
Mod4 2      :Workspace 2
Mod4 3      :Workspace 3
Mod4 4      :Workspace 4
Mod4 Mod1 1 :TakeToWorkspace 1
Mod4 Mod1 2 :TakeToWorkspace 2
Mod4 Mod1 3 :TakeToWorkspace 3
Mod4 Mod1 4 :TakeToWorkspace 4
# Window title click-events
OnTitlebar        Mouse2 :StartTabbing
OnTitlebar Double Mouse1 :Shade
OnTitlebar        Mouse3 :WindowMenu
# Window manipulation
OnWindow Mod4 Mouse1      :MacroCmd {Raise} {Focus} {StartMoving}
OnWindow Mod4 Mod1 Mouse1 :MacroCmd {Raise} {Focus} {StartResizing NearestCorner}
Mod4 KP_5                 :MoveUp    100
Mod4 KP_2                 :MoveDown  100
Mod4 KP_1                 :MoveLeft  100
Mod4 KP_3                 :MoveRight 100
Mod4 Mod1 KP_5            :MoveUp    10
Mod4 Mod1 KP_2            :MoveDown  10
Mod4 Mod1 KP_1            :MoveLeft  10
Mod4 Mod1 KP_3            :MoveRight 10
# Window navigation
Mod4 Tab        :NextWindow 0
Mod4 Mod1 Tab   :PrevWindow 0
Mod4 Up         :PrevGroup 0
Mod4 Down       :NextGroup 0
Mod4 Left       :PrevTab
Mod4 Right      :NextTab
Mod4 Mod1 Up    :MoveUp    50
Mod4 Mod1 Down  :MoveDown  50
Mod4 Mod1 Left  :MoveLeft  50
Mod4 Mod1 Right :MoveRight 50

##### APPLICATIONS #####
# TODO http://fluxbox-wiki.org/index.php?title=Keyboard_shortcuts#Using_wmctrl
Mod4      a :Exec pavucontrol
Mod4      d :Exec deluge
Mod4      e :Exec gedit
Mod4 Mod1 e :Exec oowriter -nologo
Mod4      f :Exec firefox -P default -no-remote
Mod4 Mod1 f :Exec firefox -P developer -no-remote
Mod4      m :Exec songbird
Mod4      p :Exec pidgin
Mod4      t :Exec thunderbird
Mod4      v :Exec gizmo
Mod4 Mod1 v :Exec skype
Mod4      x :Exec xterm -fg green
Mod4      z :MacroCmd {Exec firefox -P default -no-remote} {Exec thunderbird} {Exec songbird} #{pidgin}
Mod4      grave :Exec thunar
Mod4 Mod1 grave :ShowDesktop

##### SPECIAL KEYS #####
# Lock/turn off screen
Pause :Exec xscreensaver-command -lock && xset dpms force off
XF86Display :Exec xset dpms force off
# Volume Control
XF86AudioMute :Exec amixer set -q Master toggle
XF86AudioLowerVolume :Exec amixer -q set Master 5%-
XF86AudioRaiseVolume :Exec amixer -q set Master 5%+
# Print screen
Print :Exec scrot `date +%F-%T`_scrot.png
Mod4 Print :Exec import -frame -window $(xprop _NET_ACTIVE_WINDOW -root | awk '{print $5}') `date +%F-%T`_scrot.png
```

---

