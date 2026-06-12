---
title: "using xfdesktop"
date: 2007-04-22
forum: Desktop Environments
---

### Post by ajmorris on 2007-04-22
i am using gnome with xfdesktop instead of nautilus.... to do this i edited ~/.gnome2/session.
Below is my edited version of this file (the bold part is what i changed). My problem is, when gnome starts, it takes forever on the loading of the gnome-panel and as a result the system tray takes forever to load so beryl and my firewall take ages. Also a terminal starts on startup however nowhere, is it specified to open one. anyone know how to fix theses problems, (especially the delayed system tray start as this is starting to really piss me off.)

[Default]
0,id=117f000101000117721431500000117150004
0,RestartStyleHint=1
0,Program=update-notifier
0,CurrentDirectory=/home/l337h4x0r
0,CloneCommand=update-notifier --sm-config-prefix /update-notifier-ic8TQs/ 
0,RestartCommand=update-notifier --sm-config-prefix /update-notifier-ic8TQs/ --sm-client-id 117f000101000117721431500000117150004 --screen 0 
1,id=117f000101000117721431600000117150005
1,Program=gnome-power-manager
1,CurrentDirectory=/home/l337h4x0r
1,CloneCommand=gnome-power-manager --sm-config-prefix /gnome-power-manager-JbVLLs/ 
1,RestartCommand=gnome-power-manager --sm-config-prefix /gnome-power-manager-JbVLLs/ --sm-client-id 117f000101000117721431600000117150005 --screen 0 
2,id=117f000101000117721431600000117150006
2,RestartStyleHint=2
2,Priority=50
2,Program=gnome-cups-icon
2,CurrentDirectory=/home/l337h4x0r
2,CloneCommand=gnome-cups-icon --sm-config-prefix /gnome-cups-icon-W8cV2s/ 
2,RestartCommand=gnome-cups-icon --sm-config-prefix /gnome-cups-icon-W8cV2s/ --sm-client-id 117f000101000117721431600000117150006 --screen 0 
3,id=117f000101000117721431800000117150007
3,RestartStyleHint=0
3,Program=evolution-alarm-notify
3,CurrentDirectory=/home/l337h4x0r
3,CloneCommand=evolution-alarm-notify --sm-config-prefix /evolution-alarm-notify-XtDrXs/ 
3,RestartCommand=/usr/lib/evolution/2.10/evolution-alarm-notify --sm-config-prefix /evolution-alarm-notify-XtDrXs/ --sm-client-id 117f000101000117721431800000117150007 --screen 0 
4,id=117f000101000117721434400000117150010
4,Program=gnome-terminal
4,CurrentDirectory=/home/l337h4x0r
4,CloneCommand=gnome-terminal --sm-config-prefix /gnome-terminal-ahDZat/ 
4,RestartCommand=gnome-terminal --sm-config-prefix /gnome-terminal-ahDZat/ --sm-client-id 117f000101000117721434400000117150010 --screen 0 --window-with-profile-internal-id=Default --show-menubar --role=gnome-terminal-12041--2138082060-1177214344 --active --geometry 80x24+0+23 --title l337h4x0r@l337h4x0r-ubuntu:\\ ~ --working-directory /home/l337h4x0r --zoom 1 
5,id=117f000101000117721431300000117150000
5,RestartStyleHint=2
5,Priority=40
5,Program=gnome-panel
5,CurrentDirectory=/home/l337h4x0r
5,CloneCommand=gnome-panel --sm-config-prefix /gnome-panel-CqwEks/ 
5,RestartCommand=gnome-panel --sm-config-prefix /gnome-panel-CqwEks/ --sm-client-id 117f000101000117721431300000117150000 --screen 0 
6,id=117f000101000117721431300000117150002
6,RestartStyleHint=0
6,Priority=40
[B]6,Program=thunar
6,CurrentDirectory=/home/l337h4x0r
6,CloneCommand=xfdesktop
6,RestartCommand=xfdesktop[/B]
7,id=117f000101000117721432200000117150008
7,Program=evolution-exchange
7,CurrentDirectory=/
7,CloneCommand=evolution-exchange --sm-config-prefix /evolution-exchange-9tZQpx/ 
7,RestartCommand=evolution-exchange --sm-config-prefix /evolution-exchange-9tZQpx/ --sm-client-id 117f000101000117721432200000117150008 --screen 0 
8,id=117f000101000117721431300000117150001
8,RestartStyleHint=1
8,Priority=40
8,Program=gnome-volume-manager
8,CurrentDirectory=/home/l337h4x0r
8,CloneCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-QV4D2z/ 
8,RestartCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-QV4D2z/ --sm-client-id 117f000101000117721431300000117150001 --screen 0 
9,id=117f000101000117721431400000117150003
9,RestartStyleHint=2
9,Priority=20
9,Program=metacity
9,CurrentDirectory=/home/l337h4x0r
9,DiscardCommand=rm -f /home/l337h4x0r/.metacity/sessions/1177214381-11781-3892089101.ms 
9,CloneCommand=metacity 
9,RestartCommand=metacity --sm-save-file 1177214381-11781-3892089101.ms 
10,RestartCommand=restricted-manager --check 
11,RestartCommand=gksu firestarter 
12,RestartCommand=/usr/lib/evolution/2.10/evolution-alarm-notify 
13,RestartCommand=cairo-clock 
14,RestartCommand=nm-applet --sm-disable 
num_clients=15

---

### Post by ajmorris on 2007-04-22
never mind, i fixed it. I got rid of the lines : 6,CloneCommand=xfdesktop 6,RestartCommand=xfdesktop
completely and just put a startup entry in sessions for xfdesktop and that fixed it.

---

