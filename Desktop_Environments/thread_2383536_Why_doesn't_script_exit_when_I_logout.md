---
title: "Why doesn't script exit when I logout?"
date: 2018-01-26
forum: Desktop Environments
---

### Post by again? on 2018-01-26
I installed an xfce session in Ubuntu 17.10.
I created a bash loop script to provide hot corners and added to sessions & startups.
Anyone know why the script doesn't exit when I logout?
It remains running and a new instance is started when I log back in to the xfce session.
The script...
```
#! /bin/bash

# script to use for a hot corner command
# get the coordinates for whatever corner you want to use by running:
# 	sleep 3; eval $(xdotool getmouselocation --shell); echo $X$Y
#
# Place cursor in corner immediately upon executing command and wait 3 seconds
# replace the mouselocation variables below with your $X$Y output

mouselocationtl=00     # top left xy coordinates
mouselocationtr=16790  # top right xy coordinates


while true; do
	sleep 0.5
	eval $(xdotool getmouselocation --shell)

	## top left corner	
	if [ "$X$Y" = "$mouselocationtl" ]; then
		xdotool key Super+d &
		sleep 0.2
		xdotool mousemove_relative --polar 135 3

	elif [ "$X$Y" = "$mouselocationtr" ]; then
		altyo --toggle &
		sleep 0.2
		xdotool mousemove_relative --polar 225 3
	fi
done 
exit 0
```

---

### Post by vasa1 on 2018-01-26
What happens if you remove the script from startup? XFCE probably has an optional feature (on by default) to restore the last session and so having a script in startup as well may result in a sort of duplication?

---

### Post by again? on 2018-01-26
Session saving is disabled.
[ATTACH=CONFIG]278332[/ATTACH]

But for good measure I removed the script from startups and cleared saved sessions.
Script does not start at all upon log out/in.

Added script path back to startups and creates one instance but subsequent log out/ins, creates  duplicate instances.
The more I login out/in ,the more instances.
[ATTACH=CONFIG]278333[/ATTACH]

Possibly I need to add something to the loop script.
Doesn't duplicate in gnome session.

---

### Post by vasa1 on 2018-01-26
Okay! One other question: does a clean Xubuntu (in VBox or on another machine/partition/etc) do this? I'm asking because you've added "xfce" to Ubuntu and so there could be some sort of conflict? Also, xfce maybe more basic than xubuntu-desktop with the latter possibly allowing for a complete experience.

Came across [https://serverfault.com/questions/115999/if-i-launch-a-background-process-and-then-log-out-will-it-continue-to-run](https://serverfault.com/questions/115999/if-i-launch-a-background-process-and-then-log-out-will-it-continue-to-run) Could it help?

---

### Post by again? on 2018-01-26
> **guber2 said:**
> 
[s]Doesn't duplicate in gnome session.[/s]
Having another look it appears the script behaves the same with the gnome session.
I thought a user loop script would exit when you logout.
Maybe this isn't the case?
Will focus on the script.
Thanks.

---

### Post by again? on 2018-01-26
> **vasa1 said:**
> 
Came across [https://serverfault.com/questions/115999/if-i-launch-a-background-process-and-then-log-out-will-it-continue-to-run](https://serverfault.com/questions/115999/if-i-launch-a-background-process-and-then-log-out-will-it-continue-to-run) Could it help?

I understand more about hiccups :-& than nohup and SIGHUP but stumbled on [this page]("https://bbs.archlinux.org/viewtopic.php?id=195965")
showing how to launch a loop script as a systemd user service and let systemd handle what happens at logout.

Added this to startups....
```
systemd-run --user --unit=customcorners /home/glen/scripts/custom-corners-xfce.sh
```
Logged out back in.
[ATTACH=CONFIG]278335[/ATTACH]
Will look into creating a permanent customcorners systemd service I can stop/start when playing counterstrike.

---

### Post by again? on 2018-01-27
For anyone interested this is how I made a systemd user service to run the script.

Created ~/.config/systemd/user/customcorners.service
```
[Unit]
Description=Custom hot corners service

[Service]
ExecStart=/home/glen/scripts/custom-corners-xfce.sh

[Install]
WantedBy=default.target
```

Enabled the service (will autostart at login)...
```
systemctl --user enable customcorners
```
Log out, 
or start the service now...
```
systemctl --user start customcorners
```

*****Note**: Had to add $DISPLAY to my script for it to work.
```
export DISPLAY=":0"
```
I have to read more about env variables for systemd user services.

---

### Post by again? on 2018-01-27
```

```> **guber2 said:**
> 

*****Note**: Had to add $DISPLAY to my script for it to work.
```
export DISPLAY=":0"
```
I have to read more about env variables for systemd user services.

To not have to set DISPLAY env in the script I created /home/glen/.config/environment.d/99-glen.conf
as shown in the [arch wiki]("https://wiki.archlinux.org/index.php/Systemd/User#Environment_variables")
_99-glen.conf_
```
DISPLAY=:0
DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus
XAUTHORITY=/home/glen/.Xauthority

```

---

