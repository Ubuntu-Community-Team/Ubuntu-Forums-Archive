---
title: "LXPanel won't run any logout-command"
date: 2009-03-24
forum: Desktop Environments
---

### Post by Gabbsmo on 2009-03-24
I've been trying two commands to logout from my openbox session and return to GDM. Both work from the terminal but not form the Logout-button in LXPanel.

I've installed it in my Openbox-session alongside with the default ubuntu desktop.

Distro: Ubuntu 8.10
WM: openbox
Session Manager: GDM

The first is simply:
```
killall openbox
```

And the other one:
```
~/.scripts/shutdown
```
```

#!/bin/bash

gmessage "Are you sure you want to shut down your computer?" -center -title "Take action" -font "Sans bold 10" -default "Cancel" -buttons "_Cancel":1,"_Log out":2,"_Reboot":3,"_Shut down":4 >/dev/null 

case $? in
	1)
		echo "Exit";;
	2)
		killall openbox;;
	3)
		sudo shutdown -r now;;
	4)
		sudo shutdown -h now;;
esac

```

---

### Post by Denestria on 2009-03-24
I have it working like this:

Open .config/lxpanel/default/panels/panel and edit the logout section to look like

```
 item {
            name=Logout
            image=gnome-logout
            action=/usr/local/bin/openbox-logout
        }

```

I put the logout script, openbox-logout, in /usr/local/bin and made it executable.

---

### Post by Gabbsmo on 2009-03-24
> **Denestria said:**
> I have it working like this:

Open .config/lxpanel/default/panels/panel and edit the logout section to look like

```
 item {
            name=Logout
            image=gnome-logout
            action=/usr/local/bin/openbox-logout
        }

```

I put the logout script, openbox-logout, in /usr/local/bin and made it executable.


I'll try it as soon as I get home. Can I use my own gmessage-script as well? And what do you mean with "make it executeable"?

---

### Post by Denestria on 2009-03-24
Executable:
```
chmod +x nameofthescript
```

You don't have to use the script I posted if you want to use a different one, I just know for sure that one works.  Change the *action=* to the script you are using.

**BTW, after you make the changes lxpanel will probably need to be restarted before they will show up.

---

### Post by kerry_s on 2009-03-24
my logout script:

```
#!/bin/sh
XMESSAGE=$(which gxmessage) || XMESSAGE=xmessage

$XMESSAGE "Logout Selections" -center -buttons "Cancel":1,"Suspend":2,"Reboot":3,"Shutdown":4,"Exit X":5  
case $? in
1) exit 0 ;;
2) sudo pm-suspend ;;
3) sudo reboot ;;
4) sudo poweroff ;;
5) jwm -exit ;;
esac

```

---

