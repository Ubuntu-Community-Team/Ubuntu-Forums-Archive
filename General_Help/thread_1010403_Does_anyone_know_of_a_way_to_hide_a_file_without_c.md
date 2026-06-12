---
title: "Does anyone know of a way to hide a file without changing the filename to include a ."
date: 2008-12-13
forum: General Help
---

### Post by bobleny on 2008-12-13
Does anyone know of a way to hide a file without changing the filename to include a .(dot)?

I've searched yahoo and understand the whole don't do not dots.....  :confused:

A game that I play keeps a file in my home directory. I don't want to see it there and I have no way of changing the file location. If I rename the file to include the .(dot), the game puts a new file there.

So, all I want to do is hide the one file. Any ideas?

Thanks!
[Kubuntu 8.04]

---

### Post by drs305 on 2008-12-13
This works for nautilus in ubuntu. You will have to try it with your file browser in kubuntu:

Make a text file called .hidden in the same directory as the folder or file you want to hide. Open the file and enter the name of any file(s) or folder(s) you want hidden. If you have the file browser set to hide hidden files, and files listed in .hidden will not be shown.

Example. In /media/data I have created a file called .hidden
The contents of .hidden  contain on a separate line:  lost+found
When I have the View Hidden Files disabled, I do not see .hidden or the 'lost+found' folder

---

### Post by bobleny on 2008-12-13
Thank you for the quick reply, but of course it wouldn't work in Konqueror...

By the way, I am using Konqueror as my file manager. I can't stand dolphin...

Any other ideas?

---

### Post by Zorael on 2008-12-13
I'd write a wrapper script that renames (unhides) the file, starts the game, and then hides (renames) the file upon exiting. Name it 'game**.start**' or something like that; so, pacman.start, otrspod.start, digdug.start, etc. Naturally you'd need to start the game via this script instead of the normal executable.

```
#!/bin/bash

if [ -e $"~/[COLOR="DeepSkyBlue"]**.**filename[/COLOR]" ]
then
	# hidden file exists, rename
	mv ~/[COLOR="DeepSkyBlue"]**.**filename[/COLOR] ~/[COLOR="DeepSkyBlue"]filename[/COLOR]
fi

# start the game
[COLOR="Lime"]startgame[/COLOR]

# game is not running anymore
if [ -e $"~/[COLOR="DeepSkyBlue"]filename[/COLOR]" ]
then
	# file exists, rename to hide
	mv ~/[COLOR="DeepSkyBlue"]filename[/COLOR] ~/[COLOR="DeepSkyBlue"]**.**filename[/COLOR]
fi
```
The above only works if the game doesn't return terminal control upon starting it, though. In that case, it simply doesn't proceed to the "# game is not running anymore" line until startgame ends. In the case it launches itself as a child process, you'd need to do something like this.
```
#!/bin/bash

if [ -e $"~/[COLOR="DeepSkyBlue"]**.**filename[/COLOR]" ]
then
	# hidden file exists, rename
	mv ~/[COLOR="DeepSkyBlue"]**.**filename[/COLOR] ~/[COLOR="DeepSkyBlue"]filename[/COLOR]
fi

# start the game
[COLOR="Lime"]startgame[/COLOR]

# wait for [COLOR="SeaGreen"]game process[/COLOR] to end
while true
do
	if [ ! "$(pidof [COLOR="SeaGreen"]gameprocessname[/COLOR])" ]
	then
		# game is not running anymore
		if [ -e $"~/[COLOR="DeepSkyBlue"]filename[/COLOR]" ]
		then
			# file exists, rename to hide
			mv ~/[COLOR="DeepSkyBlue"]filename[/COLOR] ~/[COLOR="DeepSkyBlue"]**.**filename[/COLOR]
		fi

		# break loop to end script
		break
	else
		# game still running, wait a bit and probe again, tweak [COLOR="Red"]number[/COLOR] as you wish
		sleep [COLOR="Red"]10[/COLOR]
	fi
done
```

Obviously you'd need to find out the name of the game process in the second case, and of course replace [COLOR="DeepSkyBlue"]filename[/COLOR] and [COLOR="Lime"]startgame[/COLOR] with the correct names and commands. I'm writing this off the top of my head but should work.

---

### Post by bobleny on 2008-12-13
Wow, thanks for your hard work and help, but that is not quite the solution I was looking for.

I don't know....

I just hate stupid files like that floating around. There just in the way and interrupt the flow of things....

I guess if there is no other ideas I will.... 


Thanks for everyones help!

---

### Post by lensman3 on 2008-12-13
It might be simpler to create another user for running the game.  Setup another directory and user.  Set the privileges for the directory to be very restrictive.  Then when you want to run the game start a text window.

Run the command "su newuser".  Do a "cd" and the cd will take you to the newuser directory.  Type in the game name an run it from there.  The game will be run as the "newuser".  If you don't believe me, then run the command "whoami" to see current user.

The only way someone could tell if you are running as another user is to execute the program "who" or "finger".  The program "last" doesn't even list the newuser.

---

