---
title: "HOWTO: The Best Way To Play Games On Ubuntu"
date: 2008-02-17
forum: Gaming &amp; Leisure
---

### Post by mikeym on 2008-02-17
Hi,

I think I have found **the best **way of running games on Ubuntu. By creating a new X server you get to run games faster, toggle between running games and your desktop using [Ctrl]+[Alt] + F7, and by starting the new X server as a new daemon you can stop it without any fuss if it goes down - a much more likely prospect where games are concerned. Also there are no issues with Compiz or the Xfce panel.

Anyway there was a project to allow you to launch games on a new X server but it appears to be long dead so I've made this script to do it for you.

This is a script to install 'x.game'. Copy the code into 'install-x.game' and run 'chmod +x install-x.game' and run it as root (using *sudo* or *gksudo*). (You will need the *Universe* package repository enabled for installing.)

Zenity based prompts will guide you through the rest.

**[COLOR="Red"]Warning:[/COLOR]** Whilst I've done my best to get this to work responsibly and tested it out on my system to get rid of bugs it does require some modification of sensitive system files such as '/etc/sudoers'. This is because for some reason you require su privileges to change the virtual terminal (the [Alt] + F keys). To get round this I create a group 'chvt' who are allowed to run 'sudo chvt' without being asked for a password. **[COLOR="Red"](edit)[/COLOR]** This has been improved a bit in the new version and thanks to *Cappy* who pointed out a few issues I had in the old script.

**[COLOR="Red"]Known Bugs:[/COLOR]** 
[LIST]
[*]There is still a problem with the way 'x.game' handles spaces in file names if anyone knows a way to do this properly then let me know.
[*]xrandr and other screen tools don't work properly on the new X server and cause it to crash. I'm rewriting 'winefix' to work with this method of starting games and provide useful functions.
[*]The performance boost I get on my dual core PC is not matched by my low-end 1Ghz powerpc that receives a performance drop with the extra overhead of having an extra xserver running.
[/LIST]

**Usage:** Run 'x.game start PROGRAM' to start a new server and launch a game. And 'x.game stop' to stop a server that's not responding properly. Otherwise right click on the desktop and click on exit to close a server. 

Change desktops with [Ctrl] + [Alt] + F7 (normally these are assigned as one higher each time you reboot X) to go to your Ubuntu desktop and press [Ctrl] + [Alt] + F12 to go to x.game.

Lets you select the users who can access *chvt* and therefore *x.game*. If you want to add users then add them to the 'chvt' group.

([COLOR="Red"]**edit)**[/COLOR] Vesion 0.4 - New uninstall option has been added and a number of errors have been fixed.
([COLOR="Red"]**edit)**[/COLOR] Vesion 0.5 - Gives you a notification icon to let you know that *x.game* is running, Has been tested for **hardy**.
([COLOR="Red"]**edit)**[/COLOR] Vesion 0.6 - Installer now lets you select the users to be allowed *chvt* access, Has been tested for **hardy**.
([COLOR="Red"]**edit)**[/COLOR] Vesion 0.7 - Removed references to *gksudo* script needs to be run now as root. Has been tested for **hardy**.
([COLOR="Red"]**edit)**[/COLOR] Vesion 0.8 - Proper user specific x authorization and fixes for a problem with 0.7. Has been tested for **hardy**.

**install-x.game**
```

#!/bin/bash
#x.game linux game daemon
#Version 0.8
#written by mikey <abc.mikey@googlemail.com>

function gettmpdir {
	TMPDIR=$(mktemp /tmp/x.game.XXXXXXXXXX || zenity --info --text="Error unable to create temp directory in /tmp."; exit 1)
}

function uninstall {
	zenity --question --text="Uninstall x.game?"
	if [ $? = 1 ]; then 
		exit 0
	fi
	gettmpdir
	awk '{ if ($1 ~ /^allowed_users=/) { printf "#"; print; } else print }' /etc/X11/Xwrapper.config > $TMPDIR
	grep "#allowed_users=" /etc/X11/Xwrapper.config | head -n 1 | sed "s/#//" >> $TMPDIR
	mv $TMPDIR /etc/X11/Xwrapper.config
	groupdel chvt
	gettmpdir
	sed "s/^\%chvt ALL= NOPASSWD: \/usr\/bin\/chvt$//" /etc/sudoers > $TMPDIR
	visudo -c -f $TMPDIR
	if [ $? != 0 ]; then 
		zenity --info --text="Error updating /etc/sudoers!"
		exit 1
	fi
	if [ -e /etc/sudoers.tmp ]; then 
		zenity --info --text="Error updating /etc/sudoers! Locked by another user. Try again later."
		exit 1
	fi
	chmod 0440 $TMPDIR
	chown 0:0 $TMPDIR
	mv $TMPDIR /etc/sudoers
	USERS=$(awk -F: '{if ($3>=1000 && $3 < 65534) print $1 }' /etc/passwd)
	IFS="
"
	for USR in $USERS
	do
		USRHOME=$(awk -F:  -v user="$USR"  '{if ($1==user) print $6 }' /etc/passwd)
		echo "Removing xauth for $USR in $USRHOME/.Xauthority"
		sudo -u $USR xauth -f $USRHOME/.Xauthority remove :1.1
	done
	zenity --question --text="Uninstall openbox and feh?"
	if [ $? = 0 ]; then 
		apt-get remove openbox feh --yes
	fi
	rm /usr/local/bin/x.game
	rm /usr/share/pixmaps/xgame.xpm
	zenity --info --text="x.game uninstalled."
}

#Check that we are running as root
if [ "$USER" != "root" ]; then
	zenity --info --text="Must be run as 'root'. Try 'sudo'."
	exit 1
fi

if [ "$1" = "--uninstall" ]; then
	uninstall
	exit 0
elif [ -n "$1" ]; then
	echo "Usage: $0 [--uninstall]"
	exit 1
fi

zenity --question --text="Install x.game?"
if [ $? = 1 ]; then 
	exit 0
fi
#replace "allowed_users=console"
#Allow any user to start an XServer
gettmpdir
awk '{ if ($1 ~ /^allowed_users=/) { printf "#"; print; } else print }' /etc/X11/Xwrapper.config > $TMPDIR
echo "allowed_users=anybody" >> $TMPDIR
mv $TMPDIR /etc/X11/Xwrapper.config
#Add group 'chvt' and add current user to group
groupadd chvt
USERS=$(awk -F: '{if ($3>=1000 && $3 < 65534) print "TRUE "$1 }' /etc/passwd)
ANS=$(zenity  --list  --text="Select users to access x.game?" --checklist  --column "Allow" --column "User" $USERS)
IFS="|"
for USR in $ANS
do
        usermod -a -G chvt $USR
	#Authorise X for user on display :1 
	USRHOME=$(awk -F:  -v user="$USR"  '{if ($1==user) print $6 }' /etc/passwd)
	sudo -u $USR xauth -f $USRHOME/.Xauthority add :1.1 . $(mcookie)
done
IFS="
"
#Add group 'chvt' to no password group for command 'chvt'
gettmpdir
cat /etc/sudoers > $TMPDIR; echo "%chvt ALL= NOPASSWD: /usr/bin/chvt" >> $TMPDIR
visudo -c -f $TMPDIR
if [ $? != 0 ]; then 
	zenity --info --text="Error updating /etc/sudoers!"
	exit 1
fi
if [ -e /etc/sudoers.tmp ]; then 
	zenity --info --text="Error updating /etc/sudoers! Locked by another user. Try again later."
	exit 1
fi
chmod 0440 $TMPDIR
chown 0:0 $TMPDIR
mv $TMPDIR /etc/sudoers
#Install required programs from Universe
apt-get install openbox feh --yes
zenity --info --text="Select a background image for desktop."
while true; do
	FILE=$(zenity --file-selection)
	RES=$(echo "${FILE}" | grep -i ".jpg$")
	if [ -n "${RES}" ]; then
		break
	else
		zenity --question --text="Invalid file name. Try again?"
		if [ $? = 1 ]; then 
			exit 0
		fi
	fi
done
gettmpdir
head -n 5 $0 > $TMPDIR
echo "BGIMAGE=\"${FILE}\"" >> $TMPDIR
tail -n 83 $0 >> $TMPDIR
mv $TMPDIR /usr/local/bin/x.game
chmod +rx /usr/local/bin/x.game
#Install icon
gettmpdir
echo '/* XPM */
static char * xgame_xpm[] = {
"32 32 2 1",
" 	c None",
".	c #000000",
"                                ",
"                                ",
"                                ",
"                                ",
"                                ",
"                                ",
"                                ",
"           .                    ",
"          ...       ..          ",
"         ....     .....         ",
"         .....   ......         ",
"          ..... ......          ",
"          ...........           ",
"           .........            ",
"            .......             ",
"             ......             ",
"             .......            ",
"            .........           ",
"           ...........          ",
"           ....  ......         ",
"          .....  .......        ",
"         .....     .....        ",
"         ....       ...         ",
"          ...        .          ",
"           .                    ",
"                                ",
"                                ",
"                                ",
"                                ",
"                                ",
"                                ",
"                                "};' > $TMPDIR
mv $TMPDIR /usr/share/pixmaps/xgame.xpm
chmod +r /usr/share/pixmaps/xgame.xpm
zenity --info --text="Successfully installed.\nRun 'x.game start [program]'."
exit 0

PIDFILE="${HOME}/.xgame.pid"
WMPATH="/usr/bin/openbox"
function start {
	if [ -f "/tmp/.X1-lock" ]; then
		echo "X Display :1 already open"
		sudo chvt 12
		DISPLAY=:1
	else
		echo "Starting Daemon:"
		zenity --notification --text="x.game running..." --window-icon=/usr/share/pixmaps/xgame.xpm &
		echo $! > /tmp/x.game-notification
		start-stop-daemon --start --quiet --oknodo --pidfile $PIDFILE --make-pidfile --name xgame --startas /usr/bin/xinit -- $WMPATH -- :1 vt12 &
		sleep 2s
		DISPLAY=:1
		feh --bg-scale "$BGIMAGE" & 
	fi
	PROGRAM=$1
	echo "Program: $PROGRAM"
	if [ "$PROGRAM" != "" ]; then
		execute $*
	fi
}
function stop {
	echo "Stoping Daemon:"
	start-stop-daemon --stop --quiet --oknodo --pidfile $PIDFILE --name xinit --startas /usr/bin/xinit 
	kill `cat /tmp/x.game-notification`
}
function execute {
	if [ -f "/tmp/.X1-lock" ]; then
		echo "Switching to display :1"
		sudo chvt 12
		DISPLAY=:1
	else
		echo "Display :1 is not running!"
		echo "Try 'x.game start PROGRAM'"
		exit 1	
	fi
	PROGRAM=$1
	shift
	if [ "$PROGRAM" == "" ]; then
		echo "Usage: "
		echo "x.game [start | stop] [PROGRAM] [parameters]"
		exit 1
	else
		while (( "$#" )); do
			if [[ -n "$1" && $1 == *\ * ]]; then
				ARGS="$ARGS \"$1\""
			else
				ARGS="$ARGS $1"
			fi
			shift
		done
	fi
	echo $PROGRAM $ARGS
	echo $ARGS | xargs $PROGRAM
}
#START OF SCRIPT
IFS="
"
SS=$1
echo "Selecting: $SS"
case "$SS" in
	start)
		echo "Starting:"
		shift
		start $*
		;;
	stop)
		echo "Stoping:"
		shift
		stop $*
		;;
	restart)
		echo "Restarting:"
		shift
		stop $*
		start $*
		;;
	*)
		echo "Executing:"
		execute $*
esac
exit 0

```

---

### Post by charlieg on 2008-02-17
Good tip, I'll put that on Free Gamer! :D

---

### Post by rosegarden78 on 2008-02-18
It won't matter if your graphics card doesn't have T&L chips to support 3D rendering.

---

### Post by mikeym on 2008-02-18
Sorry I'm not an expert on graphics cards or even the way X works. 

You will still need the hardware for playing games. The advantage you get from running them on a separate X server is that you don't have much of an overhead from your desktop. The Window Manager I've selected (openbox) is extremely light weight. I've noticed a great performance boost in my games over any other method that I've tried - quite a few. 

This is good when combined with the extra convenience you get from running games like this.

---

### Post by mikeym on 2008-02-20
Hi,

Can anyone confirm that they've tried this and if it's working on their system?

---

### Post by KhaaL on 2008-02-20
did not work on my system, got this output:

```

khaal@Xeraphim:~/no-backup/apps/etqw$ x.game etqw
Selecting: etqw
Executing:
Display :1 is not running!
Try 'x.game start PROGRAM'
khaal@Xeraphim:~/no-backup/apps/etqw$ xg
xgamma    xgc       xgettext
khaal@Xeraphim:~/no-backup/apps/etqw$ x.game start etqw
Selecting: start
Starting:
Starting Daemon:


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux Xeraphim 2.6.22-14-rt #1 SMP PREEMPT RT Tue Feb 12 09:57:10 UTC 2008 i686
Build Date: 18 January 2008
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Wed Feb 20 10:20:04 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module already built-in
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
/usr/local/bin/x.game: line 19: feh: command not found
Program: etqw
Switching to display :1
etqw
xargs: etqw: No such file or directory
khaal@Xeraphim:~/no-backup/apps/etqw$ /usr/bin/xinit:  No such file or directory (errno 2):  no program named "/usr/bin/openbox" in PATH

Specify a program on the command line or make sure that /usr/bin
is in your path.


waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.




```


Tried to switch to the second X-server, but it was only blank.

---

### Post by mikeym on 2008-02-20
Looks like the install failed to install feh (a image display program for showing a background) and openbox (the light weight window manager). 

What output do you get if you run:

```

sudo apt-get install openbox
sudo apt-get install feh
```

from the terminal?

---

### Post by KhaaL on 2008-02-20
You're most correct - I didn't have them installed. but why go and install all these packages? isnt it just easier to run the games in another plain X-server?

---

### Post by mikeym on 2008-02-20
The X server wont process keypresses without a window manager running. I believe this is a bug but it's one that's on Ubuntu. It also makes windows work correctly if you're running something that's not always fullscreen such as *steam*. 

*Feh *is just for showing a background image on the desktop. No necessary but welcome after spending lost of time testing with the hatch background. :)

Can I ask what was preventing the script from installing *openbox* and *feh*? What did you do to install them?

---

### Post by DShroud on 2008-02-20
I tried this and the screen went to a blank screen with cross hatches and the cursor as an x.  The Alt - F7 key stroke didn't work so I had to restart.

I was trying to run WoW from Wine, so maybe that had something to do with it.  Heres what I tried to run...

x.game start  WINEDEBUG=-all wine /home/justin/.wine/drive_c/"Program Files"/"World of Warcraft"/WoW.exe

---

### Post by KhaaL on 2008-02-20
> **mikeym said:**
> The X server wont process keypresses without a window manager running. I believe this is a bug but it's one that's on Ubuntu. It also makes windows work correctly if you're running something that's not always fullscreen such as *steam*. 

*Feh *is just for showing a background image on the desktop. No necessary but welcome after spending lost of time testing with the hatch background. :)

Can I ask what was preventing the script from installing *openbox* and *feh*? What did you do to install them?

Hehe I see. the script seems to have failed installing them, what made it fail I don't know... the output I posted is all I got from after running the script. 

I really like it by the way,.. Very ambitious! You should add a option to uninstall it too for those who like to keep a tidy system (like me).

Wish you luck on this project :)

---

### Post by mikeym on 2008-02-21
The PROGRAM bit in 'x.game start PROGRAM' needs to be a program.

Try:

```
WINEDEBUG=-all x.game start wine /home/justin/.wine/drive_c/"Program Files"/"World of Warcraft"/WoW.exe
```

Did you select a real image file for your background when you were installing? You should have seen this instead hatch (after a brief flash of the hatch). To exit x.game try right clicking on the desktop and selecting exit.

Woops the key combination to switch windows is [ctrl]+[alt]+F7. I'll change my post. One back at your desktop if you're having problems exiting by right clicking you can stop x.game with 'x.game stop'.

---

### Post by mikeym on 2008-02-21
KhaaL you don't have the output from the install there so it wouldn't include any errors from installing *openbox* or *feh*. I'll see about putting more error checking in the install script.

The only thing I can see that would cause a problem is that these packages are part of the Universe repository - it's possible you didn't have this enabled. I've put a note about this in the install instructions. 

Thanks. I'll see about putting a uninstall when I have time. :)

---

### Post by DShroud on 2008-02-21
> **mikeym said:**
> The PROGRAM bit in 'x.game start PROGRAM' needs to be a program.

Try:

```
WINEDEBUG=-all x.game start wine /home/justin/.wine/drive_c/"Program Files"/"World of Warcraft"/WoW.exe
```

Did you select a real image file for your background when you were installing? You should have seen this instead hatch (after a brief flash of the hatch). To exit x.game try right clicking on the desktop and selecting exit.

Woops the key combination to switch windows is [ctrl]+[alt]+F7. I'll change my post. One back at your desktop if you're having problems exiting by right clicking you can stop x.game with 'x.game stop'.

Ok so I reinstalled the script and chose a different image but it didn't change the background, I'm still getting the hatches.  But I tried running the game in a different way, heres what I got...

```
x.game start wine /home/justin/.wine/drive_c/"Program Files"/"World of Warcraft"/WoW.exe
Selecting: start
Starting:
X Display :1 already open
Program: wine
Switching to display :1
wine  "/home/justin/.wine/drive_c/Program Files/World of Warcraft/WoW.exe"

fixme:spoolsv:serv_main (0 (nil))
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 8000000a


































AUDIT: Thu Feb 21 11:02:45 2008: 10626 X: client 1 rejected from local host (uid 1000)
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels

AUDIT: Thu Feb 21 11:02:45 2008: 10626 X: client 1 rejected from local host (uid 1000)
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified




AUDIT: Thu Feb 21 11:02:45 2008: 10626 X: client 1 rejected from local host (uid 1000)
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

AUDIT: Thu Feb 21 11:02:45 2008: 10626 X: client 1 rejected from local host (uid 1000)
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:wgl:process_attach X11DRV or GDI32 not loaded. Cannot create default context.
err:module:LdrInitializeThunk "opengl32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\WoW.exe" failed, status c0000142
```

---

### Post by mikeym on 2008-02-21
OK,

Could you try running:

```
xauth add ubuntu/unix:1 . `mcookie`
```

for me and then retrying x.game?

I may need to add this line to the install to give the authority to launch X on a new display.

---

### Post by mikeym on 2008-02-22
OK,

I've made quite a few fixes on the install script now. I'd appreciate it if someone could try it and tell me how it goes.

---

### Post by DShroud on 2008-02-22
OK, tried it again with the new updated script and it still wouldn't work right...

```
justin@justin:~/Desktop$ x.game start wine /home/justin/.wine/drive_c/"Program Files"/"World of Warcraft"/WoW.exe
Selecting: start
Starting:
Starting Daemon:


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux justin 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Build Date: 18 January 2008
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Fri Feb 22 12:06:49 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module already built-in
Program: wine
Switching to display :1
wine  "/home/justin/.wine/drive_c/Program Files/World of Warcraft/WoW.exe"
fixme:spoolsv:serv_main (0 (nil))
AUDIT: Fri Feb 22 12:06:52 2008: 16585 X: client 1 rejected from local host (uid 1000)
AUDIT: Fri Feb 22 12:06:52 2008: 16585 X: client 2 rejected from local host (uid 1000)
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified


waiting for X server to begin accepting connections Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

feh ERROR: Can't open X display. It *is* running, yeah?
.
AUDIT: Fri Feb 22 12:06:54 2008: 16585 X: client 1 rejected from local host (uid 1000)
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

.AUDIT: Fri Feb 22 12:06:55 2008: 16585 X: client 1 rejected from local host (uid 1000)
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
AUDIT: Fri Feb 22 12:06:55 2008: 16585 X: client 1 rejected from local host (uid 1000)
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

AUDIT: Fri Feb 22 12:06:55 2008: 16585 X: client 1 rejected from local host (uid 1000)
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

AUDIT: Fri Feb 22 12:06:55 2008: 16585 X: client 1 rejected from local host (uid 1000)
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:wgl:process_attach X11DRV or GDI32 not loaded. Cannot create default context.
err:module:LdrInitializeThunk "opengl32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\WoW.exe" failed, status c0000142
justin@justin:~/Desktop$ .
AUDIT: Fri Feb 22 12:06:56 2008: 16585 X: client 1 rejected from local host (uid 1000)
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

..
AUDIT: Fri Feb 22 12:06:58 2008: 16585 X: client 1 rejected from local host (uid 1000)
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

..
AUDIT: Fri Feb 22 12:07:00 2008: 16585 X: client 1 rejected from local host (uid 1000)
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

..
AUDIT: Fri Feb 22 12:07:02 2008: 16585 X: client 1 rejected from local host (uid 1000)
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

..
AUDIT: Fri Feb 22 12:07:04 2008: 16585 X: client 1 rejected from local host (uid 1000)
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

..
AUDIT: Fri Feb 22 12:07:06 2008: 16585 X: client 1 rejected from local host (uid 1000)
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

```

EDIT:  I tried using that command you posted, and I think that made it worse, is there any way I can reverse that?

---

### Post by Sindwiller on 2008-02-23
Something's going horribly wrong...

[http://pastebin.ca/915149](http://pastebin.ca/915149)

---

### Post by neonprophet on 2008-02-23
I would love to test this out, but, I can't change to another terminal in gutsy. It just gives me a flashing curser but no command line.
Any ideas??
:confused::confused::confused:

---

### Post by KIAaze on 2008-02-24
It doesn't work for me. I tried it simply with kobodeluxe, but apparently it has some problems with sdl.
Is it supposed to work with wine apps and window (i.e. non-fullscreen) apps too?

After running "x.game start kobodl" (I made sure it launches fullscreen when run normally), a new x screen appears, completely empty (grey, no background image) with the default X cursor. (right-click to exit also not working)
Then nothing. I switched back to ubuntu and here's the output I got:
```
x.game start kobodl
Selecting: start
Starting:
Starting Daemon:


This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu4)
Current Operating System: Linux KIAaze-laptop 2.6.24-7-generic #1 SMP Thu Feb 7 01:29:58 UTC 2008 i686
Build Date: 20 February 2008  11:54:41AM

        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Sun Feb 24 20:39:42 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module "ddc" already built-in
(II) Module "i2c" already built-in
NTSC PAL NTSC-J
finished output detect: 0
proc lid open
finished output detect: 1
finished output detect: 2
finished all detect
before xf86InitialConfiguration
/usr/local/bin/x.game: line 19: feh: command not found
Program: kobodl
Switching to display :1
kobodl
Application path: '.'
proc lid open
in RADEONProbeOutputModes
after xf86InitialConfiguration
(II) Module "ramdac" already built-in
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
(EE) [drm] Could not set DRM device bus ID.
(EE) RADEON(0): [dri] DRIScreenInit failed.  Disabling DRI.
init memmap
init common
init crtc1
init pll1
restore memmap
restore common
restore crtc1
restore pll1
restore LVDS
enable montype: 2
disable montype: 2
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
Atom 4, CARD32 4, unsigned long 4
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
enable montype: 2
AUDIT: Sun Feb 24 20:39:50 2008: 25428 X: client 1 rejected from local host (uid 1000)
AUDIT: Sun Feb 24 20:39:50 2008: 25428 X: client 2 rejected from local host (uid 1000)
No protocol specified

waiting for X server to begin accepting connections No protocol specified
AUDIT: Sun Feb 24 20:39:50 2008: 25428 X: client 1 rejected from local host (uid 1000)
No protocol specified

     =======================|  DirectFB 1.0.1  |=======================
          (c) 2001-2007  The DirectFB Organization (directfb.org)
          (c) 2000-2004  Convergence (integrated media) GmbH
        ------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2007-12-12 00:46)
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!
[6761] Failed to initialize SDL!

```
Then lots of:
```
AUDIT: Sun Feb 24 20:39:52 2008: 25428 X: client 1 rejected from local host (uid 1000)
No protocol specified
..
AUDIT: Sun Feb 24 20:39:54 2008: 25428 X: client 1 rejected from local host (uid 1000)
No protocol specified

```
And finally, after using x.game stop:
```
giving up.
/usr/bin/xinit:  Resource temporarily unavailable (errno 11):  unable to connect to X server

waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.


/usr/bin/xinit:  unexpected signal 15.

```

P.S:
I really like the way you install your script:
```
tail -n 80 $0 >> /tmp/x.game
gksudo mv /tmp/x.game /usr/local/bin/x.game

```
This is simply too cool. 8)

---

### Post by mikeym on 2008-02-25
OK.

I'm not sure why that last command didn't work! The problem everyone is having is that they don't have permission to start a new XServer on display :1 


The command I gave you gives permission to allow access. First off all to remove what I did before type

```
xauth remove ubuntu/unix:1
```

Then could you show me what you get when you type 

```
xauth list
```

but you're best to remove the long numbers when you post it for security reasons!

---

### Post by mikeym on 2008-02-25
OK.

I think I probably should have used your hostname for the xauth command. What I've given you is mine - I was thrown because mine is still my default *ubuntu*. 

Try this instead;

```
xauth add $(hostname)/unix:1 . $(mcookie)
```

---

### Post by ZylGadis on 2008-02-25
mikeym, there is an old (about 2 years or so) HOWTO somewhere around here that does exactly what you are trying to do, works every time, etc. If you want to be helpful, find and resurrect that thread. You can learn from it for your own scripts, instead of going the way of trial and error.

There is just too much reinventing the wheel in the FLOSS community.

---

### Post by mikeym on 2008-02-25
Thanks for the tip. I hadn't found that HOWTO before. It gave me a simpler solution to the authorization command I was looking for. (although I believe the one above would work just as well.) ([COLOR="Red"]**edit**[/COLOR]) Just noticed that the post you mentioned missed out exactly the same step I did in my script :))

In terms of reinventing the wheel I'm not trying to create anything spectacularly original. There was a project to do exactly what my script does but it's no longer active. I just wanted to share what I find to be the most useful script on my computer - I originally wrote it for myself. 

I hadn't anticipated how tricky getting it to install would be (much harder than the script itself) and I could have just given instructions to do what the script does but I thought it would be nicer if it did it for you. 

Well I can't see any problems with the script now so I'd love to hear back form anyone who's tried it again and see if it's worked.

---

### Post by KIAaze on 2008-02-27
And where is that other thread doing the same thing?

---

### Post by pizpot on 2008-02-27
Mikeym, the script worked fine for me. (7.10)  Thanks for it, I saw the other thread and didn't want to do all the steps.

(had a heck of a time logging in to this forum and having it stick past redirections , or I'd have replied sooner)

---

### Post by peddy on 2008-03-30
having the same error as everybody else...

---

### Post by cdsboy on 2008-03-30
Ya it only works for me if i use

> xauth add $(hostname)/unix:1 . $(mcookie)

every time i start the system up

---

### Post by peddy on 2008-03-31
me too. I forgot to edit my previous post.

---

### Post by mikeym on 2008-03-31
Do you have any unusual setups such as 2 monitors? You're not accessing the machine from a remote location or anything?

Could you give me the errors displayed?

---

### Post by cdsboy on 2008-03-31
Nope no unusual settings. On a laptop. Acer aspire 5050-3785 with an ati express 1100 graphics card. Can't give ya any errors. It goes to a gray screen with some symbol repeated. Hangs when i cancel the x-session

---

### Post by Cappy on 2008-03-31
Here is what I get:
```

$ ./install-x.game 
groupadd: unable to lock group file
/tmp/sudoers file parsed OK

The following NEW packages will be installed:
  libobparser16 libobrender16 openbox

..... (filtered)

The following NEW packages will be installed:
  feh giblib1

.... (filtered)

cappy@cappy-chan:~$ x.game
Selecting: 
Executing:
Display :1 is not running!
Try 'x.game start PROGRAM'

cappy@cappy-chan:~$ x.game start /home/cappy/.Savage2i/savage2.bin
Selecting: start
Starting:
Starting Daemon:

X: user not authorized to run the X server, aborting.
Program: /home/cappy/.Savage2i/savage2.bin
Display :1 is not running!
Try 'x.game start PROGRAM'
cappy@cappy-chan:~$ feh ERROR: Can't open X display. It *is* running, yeah?
giving up.
/usr/bin/xinit:  Connection refused (errno 111):  unable to connect to X server
/usr/bin/xinit:  No such process (errno 3):  Server error.


```


If I use
```
xauth add $(hostname)/unix:1 . $(mcookie)
``` I get the same errors. Nvidia 7900, Gutsy, nvidia-glx-new.


Edit:
Fixed problem.
```
sudo groupadd chvt
sudo usermod -a -G chvt $USER

```
Then I added the line from your script "allowed_users=anybody"
into nano /etc/X11/Xwrapper.config
The file was blank and your regex didn't work.

Your $current_user is unnecessary, $USER is already in the shell; use it instead. Your $current_user will break if someone uses characters you didn't specify.

The script isn't secure, someone can easily put information into the sudoers - you should use mktemp. E.g.
```

tempdir=`mktemp -d /tmp/x.game.XXXXXXXXXX || echo "Unable to create temp directory in /tmp"; clean_up_err`
```

combine the apt-get lines

check for errors on moving/editing the sudoers and Xwrapper. If the file exists and the move fails then abort program. If the file doesn't exist and the move fails then make a new file (in the case of Xwrapper). Sudoers can be another file than the default so it wouldn't be a good idea to tell visudo to write a new sudoers just because the file isn't /etc/sudoers.

I think it would be nice if the view switched back to the Desktop after the program finished using an && when you run the user's program

---

### Post by peddy on 2008-04-02
no, I just have to run it every time I boot (I set it to do so automatically).

works now

---

### Post by Kemper Boyd on 2008-04-05
Thanks for this script mickey, it worked but I needed a bit of tweak. To be honest the first time I ran it I interrupted its process so it fubared my /etc/sudoers (had to rebuild it from recovery mode). So note that if you answer "cancel" to some of the dialogs, you can run into troubles.

After fixing it I had to manually add the chvt group and finally I had to fill the Xwrapper.config which was empty. As said I messed it up so not sure if it's all due to the fact that I interrupted the script with "cancel".

Anyway working now, thanks :)

---

### Post by mikeym on 2008-04-09
Sorry about the long delay in getting back to you. I've been busy with Uni. :) 

I've updated the script to [version 0.4]("http://ubuntuforums.org/showpost.php?p=4348105&postcount=1"). I've tried to address the issues you've been having. 

I've added and uninstall option on the install script. 
I've fixed the security issue with */etc/sudoers* - thanks *Cappy* you're input was a big help.
I've fixed the error where the *chvt* group wasn't created.
However I've not been able to find out why some people's xauth settings are being forgotten when they restart. 

Kemper Boyd, I'm sorry that the script caused a problem with your */etc/sudoers* file. I've not been able to make a fix for this as I can't see where this would be possible. The file is read on a number of lines but only written on one line so it shouldn't be possible for you to exit out at the wrong point - even if you killed it :confused:. Was it a *gksudo* prompt you canceled, or was it one of the zenity prompts? 

Cappy, I don't think exiting when you close the game would be the right way to go. It would add unnecessary complication and doesn't fit well with the idea of opening a dedicated game xserver or box to start games in. You just right click and exit anyway.

Well, I hope this helps.:)

---

### Post by mikeym on 2008-04-09
Hi,

Just updated things again to version 0.5 so that you get a notification icon to let you know if *x.game* is running so you don't start 2 games on top of one another unless you want to.

---

### Post by mikeym on 2008-04-10
Version 0.6 Lets you select from a list the users who should get access to the* chvt* command (and x.game). Also has been tested for **hardy**.

---

### Post by PriceChild on 2008-04-13
```
install-x.game: 6: function: not found
install-x.game: 8: Syntax error: "}" unexpected
```

---

### Post by Ideastone on 2008-04-13
I would think that starting a second X server would create some overhead that would hurt performance. However, if you have sufficiently modern hardware, this could work.

---

### Post by mikeym on 2008-04-14
Ok I need to apologize as there were a couple of problems with the 0.7 script that I didn't uncover before posting it. If anyone ran that script and is now having problems with getting X programs to start. If run from the terminal it would say that you don't have authorization to run on display 0:0 then try deleting your $HOME/.Xauthority file and restarting X with [ctrl] + [alt] + [Backspace] so that the .Xauthority file is regenerated. The problem was that the permissions were messed up on the file by running xauth as root. 

The new script runs xauth as each user. 

PriceChild, can you make sure that you've copied the whole script as I can't see where the error could be happening at that point in the script. 

Ideastone, you're spot on with that. It has a performance drag on my 1GHz PowerPC but on more powerful machines it should improve things especially if you are running things with compositing on your main session. It also avoids the pitfalls of causing conflicts with other programs or crashing your main X session.

---

### Post by Odr on 2008-04-23
hi there,
I've tried your script, I'm running Hardy with an Athlon XP 2000+, 1Gb RAM and a 6600GT 128Mo, yes the game (enemy territory) was really "smoother", but the mouse was acting really weird. Some sort of lags, when i make some quick turns it's starting to "lag" making the game unplayable. I don't have this problem on the main X.
Also, it would be great to give a way to uninstall your script.
keep the good work.

---

### Post by mikeym on 2008-04-24
The only thing I can think of doing is trying to experiment from the second Xsession to see what is happening with the mouse. You could start by trying the second session without any game, so: *x.game start* and when it loads seeing how the mouse is. You can right click on the background to bring up the menu and open a terminal to check out the settings. 

To uninstall just type:

```

install-x.game --uninstall
```

---

### Post by Odr on 2008-04-25
It happened to be a mousepoll issue. problem solved.
I have a last anoying problem, who's not related to your script ;)
Thanks for your reply, keep the good work !

---

### Post by meborc on 2008-04-25
> **mikeym said:**
> The only thing I can think of doing is trying to experiment from the second Xsession to see what is happening with the mouse. You could start by trying the second session without any game, so: *x.game start* and when it loads seeing how the mouse is. You can right click on the background to bring up the menu and open a terminal to check out the settings. 

To uninstall just type:

```

install-x.game --uninstall
```

had to thank you for the thread... it seems like there is no "medal" in first few pages, so i thanked you for this post instead :)

nice work!

---

### Post by Stormspireiv on 2008-04-26
First of all, excellent work!  I tried the original xgame script with limited success in Gutsy before I replaced it with Hardy. The original script was a terrible pain to set up (giving your user the ability to launch X sessions, etc.). Anyway, your script installed perfectly and works like a charm save for its inability to deal with spaces in filenames.

Most, if not all, WINE games have spaces in their pathname so this is a serious drawback.  My workaround has been to create mini scripts for each game:

```
#!/bin/sh

cd ~/".wine/drive_c/Program Files/Folder"

/usr/bin/wine program.exe
```

I then launch that script with xgame and it would work:
```
x.game start /path/to/script
```

Though, for now, this seems like a roundabout way of doing it as you could accomplish a much similar thing in one script (though without your window manager and background).

```
#!/bin/sh

X :3 -ac -terminate &

cd ~/".wine/drive_c/Program Files/Folder"

sleep 2

DISPLAY=:3 /usr/bin/wine program.exe
```

I don't know that much about scripting, but it seems like you should somehow be able to allow it to use filenames with spaces.

---

### Post by Psylocke on 2008-04-26
I am able to just create a shortcut with the following:

"x.game start wine /data/games/World\ of\ Warcraft/Wow.exe"

This is working perfect.

One small thing i noticed:
when running "x.game stop" the script returns with:
"stoping daemon" this must be with double p i suppose :)


Thanx for this great game launcher.

---

### Post by mikeym on 2008-04-28
Well...Uh...thanks. Glad it's been of some use. :)

To be honest the whole install was a real pain to get working but it's going mostly OK now. The space issue is a real pain and I'd like to hear from anyone who can explain how to handle these 'properly' in bash. 

It is a fix for the moment. Hopefully [DRI2]("http://www.x.org/wiki/DRI2") will make this kind of hack unnecessary and we'll get glorious games that can sit happily along side our fancy window managers. (well that's the story according to the folks at the [compiz forums]("http://forum.compiz-fusion.org/showthread.php?t=7912"))

happy gaming!

---

### Post by mikeym on 2008-04-29
Never mind! I was replying to an old post! Silly refresh.

---

### Post by yeaitsdark on 2008-04-30
Ah thanks man great option here. I have dual monitors and being as my "resolution" is something like 2700x1300 most games get rather confused. At any rate it works really nicely thank you very much for making this. It's truly a time saver and when I want to simply browse (like right now I'm on my "F7" desktop while GTA San Adreas is running on the xgame display). It's just awesome for those full screen games! I love you seriously. :D

---

### Post by JonnyM on 2008-05-03
Just coped and pasted the code into a file and ran it... Works perfectly first time, You are a genius for writing this, It's exactly what I've been looking for ever since I switched to Linux because I need to get back to the desktop while I'm playing games to use things like Team speak and Instant messaging. I used to really annoy me that i could do this on windows and not Ubuntu.

Thanks for the great work!

---

### Post by Svenstaro on 2008-07-05
Great script, thanks a lot for creating this :)
Works well so far, except one thing that makes this only half-usable for me:
I'm using a dual screen set-up with Nvidia TwinView and made my left screen the default screen, ie. all windows spawn here except they know better. 
Fullscreen applications are only displayed on my left (primary) screen. That's perfectly fine. 

In x.game my games are spawned in the middle of both screens, now you pointed out that screen tools don't work, so I'm not blaming you, though I'm curious if there is a way to make it only appear on my primary screen? I'm currently looking through the script searching for hints on how to do that, though I suppose asking you isn't a bad idea either :P.

---

### Post by soul.. on 2008-08-03
Hello, 
Just short Q this thing must not work i guess on any Debian/ubuntu based systems ? Yes I'm not with ubuntu (please don't blame me) my system is based on debian etch (its Elive).

OK then just, installed, trying:

```
a@e[~]$ x.game start quake3
Selecting: start
Starting:
Starting Daemon:
/usr/local/bin/x.game: line 17: start-stop-daemon: command not found
Program: quake3
Display :1 is not running!
Try 'x.game start PROGRAM'
a@e[~]$ 
a@e[~]$ feh ERROR: Can't open X display. It *is* running, yeah?
```

What can i do about that start-stop-daemon ?

Anyway I'm did something too before seeing Your's script, to launch q3 in separate x:

1.Created separate xorg config x.q3.
2.Separate script to launch my lovely q3:
```
#!/bin/sh
    cd "/usr/local/games/quake3"
    taskset -c 1 xinit /usr/local/games/quake3/quake3.x86 $* -- :1 -xf86config x.q3

#'taskset -c 1' asigns to only one core, so it can be removed
```
3.But, i need to resolve audit problem (this and pointed me, here to this thread): 
```
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified
```
4.```
xauth add $(hostname)/unix:1 . $(mcookie)
``` helps, but i always must manually this to do; help me solve this smal problem plz. Is it related to users to be allowed chvt access, how can i manually add? Can it be improved somehow ?

Thank you. :)

---

### Post by Vadi on 2008-08-03
Does anyone actually have benchmarks for this?

---

### Post by soul.. on 2008-08-03
Game feels noticeably smoother and main thing frames per second is totally more stable then on desktop.

Switching ttys: q3 <-> desktop takes less time, comparing to: desktop q3 windowed <-> full-screen.

Max fps just from game.. 
shot0316.jpg q3 on work desktop
shot0315.jpg separate x for my q3
If u have some more ideas how to benchmark more, tell it.

**NOTICE is used my own way that i described earlier*

---

### Post by Keldrif on 2008-08-10
I can't seem to figure out how to run a script. If I read the first post right I think I'm suppose to copy the script and paste it into a file named 'install-x.game' then type 'sudo chmod +x install-x.game' in terminal if that is correct what folder should 'install-x.game' be? 

Sorry I'm sure this is a newbie question but this is the first script I've found that I want to run and even us newbies have to start learning somewhere...

thanks
Kel

---

### Post by asbjornn on 2008-08-10
Having read this thread, I'm sure this is a very useful script. Only thing is: Being at least as much of newbie as keldrif, I don't understand the basic steps. 

So if someone would take a minute or two to explain it really slowly, it'll be much appreciated.

\asbjornn

---

### Post by cristo-father on 2008-08-10
> **asbjornn said:**
> Having read this thread, I'm sure this is a very useful script. Only thing is: Being at least as much of newbie as keldrif, I don't understand the basic steps. 

So if someone would take a minute or two to explain it really slowly, it'll be much appreciated.

\asbjornn
x2

---

### Post by Keldrif on 2008-08-10
Hey,hey! I'm back and I got it to work all by myself.  What I did was copy the code in post 1 into a blank txt file and named that file "install-x.game". I saved it into my Home/"Username" folder. Next I right clicked on said file and put a check in the box under the Permissions tab\ allow executing file a program.  Then I opened a terminal window and typed "sudo '/home/"username"/install-x.game" and that did the trick.

Hope that helps you two. I just played a round of ETQW with x.game and i have to say very nice thank a lot mikeym. But I to and having mouse problems its like the pointer is moving on ice and with the lack of options on the new desktop I dont know where to start digging to fix it.

---

### Post by asbjornn on 2008-08-10
It seems to be working just fine, thanks.

And thanks for the script itself.

---

### Post by Unanimated on 2008-08-10
> **rosegarden78 said:**
> It won't matter if your graphics card doesn't have T&L chips to support 3D rendering.

Wow, way to be a fun-killer.

---

### Post by Twilight in Zero on 2008-08-13
Unfortunately, I'm not getting good results from this script. All games run **much slower** through this script.

I have compiz on when I run it, and I'm using the open-source ati driver. Any thoughts?

---

### Post by MemoryDump on 2008-08-14
> **Twilight in Zero said:**
> I have compiz on when I run it, and I'm using the open-source ati driver. Any thoughts?
it shouldn't matter since it's starting it's own X session. As long as your video drivers are configured properly you should be ok.


now.. I have a question regarding using this script... is it possible to start VNC when this new sessions starts? I'd like to be able to connect to this "game" session remotely using VNC.

---

### Post by Ng Oon-Ee on 2008-09-24
Man, I've been trying to do my own script for running games on a separate xserver for ages... Never wanted to go into too much detail with starting up another WM or anything like that, and then I find this script.

Thank you so much mikeym. I'd thank your posts but they're too old :(

---

### Post by mikeym on 2008-09-29
Thanks Ng Oon-Ee, I've not been terribly active on the thread because I've been busy getting out climbing so not so much computer work. :(

MemoryDump I don't see why you couldn't do this. You can easily modify the installed script which is in /usr/local/bin/x.game. 

The bit you'd be interested in is in start() and looks like this:

```
                start-stop-daemon --start --quiet --oknodo --pidfile $PIDFILE --make-pidfile --name xgame --startas /usr/bin/xinit -- $WMPATH -- :1 vt12 &
                sleep 2s
                DISPLAY=:1
                feh --bg-scale "$BGIMAGE" & 
        fi
        PROGRAM=$1
        echo "Program: $PROGRAM"
        if [ "$PROGRAM" != "" ]; then
                execute $*
        fi

```

The start-stop-daemon bit starts a daemon with the new X session (so we can close it later) on virtual terminal 12.

We just use feh to display a background image - otherwise we'd be stuck with black and white hatch boxes. :( 

Then we execute the command that we've passed that's in $*.

This site gives a bit more about VNC and other techniques. 

[http://mandrivausers.org/old_docs/xwin/xnet.html](http://mandrivausers.org/old_docs/xwin/xnet.html)
[http://ubuntuforums.org/showthread.php?t=191564](http://ubuntuforums.org/showthread.php?t=191564)

Good luck!

---

### Post by Rotarychainsaw on 2008-10-05
Hi all,
I wanted to try this since turning off compiz to play games is a pain, but I am having trouble. 

If I run this, my background picture will come up, then all X sessions, and maybe even more will lock up. No key combinations will do anything. I think it may be an error with fglrx due to some odd errors I see before lock. 

```

Oct  5 23:00:01 bj-desktop kernel: [303175.414409] [fglrx] ASIC hang happens.
Oct  5 23:00:01 bj-desktop kernel: [303175.414413] Pid: 1146, comm: Xorg Tainted: P        2.6.24-21-generic #1
Oct  5 23:00:01 bj-desktop kernel: [303175.414416] 
Oct  5 23:00:01 bj-desktop kernel: [303175.414416] Call Trace:
Oct  5 23:00:01 bj-desktop kernel: [303175.414455]  [fglrx:firegl_hardwareHangRecovery+0x1c/0x610] :fglrx:firegl_hardwareHangRecovery+0x1c/0x50
Oct  5 23:00:01 bj-desktop kernel: [303175.414509]  [fglrx:_ZN4Asic9WaitUntil15ResetASICIfHungEv+0x9/0x70] :fglrx:_ZN4Asic9WaitUntil15ResetASICIfHungEv+0x9/0x10
Oct  5 23:00:01 bj-desktop kernel: [303175.414564]  [fglrx:_ZN4Asic9WaitUntil15WaitForCompleteEv+0x6c/0xc0] :fglrx:_ZN4Asic9WaitUntil15WaitForCompleteEv+0x6c/0xb0
Oct  5 23:00:01 bj-desktop kernel: [303175.414620]  [fglrx:_ZN8AsicR60016ASICIdleInternalEN4Asic15idle_WaitMethodE+0xa2/0x1e0] :fglrx:_ZN8AsicR60016ASICIdleInternalEN4Asic15idle_WaitMethodE+0xa2/0x1e0
Oct  5 23:00:01 bj-desktop kernel: [303175.414627]  [zone_statistics+0x7d/0x80] zone_statistics+0x7d/0x80
Oct  5 23:00:01 bj-desktop kernel: [303175.414632]  [file_read_actor+0x138/0x160] file_read_actor+0x138/0x160
Oct  5 23:00:01 bj-desktop kernel: [303175.414642]  [filemap_fault+0x188/0x390] filemap_fault+0x188/0x390
Oct  5 23:00:01 bj-desktop kernel: [303175.414696]  [fglrx:_ZN4Asic7PM4idleENS_15idle_WaitMethodE+0x55/0x90] :fglrx:_ZN4Asic7PM4idleENS_15idle_WaitMethodE+0x55/0x90
Oct  5 23:00:01 bj-desktop kernel: [303175.414751]  [fglrx:_ZN15QS_PRIVATE_CORE7PM4idleEN4Asic15idle_WaitMethodE+0x26/0xf0] :fglrx:_ZN15QS_PRIVATE_CORE7PM4idleEN4Asic15idle_WaitMethodE+0x26/0x50
Oct  5 23:00:01 bj-desktop kernel: [303175.414803]  [fglrx:_ZN10QS_PRIVATE11synchronizeEv+0x29/0x30] :fglrx:_ZN10QS_PRIVATE11synchronizeEv+0x29/0x30
Oct  5 23:00:01 bj-desktop kernel: [303175.414856]  [fglrx:_Z8uCWDDEQCmjjPvjS_+0x3df/0x3720] :fglrx:_Z8uCWDDEQCmjjPvjS_+0x3df/0x1040
Oct  5 23:00:01 bj-desktop kernel: [303175.414902]  [fglrx:firegl_cmmqs_CWDDE_32+0x368/0x410] :fglrx:firegl_cmmqs_CWDDE_32+0x368/0x410
Oct  5 23:00:01 bj-desktop kernel: [303175.414946]  [fglrx:firegl_cmmqs_CWDDE32+0x76/0x300] :fglrx:firegl_cmmqs_CWDDE32+0x76/0x110
Oct  5 23:00:01 bj-desktop kernel: [303175.414992]  [fglrx:firegl_cmmqs_CWDDE32+0x0/0x300] :fglrx:firegl_cmmqs_CWDDE32+0x0/0x110
Oct  5 23:00:01 bj-desktop kernel: [303175.415029]  [fglrx:firegl_ioctl+0x1fb/0x270] :fglrx:firegl_ioctl+0x1fb/0x270
Oct  5 23:00:01 bj-desktop kernel: [303175.415042]  [do_ioctl+0x7d/0xa0] do_ioctl+0x7d/0xa0
Oct  5 23:00:01 bj-desktop kernel: [303175.415048]  [vfs_ioctl+0x220/0x2c0] vfs_ioctl+0x220/0x2c0
Oct  5 23:00:01 bj-desktop kernel: [303175.415051]  [recalc_sigpending+0xe/0x40] recalc_sigpending+0xe/0x40
Oct  5 23:00:01 bj-desktop kernel: [303175.415058]  [sys_ioctl+0x91/0xb0] sys_ioctl+0x91/0xb0
Oct  5 23:00:01 bj-desktop kernel: [303175.415065]  [system_call+0x7e/0x83] system_call+0x7e/0x83
```

---

### Post by slambrick on 2008-10-08
x.start is no longer working for me. It was working perfectly but suddenly (probably after a patch to something) it stopped. I had set a specific desktop backg which no longer appears I have what looks like a x screen but there are no right click menus at all. tried to re-create the install script but it doesn't appear to do anything at all. checked the results from the last post query from sudo apt-get install feh with no change to anythng.
Any ideas???

---

### Post by wardrich on 2008-10-21
For some reason, it just throws me to a black screen and nothing seems to happen... how long should it take to fire up the game?

Also, I find ctrl-alt F1 also brings up a black screen... shouldn't that take you to the terminal?  Maybe it's something gone wonky with my install.


[EDIT] I should probably add that I'm using Gutsy, and I have Fusion installed... and I'm using a Thinkpad R60.  I think it's a Radeon X1600 Mobility card, but I'm not certain... I know it's an ATI Mobility card, though.

---

### Post by spamoom on 2008-11-04
Thanks very much mikeym, this works a treat on Warcraft III. I have one question however, is there a way to span the sound system across the two X servers? 

I'd like to use skype and play music on my main X server and hopefully still hear them when I start the other one.

Regards

Sam  ):P

---

### Post by Mguel on 2008-11-30
Thanks [mikeym]("http://ubuntuforums.org/member.php?u=119068") for the scrypt. But I'm having a problem :(

I was trying to manually use a session with openbox to play UrbanTerror as to have a better fps... but with your script this can be done much more easily.

I have an intel 945gm video card using xserver-xorg-video-intel on kubuntu hardy and intrepid. (BTW I modified te scrypt to install x.game on /usr/bin instead of usr/local/bin).

The problem I have is also present when I tried before manually use another session with openbox to run UrbanTerror: the intel driver is not loaded and the mesa driver is loaded without opengl capacity. I get the following messages:
```

(==) Log file: "/var/log/Xorg.1.log", Time: Sun Nov 30 14:36:04 2008
(==) Using config file: "/etc/X11/xorg.conf"
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(II) Module "ddc" already built-in
(II) Module "i2c" already built-in
```
...
```
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
(II) Module "ramdac" already built-in
(EE) [drm] Could not set DRM device bus ID.
(EE) intel(0): [dri] DRIScreenInit failed. Disabling DRI.
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
Atom 4, CARD32 4, unsigned long 8
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 3: 640 480
Using 4/4/4 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

```

When I first start my computer if I loggin only to the openbox session, I can run UrbanTerror with no problem (using intel driver), but if I run the openbox session as a second session I have the driver problem.

Any help is appreciated since I need to be able to have my usual apps runinig on a kde session.

Cheers,
Mguel

---

### Post by mikeym on 2008-12-08
Yeh, I have the same problem on my PPC with an ATI Raedon 9000. It wouldn't open openGL on the second session. If I remember correctly it has something to do with the graphics card not allowing paging.

---

### Post by KIAaze on 2010-03-06
I don't have sound in the second X server. :(
Any ideas how to fix this?

I'm running Kubuntu 9.10.

It worked well last time I tried it, which might have been under Kubuntu 9.04. I'm not sure exactly when I last used it.

Amarok and Juk also don't have sound in the main X server anymore, while Kaffeine and Gnome apps still do. So it might be a more global problem.

---

### Post by codethief on 2010-03-08
@KIAaze: There seems to be at least one bug involved in this.
As far as I can see, the problem is far more complicated which is why I created a [thread](http://ubuntuforums.org/showthread.php?p=8933392#post8933392) for it.

I'm currently working on this as well and will let you know as soon as I've found a solution. (Hoping you'll do the same, too.)

---

### Post by erjoalgo on 2010-06-08
This is awesome. Thank you for the script, it worked on my system with no problems. Now I can play Heroes of Newerth and switch to my desktop while in game. Also, the game runs much faster too.
Keep up the good work.

---

### Post by 2ndconfused1 on 2010-06-08
i would love to try this script but i dont know what the extension should be to run it :mad:

---

### Post by 2ndconfused1 on 2010-06-08
nevermind i got it. chmod lol i forgot

---

### Post by 2ndconfused1 on 2010-06-08
this topic is old, i dont expect anyone to answer this question but, how do you stop the screen from turning black when i try to run a game through this?

---

### Post by JohnHeikkila on 2010-06-08
I have to say, this is brilliant!
This is what I've always needed!
Thanks!

---

### Post by erjoalgo on 2010-06-08
@[2ndconfused1]("http://ubuntuforums.org/member.php?u=989804")
try running the server without a program argument, 
x.game start
And then in the x server, run your program through the terminal, that will at least give you an error message hopefully

@[mikeym]("http://ubuntuforums.org/member.php?u=119068")
Let me report some problems:
*The icon in the panel disappears when clicked, a menu with an exit option would be nice, but this is minor issue.

*When attempting to exit the 2nd x server, either by
 -right click, exit, in the 2nd X
 -doing x.game stop in the main desktop
 -trying to force stop by ^C from the terminal
My system becomes completely unresponsive and I must to force shutdown.

Also, the output form the terminal always shows some errors, albeit non fatal:

```

user@computer:~$ x.game start
Selecting: start
Starting:
Starting Daemon:


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux ernesto-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=bd127db2-35b1-47ac-93c3-91c07b464e88 ro quiet splash
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Tue Jun  8 20:52:40 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(EE) Failed to load module "dri" (module does not exist, 0)
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
Program: 
ealfonso@ernesto-laptop:~$ The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Symbol map for key <LALT> redefined
>                   Using last definition for conflicting fields
> Warning:          Symbol map for key <RALT> redefined
>                   Using last definition for conflicting fields
Errors from xkbcomp are not fatal to the X server
Openbox-Message: Unable to find a valid menu file "debian-menu.xml"

(gnome-terminal:1653): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed

```

Good work on this script anyway, its been useful for a lot of people

---

### Post by realdude19 on 2010-07-18
I Have been Looking all over for this exact kind of implementation, But I Just cant get a working one.

I went to this guys Blog site and Tried his install... It starts to work but all the Buttons just ding at me when pressed. and no games auto populated the screen. 

I have been messing around with:
```
startx /usr/bin/wine /media/1TBSATA/G-Drive/WorldofWarcraft/Wow.exe -opengl -- :3

``` 

It starts the new X server But No Sound at all and no internet.. thus the game cant connect... 

If I could fix just those two problems I would be Golden.
Any Ideas?

P.s. I Am defiantly seeing a Huge improvement in FPS on the Log in screen and the mouse is SOOO Smooth! I really wish I could login...

---

### Post by KIAaze on 2010-07-19
For sound, try running this in the new X server:
```
ck-launch-session &
```

cf:
[http://ubuntuforums.org/showthread.php?t=1424650](http://ubuntuforums.org/showthread.php?t=1424650)
[http://code.google.com/p/xgamer/issues/detail?id=2&can=1](http://code.google.com/p/xgamer/issues/detail?id=2&can=1) (=>sound problem should be fixed in latest xgamer package)

edit: Just tried xgamer 0.3.0 under Lubuntu 10.04
I confirm that the list remains empty and that adding new entries does not work.
(it opens the "add entry" window, but none of its buttons work, except the close button on the top)
Bug reported: [http://code.google.com/p/xgamer/issues/detail?id=8](http://code.google.com/p/xgamer/issues/detail?id=8)

---

### Post by alexandrius on 2010-08-25
Script is really awesome, but i haven't audio :(
any help?
I've just found out that, audio appears in gnome X not in OpenBox
here's log
```
x.game start
Selecting: start
Starting:
Starting Daemon:


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux alex-desktop 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=217093d2-b7d5-41b5-81d7-e8f8393622ae ro vga=792 quiet quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
Build Date: 21 July 2010  12:47:34PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Thu Aug 26 00:23:23 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
Program: 
alex@alex-desktop:~$ Openbox-Message: Unable to find a valid menu file "debian-menu.xml"

(gnome-terminal:2332): Gtk-CRITICAL **: gtk_accel_map_unlock_path: assertion `entry != NULL && entry->lock_count > 0' failed
```

also some games doesn't start automatically i have to run them from terminal in openbox

---

### Post by Gfurst on 2011-07-03
Hey people, is this thread dead already? That so bad, I really liked the feature and some issues i liked resolved.

Like the above, i don't have audio in the new x-server, instead the audio is directed to main first x-server, must be related to some Pulseaudio server feature.

Secondly, when quiting the openbox, even the first x-server closes, going back to a login screen, this is bad because every running application i had in the first x-server gets shutdown.

And for the last, does it really need to have open box? if i start a new x-server edfault style it just opens an simple console and then i can open any game i want, but still i have the audio issue. Does it really gives a improved performance, wouldn't it give more without openbox?

---

### Post by 42f87d89 on 2012-06-15
If your sound is not working on the other Xsessions run "sudo chmod 777 /dev/snd"

---

### Post by LordEager on 2012-07-24
This thread is quite old, but this script is worth to be more sponsorized, it works like a charm , very good job. (remeber the 775 permission to /dev/snd )

---

### Post by Lunarts on 2012-07-25
Had never thought about this before, interesting

---

### Post by mikeym on 2012-09-22
Hi, 

I recently clicked on this thread for the dust time in a long time and I was surprised to see that people were still using this script. It's good to see that you have fixed many of the problems with it. And you could probably dhow me a thing or two about running second X11 sessions in Ubuntu. 

I did however leave this script in favour of writing a small perl application / script that does a similar job. I've recently done some more work on it and it now works in a much safer way than my original BASH script, by creating new temporary configuration files for *xinit* and *openbox* without touching those already in place.

Maybe if anyone's still using this script or interested in it they could go and give my new one a shot. It's located here:

[http://code.google.com/p/xgamer/](http://code.google.com/p/xgamer/)

I'll repost some of this on my initial post.

(**[COLOR="Red"]edit[/COLOR]**) Apparently I don't have the access rights to edit my original post any more. If anyone can grant me that it would be appreciated.

---

