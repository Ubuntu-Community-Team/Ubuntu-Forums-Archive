---
title: "Remove flicker from games"
date: 2009-01-27
forum: Gaming &amp; Leisure
---

### Post by XanTrax on 2009-01-27
I do not know if this is the right section for this.  Please read below before moving it as my intentions are that this is a tip/tutorial put into a script.

I have noticed that with a lot of 3D rendering applications, primarily games, have some what of a hard time running on Ubuntu with or without wine without some form of flickering while compiz is running.  Most notably, ATI fglrx with compiz enabled running a game, whether wine is used or not, will almost inevitably flicker.  

This script will:

- Check to make sure you have compiz running in the first
- Check to make sure you have metacity installed
- Accept arguments for the application/game command that you are running, wine and nowine (used as written)
- Kill compiz
- Replace compiz with metacity
- Run the game/command/application
- Restore compiz after the game ends


Please let me know what you think


```

#!/bin/bash
 
#pre-reqs
 
#Check arguments of command
if [ -z "$1" ] || [ -z "$2" ]; then
	echo ""
	echo ""
	echo "Usage is startgame <wine> <game_path>"
	echo ""
	echo "<wine> argument accepts:"
	echo "        -wine : The game requires wine"
	echo "        -nowine : The game does not require wine"
	echo ""
	echo "<game_path> is path to the game when wine is used or accepts the command for linux games"
	echo ""
	echo ""
	echo "Example (Windows Game with wine): "
	echo "             startgame -wine \"/home/user/.wine/drive_c/Program Files/EAGames/game.exe\""
	echo ""
	echo "Note: If your windows game takes arguments, put it inside the quotes after the .exe (Ex: \"game.exe -quickstart\")"
	echo ""
	echo "Example (Linux game, no wine):"
	echo "             startgame -nowine frozenbubble"
	echo ""
	echo ""
 
	exit 0
fi
 
#Check if metacity exists
function checkmetacity {
	meta=`which metacity`
	if [ -n "$meta" ]; then
		echo "Metacity found."
	elif [ -z "$meta" ]; then
		echo "Metacity NOT found."
		exit 0
	fi
}
 
#Check if compiz exists
function checkcompiz {
	comp=`which compiz`
	if [ -n "$comp" ]; then
		echo "Compiz found."
	elif [ -z "$comp" ]; then
		echo "Compiz NOT found."
		exit 0
	fi
}
 
function checkwine {
	winecmd=`which wine`
	if [ -n "$winecmd" ]; then
		echo "Wine found"
	elif [ -z "$winecmd" ]; then
		echo "Wine not found.  Can not start game."
		exit 0
	fi
}
 
#Call the functions
checkmetacity
checkcompiz
 
 
#Start the magic
 
count=`ps -A | grep -ic compiz`
if [ $count -gt 0 ]; then
	echo "*** NOTIFICATION: Compiz found. Replacing with metacity. ***"
	echo "*** NOTIFICATION: Killing all instances of Compiz. ***"
 
	#Kill Compiz
	killall compiz.real
	if [ $? -eq 0 ]; then
		echo "*** NOTIFCATION: Killed compiz successfully. ***"
		echo "*** NOTIFCATION: Replacing with metacity. ***"
 
		#Run metacity in its place
		metacity --replace &
		if [ $? -eq 0 ]; then
			echo "*** NOTIFCATION: Metacity ran successfully. ***"
 
			# Run game
			if [ $1 = "-wine" ]; then
				checkwine
				wine $2
			elif [ $1 = "-nowine" ]; then
				$2
			fi
 
			#Return compiz
			compiz --replace &
			sleep 1
			exit 0
		else
			echo "*** WARNING: Could not run metacity. EXITING! ***"
			exit 0
		fi
	else
		echo "*** WARNING: Compiz was not killed successfully. ***"
		exit 0
	fi
elif [ $count -eq 0 ]; then
	echo "Compiz not found. Exiting!"
	exit 0
fi
 
exit 0
```

---

