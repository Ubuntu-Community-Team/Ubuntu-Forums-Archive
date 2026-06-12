---
title: "Playing games with minimal or without Windows Manager. How?"
date: 2011-09-28
forum: Desktop Environments
---

### Post by Panties on 2011-09-28
Hi team, I got this below. I try to do it, but I don't really understand how to do it. Could any Ubuntu Guru Gamer, explain how to do this? Here's a copy and paste from the link.

> 
[http://linux.about.com/od/gmr_howto/a/hwtgmr05t01.htm](http://linux.about.com/od/gmr_howto/a/hwtgmr05t01.htm)
**4.2. Playing Games In X Without a Window Manager**

 When playing a game under X, you should consider starting X without a  window manager             (WM).  Heavyweight WMs, like Enlightenment, or  full-blown desktop environments like GNOME or             KDE, may produce a  noticeable slow down.  Even lightweight WMs, like twm, rob your CPU of              clock cycles (and in twm's case, even full screen games will have a  frame around the window).             Running a game without a WM or DE depends  on how you access X.  If you usually log in to a             Virtual Console and  start X with "startx" try the following: 
 Modify ~/.xinitrc , which tells X what to run upon starting.  Here             is what my .xinitrc looks like:
 
   
 #quake3 +set r_gldriver libGR.so.1  #exec ut  #lsdldoom -server 2  #exec tribes2  exec /usr/bin/enlightenment                    
You'll usually see a window or desktop manager being executed  from this file (GNOME or             KDE).  Comment out the lines containing the  WM or desktop manager with a pound sign (#) and             place your game on a  new line with any command line arguments you want to pass.  If the game              is not located in your $PATH, give its full path name.
 If you log directly into X using gdm, then things are a little  different. These             instructions are for gdm 2.4 or greater. They *may*  work with kde, but I cannot say for             certain.
 First, check your gdm.conf  (usually in /etc/X11/gdm  or /etc/gdm )             file for a line that says begins "SessionDesktopDir=blah ".  One of the             directories listed as options should be "/usr/share/xsessions ", and is the directory which will be used in             this example.  As root, change to the "/usr/share/xsessions " directory and take a look at its contents.             It should contain some .desktop  files, each corresponding to an entry             you'll see in gdm's Session menu, e.g gnome.desktop ,             enlightenment.destop .  This example will show you how to log in to Doom3.             Copy any of the desktop files to "doom3.desktop " and open the new file in             your favourite text editor.  The file will  be full of alternative languages, so cut out             everything you don't  want and make the file look like this:
 
   
 [Desktop Entry]  Encoding=UTF-8  Name=DOOM III  Comment=iD's Doom III  #if game is not in path, remember to put the full path here  Exec=/usr/games/doom3/doom3  # no icon yet, only the top three are currently used  Icon=  Type=Application                    
Save the file and log out of your window manager.  At the gdm login screen, you should             now see "DOOM III " as an option in "Sessions".  Naturally you can add a             .desktop file for each game you have installed

Anyone knows how to do it? @@

---

### Post by juancarlospaco on 2011-09-28
I got a less complex approach, 
i use an icon to kill all the unneeded processes and then start the game,
make a new launcher on desktop, and on command, 
replace GameExecutableGoesHere with your Game Executable full path, use something like this:

killall --verbose --regexp ubuntuone-syncdaemon bamfdaemon zeitgeist-daemon zeiitgeist-datahub gnome-power-manager gnome-screensaver notify-osd bonobo-activation-server gvfsd ssh-agent nm-applet gvfsd* && GameExecutableGoesHere

Try killing more system services, one by one, and try if the game still runs fine,
if runs fine add it to the list of killed services, good luck . . .

---

