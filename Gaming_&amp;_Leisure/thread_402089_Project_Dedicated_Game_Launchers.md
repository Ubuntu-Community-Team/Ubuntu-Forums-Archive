---
title: "Project: Dedicated Game Launchers"
date: 2007-04-05
forum: Gaming &amp; Leisure
---

### Post by justin whitaker on 2007-04-05
Ok, now I need some real guru help.

When I get down to a gaming session, I really don't need a desktop at all. I would like to be able to logout (or reboot), login to console, and be able to run a dedicated X server for the games that I play.

I saw this script here on the help wiki for World of Warcraft which looks like a step in the right direction:

> #!/bin/sh
 
X :3 -ac &   # Launches a new X session on display 3 
cd "~/.wine/drive_c/Program Files/World of Warcraft"   # Goto WoW dir 
sleep 2   # Forces the system to have a break for 2 seconds 
DISPLAY=:3 /usr/X11R6/bin/wine WoW.exe -opengl   # Launches WoW

So here comes the questions!

> X :3 -ac &   # Launches a new X session on display 3 

This launches a new X session for any game. Not sure what the -ac flag means, but that looks to be the gist of it. Can you change the X: 3 to any display? Say X: 1?

> 
cd "~/.wine/drive_c/Program Files/World of Warcraft"   # Goto WoW dir 

Whichever game you are loading with this script, you point this like to the install directory. So you could do this with Crossover or Cedega?

> sleep 2   # Forces the system to have a break for 2 seconds 

This is self explanatory, but why do you need to force a system sleep? 

> DISPLAY=:3 /usr/X11R6/bin/wine WoW.exe -opengl   # Launches WoW

I don't get why the line above points to the install directory, but the last like points to /usr. 

Shouldn't the line read: Display=:(1-6) ~/.wine/drive_c/Program Files/World of Warcraft?

And how do I allow a login to terminal/console?

Thanks for the assist!

---

### Post by hikaricore on 2007-04-05
> **justin whitaker said:**
> 
This launches a new X session for any game. Not sure what the -ac flag means, but that looks to be the gist of it. Can you change the X: 3 to any display? Say X: 1?


Easy enough to explain:

```
[hikaricore@key:~ (699.8 Mb)]$ sudo X --help
Unrecognized option: --help
use: X [:<display>] [option]
-a #                   mouse acceleration (pixels)
**-ac**                    _disable access control restrictions_
```

As for the display, yes you could change it to any you wanted.

> **justin whitaker said:**
> 
Whichever game you are loading with this script, you point this like to the install directory. So you could do this with Crossover or Cedega?


There isn't any need to do this with cedega as it has a GUI front end.  I guess you could, but if you're using cedega it kinda defeats the point.

> **justin whitaker said:**
> 
This is self explanatory, but why do you need to force a system sleep? 


Gives X a chance to start before launching an application.  This process is not instant.

> **justin whitaker said:**
> 
I don't get why the line above points to the install directory, but the last like points to /usr. 

The game needs to be run from it's install directory, the last line is pointing to the location of the wine binary.  This isn't really nessicary in most cases, as you can just use:

DISPLAY=:3 **wine** WoW.exe -opengl # Launches WoW


> **justin whitaker said:**
> 
Shouldn't the line read: Display=:(1-6) ~/.wine/drive_c/Program Files/World of Warcraft?

No.

> **justin whitaker said:**
> 
And how do I allow a login to terminal/console?


Hit ctrl+alt+f1.  This brings you to a console.  Login here and for best results, shutdown your other X gui session(s).

```
sudo /etc/init.d/gdm stop
```

or if you use kubuntu:

```
sudo /etc/init.d/kdm stop
```

I've found this greatly improves gaming as nearly nothing else but system services will be running.

Then run your launcher and you're good to go.

After you're done gaming, hit ctrl+alt+backspace to close your open X session and restart gdm or kdm as such:

```
sudo /etc/init.d/gdm start
```

or:

```
sudo /etc/init.d/kdm start
```

---

### Post by justin whitaker on 2007-04-05
hikaricore, thanks a bunch!

As for Cedega/Crossover, you can run both from command line, so you can probably get the same performance increase without loading the GUI (substitute cxoffice/cedega for wine).

So if I am using Crossover, I need to point to where Crossover is installed in the last line, right?

---

### Post by invanitas on 2007-04-25
I've been using the same (modified) script to launch dedicated X sessions for games for awhile.  The performance boost is pretty great but I have a couple problems:

1)  I can't seem to take system resources from a new session once it's been declared with out crashing the new session.  Eg, I launch a game on a dedicated session, switch back to the gnome session loaded on startup and open firefox and the new session crashes to grey.  If I open firefox before launching the new session, everything is fine and I can use both simlutaneously (with a fps hit in the game, of course).

2) I can't seem to start 2 sessions with a client on each.  If I launch the 1st new session with the client and then try to launch a new session with

```
X :3 -ac &   # Launches a new X session on display 3 
nvidia-settings --load-config-only
sleep 2   # Forces the system to have a break for 2 seconds
DISPLAY=:3 clientcommand &  # Launches client on 3
sleep 2
X :2 -ac &   # Launches a new X session on display 2 
```

 I get an AGP access error and the launch fails.  I can launch both new sessions first with

```
X :2 -ac &   # Launches a new X session on display 2 
nvidia-settings --load-config-only
sleep 2   # Forces the system to have a break for 2 seconds
X :3 -ac &   # Launches a new X session on display 3 
nvidia-settings --load-config-only
```

but then assigning a client to x display (2 or 3) with

```
DISPLAY=:x clientcommand
```

doesnt' seem to have any effect.

I've tried doing these commands at a terminal one at a time and at no point do I get errors and at no point do I get a client on either display.

Does anyone have any thoughts about either of these two problems?
Thanks

---

