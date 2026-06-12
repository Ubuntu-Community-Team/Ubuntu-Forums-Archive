---
title: "Anyone have a simple and easy to follow guide on installing and using Openbox"
date: 2009-12-18
forum: Desktop Environments
---

### Post by EddDoubleD on 2009-12-18
I want o use this theme
[http://gnome-look.org/content/show.php/murrinaGSM+GTK+%2B+Openbox+Theme?content=54865](http://gnome-look.org/content/show.php/murrinaGSM+GTK+%2B+Openbox+Theme?content=54865)
as it is GSM a theme I used to love back when I used windows/litestep years ago and I miss so very much and the GTK one just doesn't look right but this Openbox one looks like the litestep one I had and I want to use it so bad but when I installed openbox and used it all got was a black screen and a right click menu and the guide I was using kinda confused me. So does anyone have simple and easy to follow guide I can use. I'm running Ubuntu 9.04.

---

### Post by ankspo71 on 2009-12-18
Hi,

The easiest wat to install ' openbox ' is to install it through Synaptic Package Manager. To install themes I suggest also installing ' obconf ' too. The ' obmenu ' package is a graphical menu editor that can make menu editing much easier. You will have to run ' obmenu ' in the terminal because there shouldn't be a menu entry for it in the openbox menu, unless you add it there yourself.   ' tint2 ' is a taskbar that can be used with Openbox. I think ' nitrogen ' will work good for a utility to draw the wallpaper on the desktop. 

obconf:
[http://icculus.org/openbox/index.php/ObConf:About](http://icculus.org/openbox/index.php/ObConf:About)

Have you tried out CrunchBang Linux? If you haven't, you could check it out to see what they used to make a complete functioning openbox desktop. Crunchbang is based on ubuntu too, except uses openbox instead of gnome.

Hope this somehow helped.

---

### Post by EddDoubleD on 2009-12-18
How do I use the menu editer as I who like to brower my folders.

---

### Post by EddDoubleD on 2009-12-18
also how do I get tint2 to start?

---

### Post by ankspo71 on 2009-12-18
Hi,

if you have obmenu installed, right click on the desktop and click on "terminal emulator"
In the terminal type:
```
obmenu
```

When obmenu opens up, look for the first entry called "openbox 3".
Click on that little black triangle next to it.... this will open the menu to full view.

The next part is a little tricky...
Click on any of the menu entries below "openbox 3"
Next, click on the "New Item" button.
THis will create a new entry inside the "openbox 3" menu.
Now give the new item a label (name)... Use "Menu Editor"
now give the new item a execute (command)... Use " obmenu "
Now click on the save button on the top of obmenu.
Close obmenu, then check your menu for your new menu entry.


The next part part is to open your home folder.
If you already have gnome installed, 
you can use nautilus as your file manager, until you find one that you like.
To use nautilus, click on "terminal emulator" again and type:
```
nautilus /home
```
This will open up the gnome file manager.
(note you can always create a menu entry for this.)
(note#2 - using nautilus in openbox gives me problems so I recommend installing one of the file managers below.

Most people using openbox like using 'pcmanfm' file manager (not nautilus), which is very good, but I am really starting to like 'thunar' too.

Thunar can be started by typing thunar in the terminal.
Pcmanfm can be started by typing pcmanfm in the terminal.

Hope this helps.

---

### Post by ankspo71 on 2009-12-18
you can start tint2 by typing tint2 in the "terminal emulator".

I don't know how to autostart programs in openbox though. :(  I don't have enough experience with openbox to know that.

---

### Post by SushiR on 2009-12-18
[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

---

### Post by MooPi on 2009-12-18
Openbox is very different from Gnome and I've found that nautilus doesn't play well with it. You'll probably want to use another file manager as well, I use pcmanfm. How familiar are you with Openbox ? How about a a desktop panel ? I use lxpanel for simplicity but there are others as well as dock style.

---

### Post by MooPi on 2009-12-18
Here is a screen shot of a simple openbox.
[http://i559.photobucket.com/albums/ss36/MooPii/2009-12-18-133101_1440x900_scrot.png](http://i559.photobucket.com/albums/ss36/MooPii/2009-12-18-133101_1440x900_scrot.png)

An even simpler . no panel or menu. I actually love this setup.
[http://i559.photobucket.com/albums/ss36/MooPii/Ubuntu-Lite/2009-12-10-115646_1440x900_scrot.png](http://i559.photobucket.com/albums/ss36/MooPii/Ubuntu-Lite/2009-12-10-115646_1440x900_scrot.png)

This is the script for  autostart.sh. Drop this file in .config/openbox  You will want to change the start programs to fit what you have installed. If you will look at the last line of the script you will see it has been commented with #. # symbol denotes that you don't want that portion to run. To get it to fun just uncomment the # symbol and it will start on next reboot.

> 
# Run the system-wide support stuff
.$GLOBALAUTOSTART

#Programs to launch at startup
feh --bg-scale ~/background/deepblue.jpg &
lxpanel &
oclock -transparent &
#xterm -e htop &

---

### Post by EddDoubleD on 2009-12-18
I really getting the hang of this I pretty much understand the basics of what I need to do now how do I get a background and a clock?

---

### Post by EddDoubleD on 2009-12-18
I really getting the hang of this I pretty much understand the basics of what I need to do now how do I get a background and a clock?

---

### Post by MooPi on 2009-12-18
I may have miss spoke about Nautilus. It works but will draw the desktop if not configured correctly. I don't even mess with nautilus on my computer, as it is never installed.

---

### Post by EddDoubleD on 2009-12-18
I installed pcmanfm pretty fast.

---

### Post by EddDoubleD on 2009-12-18
How do I get to my trash in pcmanfm?

---

### Post by MooPi on 2009-12-18
A really nice feature of pcmanfm is the F4 key will start a terminal in whatever folder you happen to be viewing. It also has tabbed configuation.

---

### Post by MooPi on 2009-12-18
Okay you've stumped me because I don't use a trash bin. Looking for an answer right now.
Doesn't come with one and seems MIA. don't delete unless you really mean it !!

---

### Post by EddDoubleD on 2009-12-18
interesting

---

### Post by EddDoubleD on 2009-12-18
what do you use?

---

### Post by MooPi on 2009-12-18
> what do you use?     Not sure of question.

---

### Post by EddDoubleD on 2009-12-18
You said you don't use a trash bin.

---

### Post by MooPi on 2009-12-18
That is correct. If I delete something I want it gone. If I have a file that's lost it's value or may be needed later I have an alternative. I create a folder for archive and dump things in there for safe keeping.

---

### Post by EddDoubleD on 2009-12-18
ok so how do I get a wallpaper up?

---

### Post by MooPi on 2009-12-18
You can install a couple of programs. The one I use is called "feh" and it was listed in my autostart.sh script. The other is called nitrogen and has a nice graphical interface. let me know which one you choose and I'll tell you how to get it to restore after each reboot

---

### Post by EddDoubleD on 2009-12-18
How do I use feh?

---

### Post by MooPi on 2009-12-18
To start, open a terminal. in terminal type ```
feh  --bg-scale ~/path_to_file
```Or you can go to wherever you keep your background pictures and open one with feh. Then right click and a menu will drop down. Scroll down to background and choose how you want it displayed. Now for adding it to your autostart.sh here is an example of how I have it listed . ```
feh --bg-scale ~/background/deepblue.jpg &
```Hope that helps.

---

### Post by EddDoubleD on 2009-12-18
does the background stay or do I have to do it everytime I reboot?

---

### Post by MooPi on 2009-12-18
If you include it in your autostart.sh file , it will come back. If you want to change your background to something else just amend the autostart. If you can show me how you've written your autostart.sh.

---

### Post by EddDoubleD on 2009-12-18
how do I do that?

---

### Post by MooPi on 2009-12-18
This is my autostart ```
# Run the system-wide support stuff
.$GLOBALAUTOSTART

#Programs to launch at startup
feh --bg-scale ~/background/deepblue.jpg &
lxpanel &
oclock -transparent &
xterm -e htop &
```The first three lines are just instructions. Just add the applications you want to start below the third line. always remember to end each line with "&".
Open a text editor and copy and paste the first three lines. Add appropriate apps and save to ```
~/.config/openbox/autostart.sh
```

---

### Post by EddDoubleD on 2009-12-18
# This shell script is run before Openbox launches.
# Environment variables set here are passed to the Openbox session.

# Set a background color
BG=""
if which hsetroot >/dev/null; then
    BG=hsetroot
else
    if which esetroot >/dev/null; then
	BG=esetroot
    else
	if which xsetroot >/dev/null; then
	    BG=xsetroot
	fi
    fi
fi
test -z $BG || $BG -solid "#303030"

# D-bus
if which dbus-launch >/dev/null && test -z "$DBUS_SESSION_BUS_ADDRESS"; then
       eval `dbus-launch --sh-syntax --exit-with-session`
fi

# Make GTK apps look and behave how they were set up in the gnome config tools
if test -x /usr/libexec/gnome-settings-daemon >/dev/null; then
  /usr/libexec/gnome-settings-daemon &
elif which gnome-settings-daemon >/dev/null; then
  gnome-settings-daemon &
# Make GTK apps look and behave how they were set up in the XFCE config tools
elif which xfce-mcs-manager >/dev/null; then
  xfce-mcs-manager n &
fi

# Preload stuff for KDE apps
if which start_kdeinit >/dev/null; then
  LD_BIND_NOW=true start_kdeinit --new-startup +kcminit_startup &
fi

# Run XDG autostart things.  By default don't run anything desktop-specific
# See xdg-autostart --help more info
DESKTOP_ENV=""
if which /usr/lib/openbox/xdg-autostart >/dev/null; then
  /usr/lib/openbox/xdg-autostart $DESKTOP_ENV
fi

Where so I put it?

---

### Post by MooPi on 2009-12-18
Okay I'm stumped but working on this. Is that the theme you posted first ?

---

### Post by EddDoubleD on 2009-12-18
ok thanks

---

### Post by ankspo71 on 2009-12-18
Thanks for the assistance MooPi. I never new what the name was of the autostart file. Now that I know what it is (and where it goes), I have installed openbox again (as a second desktop), and it is working out nicely.

---

### Post by EddDoubleD on 2009-12-19
How do I install pypanel? sudo apt-get install pypanel doesn't work.

---

### Post by MooPi on 2009-12-19
pypanel doesn't seem to be in the standard repository and the last version to support it was Intrepid 8.10  [http://packages.ubuntu.com/intrepid/x11/pypanel](http://packages.ubuntu.com/intrepid/x11/pypanel)
Install instructions included.

---

### Post by kcarpet1 on 2009-12-19
I have always been fond of Openbox.  We are going to Openbox everything on Christmas eve?  Andy You?  Christmas eve or Christmas morning.

Sorry my attempt at humor.

Keller

---

