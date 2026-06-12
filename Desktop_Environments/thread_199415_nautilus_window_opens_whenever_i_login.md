---
title: "nautilus window opens whenever i login"
date: 2006-06-18
forum: Desktop Environments
---

### Post by jewishj on 2006-06-18
Whenever I login to ubuntu, a nautilus window of my home directory automatically opens.  Originally it was also opening a terminal window and the system->preferences->sessions window.  I was able to get rid of those two by removing their entries in the ~/.gnome2/session file, but there's only one nautilus entry in that file and removing that results in my desktop not loading either.

Anyone have any idea how to fix this? Here's my ~/.gnome2/session file below

```

[Default]
0,id=117f000001000115066157000000051920002
0,RestartStyleHint=1
0,Priority=40
0,Program=gnome-volume-manager
0,CurrentDirectory=/home/admin
0,CloneCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-fX6ifS/ 
0,RestartCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-fX6ifS/ --sm-client-id 117f000001000115066157000000051920002 --screen 0 
1,id=117f000001000115066157000000051920003
1,RestartStyleHint=2
1,Priority=40
1,Program=nautilus
1,CurrentDirectory=/home/admin/
1,CloneCommand=nautilus --sm-config-prefix /nautilus-2RRviZ/ 
1,RestartCommand=nautilus --sm-config-prefix /nautilus-2RRviZ/ --sm-client-id 117f000001000115066157000000051920003 --screen 0 
2,id=117f000001000115066157000000051920001
2,RestartStyleHint=2
2,Priority=40
2,Program=gnome-panel
2,CurrentDirectory=/home/admin
2,CloneCommand=gnome-panel --sm-config-prefix /gnome-panel-vwT5Ic/ 
2,RestartCommand=gnome-panel --sm-config-prefix /gnome-panel-vwT5Ic/ --sm-client-id 117f000001000115066157000000051920001 --screen 0 
3,id=117f000001000115066157100000051920005
3,Program=gnome-power-manager
3,CurrentDirectory=/home/admin
3,CloneCommand=gnome-power-manager --sm-config-prefix /gnome-power-manager-47W3nS/ 
3,RestartCommand=gnome-power-manager --sm-config-prefix /gnome-power-manager-47W3nS/ --sm-client-id 117f000001000115066157100000051920005 --screen 0 
4,id=117f000001000115066157100000051920004
4,RestartStyleHint=1
4,Program=update-notifier
4,CurrentDirectory=/home/admin
4,CloneCommand=update-notifier --sm-config-prefix /update-notifier-qMlcrS/ 
4,RestartCommand=update-notifier --sm-config-prefix /update-notifier-qMlcrS/ --sm-client-id 117f000001000115066157100000051920004 --screen 0 
5,id=117f000001000115066157100000051920006
5,RestartStyleHint=2
5,Priority=50
5,Program=gnome-cups-icon
5,CurrentDirectory=/home/admin
5,CloneCommand=gnome-cups-icon --sm-config-prefix /gnome-cups-icon-RIsJ5X/ 
5,RestartCommand=gnome-cups-icon --sm-config-prefix /gnome-cups-icon-RIsJ5X/ --sm-client-id 117f000001000115066157100000051920006 --screen 0 
num_clients=6

```

Thanks

---

### Post by Anduu on 2006-06-18
Go to System>Preferences>Sessions and check the "Automatically save changes to session" box.

---

### Post by jewishj on 2006-06-18
thanks!  That fixed it :D

---

### Post by Anduu on 2006-06-18
wOOt!

---

