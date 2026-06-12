---
title: "Bash script I just cant get to work... logic flaw?"
date: 2009-01-10
forum: General Help
---

### Post by gettensome on 2009-01-10
Hers the deal, I want to start a launcher that will switch my window manager from Compiz to Metacity, then watch my processes to know when World of Warcraft is no longer runner and automatically switch back to Compiz.  I think it should be a pretty simple affair,  and I can get everything to work except when it's supposed to switch back to Compiz.

This is what I have narrowed it down to:

```
#!/bin/sh
IS_WOW_RUNNING='1'						# Test Viable to wait for user to exit game. 1 = running, 0 = not 
												
compiz-switch					 		# Changes window manager to metacity to facilitate opperation	
env WINEPREFIX="/home/chris/.wine" wine "C:\Program Files\World of Warcraft\Wow.exe"
						

while [ $IS_WOW_RUNNING = '1' ] do 				# Begins checking for wow is list of processes 

if [ ps -ax | grep -v grep | grep "World of Warcraft" ]		# Scanning for any process containing WoW in the name
	then							#
	IS_WOW_RUNNING='1'					# Found that WoW is running
	
	else							#
	compiz --replace				  	# Resets Window Manager to original state
	IS_WOW_RUNNING='0'					# WoW no longer running, terminates while loop
fi	
done


```

---

### Post by Dr Small on 2009-01-10
I'm no professional with metacity nor compiz, since I use neither, but isn't it supposed to be "metacity --replace" ?

---

### Post by gettensome on 2009-01-10
compiz-switch is an application that just swaps you to another install window manager.  The reason why I use it is when I use 'metacity --replace' it does just that,  but it will not execute the next line of code.

---

### Post by mgol on 2009-01-10
> **gettensome said:**
> when I use 'metacity --replace' it does just that,  but it will not execute the next line of code.

You can always run in it the background, by adding ' &' at the end of Your command.

---

### Post by schilcha on 2009-01-10
Have you verified that 
```
ps -ax | grep -v grep | grep "World of Warcraft" ]
```
in the if-statement will actually only find the wow-process started above? Have a look at the output of this statement, when you're expecting your script to switch back to compiz. Maybe there's another process with "World of Warcarft" somewhere in the name or parameter.

If this is the case, you can either try to be more specific in the grep-statement or store the process-id of the wine-process started at the beginning of the script. The bash-variable $! (see "Special Parameters"-section in the bash-man-page) can help you there. Please note that I've never used $! with wine. I've no idea how many wine-process are launched and how long they persist.

BTW: I'd add a sleep-statement (for 2 or 5 secs) at some point in the while-loop, to make sure your script will not eat up your CPU.

Good Luck,
   schilcha

---

