---
title: "problem with gnome+xfwm4"
date: 2006-01-10
forum: Desktop Environments
---

### Post by eliabramo on 2006-01-10
I used the guide from this forum to switch metacity with xfwm4. I do all the changes in .gnomerc and gnome-wm and delete the session file, logon again and I had xfwm4 working properly. but when I logon again after saving changes, the splash screen wrote xfwm4 and nothing happens, I had to do Ctrl-Alt-Backspase to go back to GDM.
I have notice than in the first login, the icon was like the metacity icon, but it wrotes only "windows manager", and inn the second login, the icon eas xfwm4, and it wrotes too "xfwm4" but gnome didn't show up.
here is the session file, maybe he caused the problem:


> [Default]
0,id=1077f36976000113667646000000125320003
0,RestartStyleHint=1
0,Priority=40
0,Program=gnome-volume-manager
0,CurrentDirectory=/home/eli2
0,CloneCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-wUYVt3/ 
0,RestartCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-wUYVt3/ --sm-client-id 1077f36976000113667646000000125320003 --screen 0 
1,id=1077f36976000113667646000000125320004
1,RestartStyleHint=1
1,Priority=50
1,Program=update-notifier
1,CurrentDirectory=/home/eli2
1,CloneCommand=update-notifier --sm-config-prefix /update-notifier-p0WID3/ 
1,RestartCommand=update-notifier --sm-config-prefix /update-notifier-p0WID3/ --sm-client-id 1077f36976000113667646000000125320004 --screen 0 
2,id=1077f36976000113667646100000125320005
2,RestartStyleHint=2
2,Priority=50
2,Program=gnome-cups-icon
2,CurrentDirectory=/home/eli2
2,CloneCommand=gnome-cups-icon --sm-config-prefix /gnome-cups-icon-xCa6z3/ 
2,RestartCommand=gnome-cups-icon --sm-config-prefix /gnome-cups-icon-xCa6z3/ --sm-client-id 1077f36976000113667646100000125320005 --screen 0 
3,id=1077f36976000113667646000000125320002
3,RestartStyleHint=2
3,Priority=40
3,Program=nautilus
3,CurrentDirectory=/home/eli2
3,CloneCommand=nautilus --sm-config-prefix /nautilus-kPToO3/ 
3,RestartCommand=nautilus --sm-config-prefix /nautilus-kPToO3/ --sm-client-id 1077f36976000113667646000000125320002 --screen 0 --no-default-window 
4,id=1077f36976000113667646000000125320001
4,RestartStyleHint=2
4,Priority=40
4,Program=gnome-panel
4,CurrentDirectory=/home/eli2
4,CloneCommand=gnome-panel --sm-config-prefix /gnome-panel-kItF51/ 
4,RestartCommand=gnome-panel --sm-config-prefix /gnome-panel-kItF51/ --sm-client-id 1077f36976000113667646000000125320001 --screen 0 
5,id=1077f36976000113667645900000125320000
5,RestartStyleHint=0
5,Priority=20
5,Program=xfwm4
5,CurrentDirectory=/home/eli2
5,CloneCommand=/usr/bin/xfwm4 --sm-client-id default0 --display :0.0 
5,RestartCommand=/usr/bin/xfwm4 --sm-client-id default0 --display :0.0 
num_clients=6


---

