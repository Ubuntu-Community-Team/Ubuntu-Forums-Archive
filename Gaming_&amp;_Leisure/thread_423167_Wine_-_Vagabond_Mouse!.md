---
title: "Wine - Vagabond Mouse!"
date: 2007-04-25
forum: Gaming &amp; Leisure
---

### Post by Sugi on 2007-04-25
Well, my problem is within wine,  when i boot up a game, i have problems with the mouse going off game, and I can see some of the desktop, but wine changes resolution to the game.  I'm still able to see the desktop where the game is not cover it up.   
terminal>winecfg>Graphics Tab> check "Allow DirectX apps to stop the mouse leaving their window".  
It's checked, but I am still about to scroll off the window appication.  How should I go about to fix this problem?

---

### Post by AndrewRiedi on 2007-04-25
Is it possible to make the game resolution the same as your desktop resolution?  Or maybe make a script that calls xrandr before running the game?  I don't know, just ideas.

---

### Post by duncan_nz on 2007-04-25
I've had the same problem with steam based games, the mouse in wine sometimes loses focus when I'm playing steam based games for example, and in the game I'll just head off without stopping in the last direction that I was going in before I lost mouse focus.

Its only a second long outage, but its annoying nonetheless.

I never had this problem with previous versions of wine (I'm using the latest).

Also I found that if you turn down hardware acceleration in the mouse settings in ubuntu, it reduces the chances of this mouse problem happeneing (note that it still happens, just less often).

---

### Post by cogadh on 2007-04-26
If you enable the "Emulate a virtual desktop" option under "Graphics" in winecfg, then set it for a window size that will fit on your desktop, that will prevent Wine from resizing your actual desktop and will allow the mouse to stay "inside the box".

Alternatively, you could create a simple launch script that will launch the game in its own X session. Here's a smple one I use for launching KOTOR (borrowed the idea from one for WoW):
```
#!/bin/sh

# Launch new X session on display 3
X :3 -ac & 
nvidia-settings --load-config-only

# Force the system to break for 2 seconds
sleep 2 

# Launch KOTOR
DISPLAY=:3 /usr/X11R6/bin/wine /media/cdrom0/autorun.exe 
```
Technically, it will work for any cd installed game that uses "autorun.exe" for a launcher. You can modify the final line to accomodate any game executable, I would imagine.

EDIT - Almost forgot, if you try the launch script, don't use the "Emulate a virtual desktop" at the same time, it ain't pretty.

---

### Post by Sugi on 2007-04-26
cogadh, i've tryed Emulate a virtual desktop, but all it changes is having the actually desktop reisze to the game.  wine changes the "virtual desktop" to the game'resolution.  the game's resolution is smaller than my desktop resolution because i have a widescreen laptop.  :-/

and forgive me if this is a noobie question, but where would i add that lauch script codes at??

---

### Post by cogadh on 2007-04-26
[SIZE="4"][COLOR="DarkRed"]Creating and using an X Server/Wine launch script[/COLOR][/SIZE]

First you need to create the script. From the terminal, do the following:
```
nano launcher.sh
```
Copy the text below and paste it into the terminal with either the middle mouse button or by clicking on Edit->Paste. Take out the nVidia settings portion if you don't have an nVidia card and modify the application paths to match your game.
```
#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac & nvidia-settings --load-config-only

# Goto game dir (modify as needed)
cd "$HOME/.wine/drive_c/Program Files/Game/Directory/"

# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "C:/Program Files/Game/Directory/game.exe"
```
Save the file in your home directory by pressing CTRL-O, hit enter then CTRL-X to exit. 
Next, make your script executable with this command:
```
chmod +x ~/launcher.sh
```

Launch the game by doing this from a terminal:
```
sh launcher.sh
```
OR
```
./ launcher.sh
```
When you are done playing, do a CTRL-ALT-BACKSPACE to get back to the desktop.

**ALTERNATE INSTRUCTIONS**
If your game doesn't work, or if you want to try and squeeze some additional performance out of the game, follows these additional steps to try running it without your default X session still running:

Uncomment (remove "#") the "sudo /etc/init.d/gdm stop" line in the script and save it. If you use KDE, uncomment the "sudo /etc/init.d/kdm stop" and save the script. Close all open applications and switch to the console by pressing CTRL-ALT-F1. Log into the console and run the script:
```
sh launcher.sh
```
OR
```
./ launcher.sh
```
You will be prompted for your password and your game will launch in its own X session, without the Gnome or KDE window manager getting in the way. If the script complains that you don't have permission to start the X session do this:
```
nano launcher.sh
```
Then modify the X server launch line of the script to read:
```
sudo X :3 -ac & nvidia-settings --load-config-only
```
[INDENT]NOTE - You can avoid having to modify the script by editing the Xwrapper.config file to allow normal users X access. Open the /etc/X11/Xwrapper.config file in a text editor using sudo, then change the "allowed_users=console" entry to "allowed_users=anybody".[/INDENT]

Once you are finished playing, either reboot or do a CTRL-ALT-BACKSPACE to get back to the terminal and restart your X server and desktop by doing this:
```
sudo /etc/init.d/gdm start
```
If you use KDE, do this instead:
```
sudo /etc/init.d/kdm start
```
The desktop should come right back up immediately, if it doesn't just type "startx".

---

### Post by YokoZar on 2007-04-27
Seriously, download the newest Wine package (0.9.36)

There was a problem with the 0.9.35 ones that I think was causing this.

---

### Post by Jarn on 2007-04-27
> **cogadh said:**
> ```
#!/bin/sh

# Launch new X session on display 3
X :3 -ac & 
nvidia-settings --load-config-only

# Force the system to break for 2 seconds
sleep 2 

# Launch KOTOR
DISPLAY=:3 /usr/X11R6/bin/wine /media/cdrom0/autorun.exe
```Is it possible to make the X session that it starts up a different resolution than my desktop? My desktop is 1280x960 and I can't run any games that size, so nothing will be fullscreen until I can do that.

---

### Post by Sugi on 2007-04-28
after updating to wine 0.9.36,  it still didn't help it. >.<

---

### Post by cogadh on 2007-04-28
> **Jarn said:**
> Is it possible to make the X session that it starts up a different resolution than my desktop? My desktop is 1280x960 and I can't run any games that size, so nothing will be fullscreen until I can do that.

Yes, but I've never tested this:
```
X :3 -ac & 
nvidia-settings --load-config-only
xrandr -s 1024x768
```

You can change the resolution to whatever you need, but it has to be a resolution that is already configured in your xorg.conf.

---

