---
title: "fluxbox w/ gnome applets"
date: 2006-09-11
forum: Desktop Environments
---

### Post by martial on 2006-09-11
had a quick question.. i am running fluxbox with xfce-mcs-manager at startup to get the gtk and icon settings... and i was curious if it is possible to run gnome-applets on the fluxbox toolbar like netspeed or ibm-acpi and others.

thanks

---

### Post by AlucardZero on 2006-11-09
Wish I knew this too.

---

### Post by kerry_s on 2006-11-10
I'm using fluxbox & thunar with xfce4-panel.

> had a quick question.. i am running fluxbox with xfce-mcs-manager at startup to get the gtk and icon settings... and i was curious if it is possible to run gnome-applets on the fluxbox toolbar like netspeed or ibm-acpi and others.


You could have just used a .gtkrc-2.0 and put your settings, here's mine->

gtk-icon-theme-name = "Rodent"
gtk-theme-name = "SphereCrystal"
gtk-font-name = "Sans 10"


Do you mean tray applets? It should work.

Pic->

---

### Post by HydroDiOxide on 2006-11-26
I can't find out how to use a Gnome theme to cheer up my fluxbox. I using the fluxbox theme found [here](http://www.boxwhore.org/modules/wfdownloads/images/screenshots/alssi.png) but I can't get the scrollbars and icons as seen in the image. Anyone any idea how to get that done? By the way: transparency doesn't seem to work either when I set it in the fluxbox rightclick menu. Anyone any idea how to get that done?

---

### Post by kerry_s on 2006-11-26
> **HydroDiOxide said:**
> I can't find out how to use a Gnome theme to cheer up my fluxbox. I using the fluxbox theme found [here](http://www.boxwhore.org/modules/wfdownloads/images/screenshots/alssi.png) but I can't get the scrollbars and icons as seen in the image. Anyone any idea how to get that done? By the way: transparency doesn't seem to work either when I set it in the fluxbox rightclick menu. Anyone any idea how to get that done?

When you set transparency, you have to restart fluxbox. I think that icon theme is blue tango  Just install it & use a  .gtkrc-2.0 like i did.

---

### Post by HydroDiOxide on 2006-11-27
I tried to set transparency, but it doesn't seem to work. Maybe it's my old hardware? How can I install the icontheme in fluxbox and what is a .gtkrc-2.0? And how will this change the scrollbars?

Could you give me a bit more info please.


UPDATE: I fixed the transparency thing. "force pseudo-transparency" has to be on.

---

### Post by kerry_s on 2006-11-27
Okay lets try this.

Tranparency:

(your editor) /.fluxbox/init
look for
session.forcePseudoTransparency:	fale
change to
session.forcePseudoTransparency:	true

if that don't work
sudo (your editor) /etc/X11/xorg.conf

add this to the end

```
Section "Extensions"
        Option   	"Composite"   "FALSE"
EndSection
```


The .gtkrc-2.0:

Basically this is a way of setting your theme's with out a gui.

gtk-icon-theme-name = "Rodent"   <- This is where you put the name of the icons, the icons are in /usr/share/icons or in ~/.icons in you home directory if you downloaded your own. I have > xfce4-icon-theme < it's called Rodent.

gtk-theme-name = "SphereCrystal"   <- This is for the scroll bars, buttons and toolbar icons, it's in /usr/share/themes.I have> gtk2-engines-spherecrystal <installed.

All the themes i use are in the repos. I use nothing fancy.


gtk-font-name = "Sans 10"  <- this is for the size of the fonts for icons.

---

### Post by HydroDiOxide on 2006-11-27
Fixed the transparency thing... I'm starting to get somewhere. 

@kerry_s: About gtkrc-2.0:

Where do I get it, and how do I execute or edit it? I've got a .gtkrc-1.2-gnome2 textfile in my home folder, is that what I'm looking for?

Ever tried Openbox?

By the way: do you know how to get a dashboard-like thing as you can see in the screendump I mentioned earlier?

---

### Post by HydroDiOxide on 2006-11-27
I'm really wondering how to get my fluxbox to sort of look like [this](http://gnome-look.org/content/show.php?content=46287) (scrollbars, icons and stuff) in combination with [this one](http://www.boxwhore.org/modules/wfdownloads/images/screenshots/alssi.png) or any other of the beautiful desktops shown [here](http://www.boxwhore.org/modules/wfdownloads/viewcat.php?cid=2).

I've really no idea how to combine these gnome gtk+ themes with fluxbox...

---

### Post by kerry_s on 2006-11-27
> **HydroDiOxide said:**
> I'm really wondering how to get my fluxbox to sort of look like [this](http://gnome-look.org/content/show.php?content=46287) (scrollbars, icons and stuff) in combination with [this one](http://www.boxwhore.org/modules/wfdownloads/images/screenshots/alssi.png) or any other of the beautiful desktops shown [here](http://www.boxwhore.org/modules/wfdownloads/viewcat.php?cid=2).

I've really no idea how to combine these gnome gtk+ themes with fluxbox...


Are you even reading my posts?

For the theme, download it & unpack it & then put it in .themes(you might have to make) in your user folder.

Now add the line to the gtkrc-2.0 file.

For the rest of the theme it's called jello( [http://www.boxwhore.org/modules/wfdownloads/visit.php?cid=2&lid=368](http://www.boxwhore.org/modules/wfdownloads/visit.php?cid=2&lid=368)   ) than just put it in the /.fluxbox/styles folder and select it in the fluxbox menu.

The icons are here-> [http://art.gnome.org/download/themes/icon/1150/ICON-UnofficialTango.tar.bz2](http://art.gnome.org/download/themes/icon/1150/ICON-UnofficialTango.tar.bz2)
download, upack & put it in .icons(you make) folder then just put the name in the gtkrc-2.0 where i have "rodent"

---

### Post by macewan on 2006-11-27
open xterm

cd .themes

wget [http://gnome-look.org/content/files/46287-Murrina-Black.tar.gz](http://gnome-look.org/content/files/46287-Murrina-Black.tar.gz)

tar -xzf 46*.gz

exit

System > Preferences > Theme

when the theme window opens select/click the 'Theme _D_etails' button. when Theme Details window appears click the Controls tab, if you are not already there. Scroll through Clearlooks, Crux and Human all the way to Murrina-Black. Now you have the basic look.


> **HydroDiOxide said:**
> I can't find out how to use a Gnome theme to cheer up my fluxbox. I using the fluxbox theme found [here]("http://www.boxwhore.org/modules/wfdownloads/images/screenshots/alssi.png") but I can't get the scrollbars and icons as seen in the image. Anyone any idea how to get that done? By the way: transparency doesn't seem to work either when I set it in the fluxbox rightclick menu. Anyone any idea how to get that done?

---

### Post by macewan on 2006-11-27
It's the Alssi theme found here:

[http://www.boxwhore.org/modules/wfdownloads/visit.php?cid=2&lid=367](http://www.boxwhore.org/modules/wfdownloads/visit.php?cid=2&lid=367)

> **kerry_s said:**
> 
For the rest of the theme it's called jello( [http://www.boxwhore.org/modules/wfdownloads/visit.php?cid=2&lid=368](http://www.boxwhore.org/modules/wfdownloads/visit.php?cid=2&lid=368)   ) than just put it in the /.fluxbox/styles folder and select it in the fluxbox menu.


---

### Post by kerry_s on 2006-11-27
> **macewan said:**
> open xterm

cd .themes

wget [http://gnome-look.org/content/files/46287-Murrina-Black.tar.gz](http://gnome-look.org/content/files/46287-Murrina-Black.tar.gz)

tar -xzf 46*.gz

exit

System > Preferences > Theme

when the theme window opens select/click the 'Theme _D_etails' button. when Theme Details window appears click the Controls tab, if you are not already there. Scroll through Clearlooks, Crux and Human all the way to Murrina-Black. Now you have the basic look.

That would work if gnome is installed, but most of us have command-line system+fluxbox, so are systems are lite weight. We like to keep things light & don't install all that fancy gui stuff ;)

---

### Post by macewan on 2006-11-27
oh, guess you're right. please forgive my ignorance in assuming GNOME was installed.

cheers


[adding]

From the screenshot he linked to I incorrectly assumed that file manager was nautilus --no-desktop

---

### Post by kerry_s on 2006-11-27
> **macewan said:**
> oh, guess you're right. please forgive my ignorance in assuming GNOME was installed.

cheers


[adding]

From the screenshot he linked to I incorrectly assumed that file manager was nautilus --no-desktop

No no, Your not ignorant, for all i know he might have fluxbox on gnome and just doesn't want to use that part. I looked over all the posts and he doesn't say what he's actually using. I was just making a general suggestion that not all have gnome installed. I meant nothing by it, don't sweat it, your suggestion was good.

---

### Post by HydroDiOxide on 2006-11-28
Hey kerry_s, I appreciate your replies. I'm really trying to follow you, but like I said there is no gtkrc-2.0 file on my laptop, so you've got me puzzled a lot. I understand what you said earlier, but really, I've got no idea where to put it. Maybe it helps to say that I started out with a Xubuntu installation (as your can read in another thread I started which you replied on as well). Please bear with me...

> Now add the line to the gtkrc-2.0 file.

What do I need to install to get a gtkrc-2.0 file......? And how do I get the theme to be applied every time I log in?

---

### Post by kerry_s on 2006-11-28
You make the .gtkrc-2.0> right click new file/text. Sometimes you make your own files or folders, like you create a .icons folder for icons so you don't have to worry about permissions, because there installed in user space. The system will always check $home/user/ for certain settings files before it uses the default.

Example:
instead of putting your icons in the root(usr/share/icons) side were you need permission(ie:gksu or sudo) you can create a hidden icons folder in your home(right click> new folder) and the system will look there for the icon set you want to use, hidden files are always started with a "." in the front(.icons, .themes,...)

Once you put your setup in the .gtkrc-2.0 your done it will always use those settings, unless you change it manually. When you change the name in the .gtkrc-2.0 the change is pretty much instant, all new windows will use the new theme,icons, or fonts.

---

### Post by HydroDiOxide on 2006-11-28
Allright! Got it up and running. Thanks for your patience, you all and especially kerry_s.

I've got two more questions. My sudo environments are not effected by the gtkrc-2.0 file (sudo thunar... sudo everything) is it possible to do this?

Second one: what initiates the gtkrc-2.0 file?

---

### Post by BLTicklemonster on 2006-11-28
I installed fluxbox this morning, and ... well, I see a taskbar when I'm in it, and if I right click on the desktop, I get an icon that says fluxbox, and that's it. 

I can see how this would keep system resources down, for sure.

But.. well, I want to use my computer. How do I get fluxbox to ... work?

---

### Post by kerry_s on 2006-11-28
> **HydroDiOxide said:**
> Allright! Got it up and running. Thanks for your patience, you all and especially kerry_s.

I've got two more questions. My sudo environments are not effected by the gtkrc-2.0 file (sudo thunar... sudo everything) is it possible to do this?

Second one: what initiates the gtkrc-2.0 file?

Copy the same .gtkrc-2.0 to the root folder.

> Second one: what initiates the gtkrc-2.0 file?

Huh? Do mean why does the system look user settings first? Any ways, it will use user settings before default.

---

### Post by kerry_s on 2006-11-28
> **BLTicklemonster said:**
> I installed fluxbox this morning, and ... well, I see a taskbar when I'm in it, and if I right click on the desktop, I get an icon that says fluxbox, and that's it. 

I can see how this would keep system resources down, for sure.

But.. well, I want to use my computer. How do I get fluxbox to ... work?

Sounds like you need to run-> update-menus

Open a terminal(you can use failsafe, or log in to your regular)
type->
sudo apt-get update
sudo apt-get install menu
sudo update-menus
update-menus

 then log back in to fluxbox.

---

### Post by BLTicklemonster on 2006-11-28
I hope you don't mean for me to open a terminal in flux box, because that is what I'm trying to tell you, there's nothing there but a blank desktop and a taskbar. The taskbar gives me nothing to use no matter how I click on it. There's only stuff relating to workspaces and the bar itself.

*edit:

okay, I did all but the last part in icewm, and booted to fluxbox.

Now I have this:

```
bill@bill-desktop:~$ update-menus
convert: unable to open file `/home/bill/.menu/icons/Play': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/Play': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/Play': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/Play': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/Play': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/Play': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/Play': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/Play': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/Play': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/Unreal': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/Unreal': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/Unreal': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/XPlug': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/XPlug': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/XPlug': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/XPlug': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/XPlug': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/XPlug': No such file or directory.
bill@bill-desktop:~$ 

```

which, in retrospect, probably means nothing.

---

### Post by kerry_s on 2006-11-28
> **BLTicklemonster said:**
> I hope you don't mean for me to open a terminal in flux box, because that is what I'm trying to tell you, there's nothing there but a blank desktop and a taskbar. The taskbar gives me nothing to use no matter how I click on it. There's only stuff relating to workspaces and the bar itself.

*edit:

okay, I did all but the last part in icewm, and booted to fluxbox.

Now I have this:

```
bill@bill-desktop:~$ update-menus
convert: unable to open file `/home/bill/.menu/icons/Play': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/Play': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/Play': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/Play': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/Play': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/Play': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/Play': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/Play': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/Play': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/Unreal': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/Unreal': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/Unreal': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/XPlug': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/XPlug': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/XPlug': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/XPlug': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/XPlug': No such file or directory.
convert: unable to open file `/home/bill/.menu/icons/XPlug': No such file or directory.
bill@bill-desktop:~$ 

```

which, in retrospect, probably means nothing.

Okay that don't look right, did you do the> sudo apt-get install menu <to make sure you have it installed?

How did you install fluxbox?
Do you have a .fluxbox folder?
If so what's in there?
Is there a /etc/X11/fluxbox ?
Whats the output of> locate menu ?

---

### Post by BLTicklemonster on 2006-11-28
Menu was already installed, the rest went okay. What you see up there is just programs I installed that aren't normally "linux" apps. At least unreal and xplug aren't for sure, not positive about play.

I have, in .fluxbox, the following folders: backgrounds, pixmaps, styles, and document are: fluxbox-menu, init, keys, menu, menudef.hook, slitlist, and startup.

So all in all, I think I have it pretty much functional for now. I wonder, though, can I add launchers and such to the task/toolbar?

---

### Post by kerry_s on 2006-11-28
> **BLTicklemonster said:**
> 
So all in all, I think I have it pretty much functional for now. I wonder, though, can I add launchers and such to the task/toolbar?

Hmm, You can put them in the system tray with alltray or kxdocker, but usally you would just add your own panel.

What are you using for the file manager? (it might have a panel)

---

### Post by BLTicklemonster on 2006-11-28
:) 


what?


I have rox-filer, if that's what you mean...

my bad, that's icewm.

so what do you mean? I'm totally new at this whole window manager stuff, and linux, too, for that matter.


*edit:

upon installing kxdocker, I ran it, and got this:

```
bill@bill-desktop:~$ kxdocker
Link points to "/tmp/ksocket-bill"
Link points to "/tmp/kde-bill"
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
KXDocker Will use Composite Extensions!
kxdocker: WARNING: Cannot find updated resources: you may need to update or reinstall KXDocker resources, checkout http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources
kxdocker: WARNING: loading xml...
kxdocker: WARNING: Warning user kxdocker_conf.xml may be corrupt: loading last backup!
kxdocker: WARNING: Warning user, and backup configurations are corrupt! I'm going to load system kxdocker_conf.xml !!!
kxdocker: WARNING: Warning user, backup, system configurations are corrupt! please install right kxdocker_conf.xml
DCOP aborting call from 'anonymous-11382' to 'kxdocker'
ERROR: Communication problem with kxdocker, it probably crashed.
bill@bill-desktop:~$ 

```

---

### Post by kerry_s on 2006-11-28
Yeap, that's what i mean. Rox has a panel and can do background & desktop icons.Try this->

in terminal:
rox --top=default

That should give you a panel for icons on the top

For background & desktop

rox --pinboard=default

That will use rox as the background, you'll neeed to go into options & check the compatibility so you can still use the right click of fluxbox.

Here's the manual for rox-> [http://rox.sourceforge.net/Manual/Manual/Manual.html?PHPSESSID=c1fcb631a92d28dc29b822e73690fd92#id2456497](http://rox.sourceforge.net/Manual/Manual/Manual.html?PHPSESSID=c1fcb631a92d28dc29b822e73690fd92#id2456497)

Don't worry about kxdocker just uninstall that, it has always been buggy.

---

### Post by BLTicklemonster on 2006-11-28
Excellent! Here I was trying to get some kxdocker-configurator and other stuff installed and working, and you just saved me some big problems. Thanks a lot!

---

### Post by kerry_s on 2006-11-28
I'm assuming you already now how to add the rox to your start up so they will start with the rest of the desktop? Just in case->
 put it in .fluxbox/startup ,Look for this line "# Applications you want to run with fluxbox."
then put this in the blank space->

rox --top=default &
rox --pinboard=default &

---

### Post by BLTicklemonster on 2006-11-28
Well, the problem I have run into is that if I have rox running, then I loose my ability to get to things as I would right now, such as right click and get a terminal, or go to net>firefox. This just won't do. I'll look over what you have at the beginning of this thread about gnome and see what that gives me.

---

### Post by BLTicklemonster on 2006-11-28
> **kerry_s said:**
> I'm using fluxbox & thunar with xfce4-panel.



You could have just used a .gtkrc-2.0 and put your settings, here's mine->

gtk-icon-theme-name = "Rodent"
gtk-theme-name = "SphereCrystal"
gtk-font-name = "Sans 10"


Do you mean tray applets? It should work.

Pic->

What do you mean here, but used a .gtkrc-2.0 and put your settings? What is gtkrc-2.0? I don't see it in synaptic anywhere, and I can't install it from the terminal. I'm new, so if you could drop a wee bit more detail, I'd appreciate it. Sorry if I'm beginning to bug you, Kerry.

Oh, and here's my starup stuff for adding things:

```
# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
unclutter -idle 2 &
wmnd &
wmsmixer -w &
idesk &
thunar $
gnome-applets $

# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

#exec /usr/bin/fluxbox
# or if you want to keep a log:
exec /usr/bin/fluxbox -log "/home/bill/.fluxbox/log"
```

I guess I did something wrong, because there's nothing there that I would have supposed would have been there. and the log shows nothing other than

```
------------------------------------------
apps file failure
apps file failure
apps file failure
apps file failure
```

at the bottom of the page. The files listed don't show up.

---

### Post by kerry_s on 2006-11-29
> **BLTicklemonster said:**
> Well, the problem I have run into is that if I have rox running, then I loose my ability to get to things as I would right now, such as right click and get a terminal, or go to net>firefox. This just won't do. I'll look over what you have at the beginning of this thread about gnome and see what that gives me.

That's why i said you need to go into options> compatibility & check the top 3 box's.

---

### Post by kerry_s on 2006-11-29
> **BLTicklemonster said:**
> What do you mean here, but used a .gtkrc-2.0 and put your settings? What is gtkrc-2.0? I don't see it in synaptic anywhere, and I can't install it from the terminal. I'm new, so if you could drop a wee bit more detail, I'd appreciate it. Sorry if I'm beginning to bug you, Kerry.

Oh, and here's my starup stuff for adding things:

```
# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
unclutter -idle 2 &
wmnd &
wmsmixer -w &
idesk &
thunar $
gnome-applets $

# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

#exec /usr/bin/fluxbox
# or if you want to keep a log:
exec /usr/bin/fluxbox -log "/home/bill/.fluxbox/log"
```

I guess I did something wrong, because there's nothing there that I would have supposed would have been there. and the log shows nothing other than

```
------------------------------------------
apps file failure
apps file failure
apps file failure
apps file failure
```

at the bottom of the page. The files listed don't show up.

Okay, i already explained the gtkrc-2.0 file, it's one of those files that you make.

---

### Post by HydroDiOxide on 2006-11-29
> **BLTicklemonster said:**
> What do you mean here, but used a .gtkrc-2.0 and put your settings? What is gtkrc-2.0? I don't see it in synaptic anywhere, and I can't install it from the terminal. I'm new, so if you could drop a wee bit more detail, I'd appreciate it. Sorry if I'm beginning to bug you, Kerry.

@BLTicklemonster

Just read through the thread and you should get it up and running. It worked for me, which means it can work for anyone.

Just create an empty file named .gtkrc-2.0 in your /home/you_user_name folder and copy the lines below into it:

```
gtk-icon-theme-name = "Rodent"
gtk-theme-name = "SphereCrystal"
gtk-font-name = "Sans 10"
```

Look in /usr/share/themes if the theme is there. Same goes for the iconset which should be located in /usr/share/icons. If they are not there, download them and put them in those folders or, if you like, /home/your_user_name/.themes and /home/your_user_name/.icons (create those folders if needed).

The values ("Rodent", "SphereCrystal and "Sans 10" in the example above) can be replaced with the name of the folder which contains the theme or icon set (not sure how it works for fonts).

So if you downloaded a theme named Murrina Neo and you extracted it into you .themes folder and the folder which contains the theme is called MurrinaNeo you would change the theme line to:

```
gtk-icon-theme-name = "MurrinaNeo"
```.

That should get your fluxbox theming up and running.


@kerry_s: was wondering if you could set a cursor theme through the .gtkrc-2.0 file as well.

What I meant by initiating is: what actually executes the .gtkrc-2.0 file, just out of curiosity.

---

### Post by BLTicklemonster on 2006-11-29
I actually had themes up and running before I made the file to list them in, lol. But I made it anyway, thanks guys. I'll check those three boxes, Kerry.

---

### Post by BLTicklemonster on 2006-11-29
Oh, and I have gotten a wallpaper to show up... jsut before the desktop goes to a solid light blue color. I'll post my settings later today once I get back home, and see if anyone has any idea how to get the wallpaper to show up. I can't get it to work using themes or anything else. Kind of frustrating, but you know, flux looks so promising, I'm bound and determined to learn to get it working.

And I know I'm probably a bit of a newbhound, so please forgive me, and thanks for your help!

---

### Post by kerry_s on 2006-11-29
> **HydroDiOxide said:**
> @BLTicklemonster

Just read through the thread and you should get it up and running. It worked for me, which means it can work for anyone.

Just create an empty file named .gtkrc-2.0 in your /home/you_user_name folder and copy the lines below into it:

```
gtk-icon-theme-name = "Rodent"
gtk-theme-name = "SphereCrystal"
gtk-font-name = "Sans 10"
```

Look in /usr/share/themes if the theme is there. Same goes for the iconset which should be located in /usr/share/icons. If they are not there, download them and put them in those folders or, if you like, /home/your_user_name/.themes and /home/your_user_name/.icons (create those folders if needed).

The values ("Rodent", "SphereCrystal and "Sans 10" in the example above) can be replaced with the name of the folder which contains the theme or icon set (not sure how it works for fonts).

So if you downloaded a theme named Murrina Neo and you extracted it into you .themes folder and the folder which contains the theme is called MurrinaNeo you would change the theme line to:

```
gtk-icon-theme-name = "MurrinaNeo"
```.

That should get your fluxbox theming up and running.


@kerry_s: was wondering if you could set a cursor theme through the .gtkrc-2.0 file as well.

What I meant by initiating is: what actually executes the .gtkrc-2.0 file, just out of curiosity.



I haven't got fluxbox to do cursors yet. Fluxbox uses a font for the cursor. About the only thing i've done with the cursor is change it to big-cursor(sudo apt-get install big-cursor).You can find the cursor font at "/usr/share/fonts/X11/misc/cursor.pcf.gz-small"
That's the standard system cursor. I looked it to it some time back, but just let it go, i can live with the big-cursor, i don't lose track of that. :p

---

### Post by HydroDiOxide on 2006-11-29
You can get a wallpaper up by editing the file named "startup" in your /home/your_user_name/.fluxbox folder. There you should uncomment the line

```
fbsetbg -f ~/.fluxbox/backgrounds/name_of_your_wallpaper_here
```

as you can see the second part of the line is the path to you wallpaper file.

In the same file comment the line

```
/usr/bin/fbsetroot -solid black
```

Instructions are in the file as well. You might also like [this link](http://fluxbox-wiki.org/index.php/Fluxbox-wiki).

---

### Post by kerry_s on 2006-11-29
> **HydroDiOxide said:**
> You can get a wallpaper up by editing the file named "startup" in your /home/your_user_name/.fluxbox folder. There you should uncomment the line

```
fbsetbg -f ~/.fluxbox/backgrounds/name_of_your_wallpaper_here
```

as you can see the second part of the line is the path to you wallpaper file.

In the same file comment the line

```
/usr/bin/fbsetroot -solid black
```

Instructions are in the file as well. You might also like [this link](http://fluxbox-wiki.org/index.php/Fluxbox-wiki).


There's an easier way.Add this to your menu->

```
 [submenu] (Backgrounds)
  [wallpapers] (/usr/share/fluxbox/backgrounds)
  [wallpapers] (~/.fluxbox/backgrounds)
 [end]

```

and in init, look for this line->

session.screen0.rootCommand:	

change to this->

session.screen0.rootCommand:	fbsetbg -l


Now you can set your background by clicking on it & it will always use the last background, so you don't need to put it in startup.

---

### Post by HydroDiOxide on 2006-11-29
Hey kerry_s, got another question for you.

I saw you were using an xfce panel in your fluxbox. I want to try this as well. I put the line ```
xfce4-panel &
``` in my startup which fires up the panel. However the panel starts with flickering as if it doesn't want to be there. Any idea how this can be?

Secondly: when I press ALT+d (which I configured as show desktop) my panel dissapears. Can this be changed. Also my maximized windows don't maximize over the panel. I want the panel to stick to the desktop, so to say, so that windows maximize over it and it remains visible when I press ALT+d.

Thirdly: is there a way to set a different theme for the panel than the one I use for the rest of the windows. So, is there a place where I can set the theme for the xfce panel so that it won't use the theme in my gtkrc-2.0 file, but another one.

Hope this makes sense...

---

### Post by kerry_s on 2006-11-29
> **HydroDiOxide said:**
> Hey kerry_s, got another question for you.

I saw you were using an xfce panel in your fluxbox. I want to try this as well. I put the line ```
xfce4-panel &
``` in my startup which fires up the panel. However the panel starts with flickering as if it doesn't want to be there. Any idea how this can be?

Secondly: when I press ALT+d (which I configured as show desktop) my panel dissapears. Can this be changed. Also my maximized windows don't maximize over the panel. I want the panel to stick to the desktop, so to say, so that windows maximize over it and it remains visible when I press ALT+d.

Thirdly: is there a way to set a different theme for the panel than the one I use for the rest of the windows. So, is there a place where I can set the theme for the xfce panel so that it won't use the theme in my gtkrc-2.0 file, but another one.

Hope this makes sense...


I think i had that problem before, i left my bar floating & i have it wait 5 sec. on startup.
sleep 5
xfce4-panel &

I put my sleep apps outside of startup & just point them(/home/user/.startup)

To make it come to the front when its covered, middle click the title bar of the front app. Also you can't see it because i have it on autohide, but since i replaced the fluxbox panel with the xfce panel i trimmed the fluxbox panel down to just the clock(session.screen0.toolbar.tools:	clock)  & put it at the top.

Make sure you don't put the panel in the same place as the slit.

---

### Post by kerry_s on 2006-11-29
Also i saw one of your threads about you having problems with mutiple apps using the restart. Try adding killall before it->
Example:
killall wmbatt &
wmbatt &

That should kill any running one before it starts a new one. I didn't respond cause i had to think on it, but than i couldn't find the thread again.

---

### Post by BLTicklemonster on 2006-11-29
A combination of

> **kerry_s said:**
> There's an easier way.Add this to your menu->

```
 [submenu] (Backgrounds)
  [wallpapers] (/usr/share/fluxbox/backgrounds)
  [wallpapers] (~/.fluxbox/backgrounds)
 [end]

```

and in init, look for this line->

session.screen0.rootCommand:	

change to this->

session.screen0.rootCommand:	fbsetbg -l


Now you can set your background by clicking on it & it will always use the last background, so you don't need to put it in startup.

and

> **HydroDiOxide said:**
> You can get a wallpaper up by editing the file named "startup" in your /home/your_user_name/.fluxbox folder. There you should uncomment the line

```
fbsetbg -f ~/.fluxbox/backgrounds/name_of_your_wallpaper_here
```

as you can see the second part of the line is the path to you wallpaper file.

In the same file comment the line

```
/usr/bin/fbsetroot -solid black
```

Instructions are in the file as well. You might also like [this link](http://fluxbox-wiki.org/index.php/Fluxbox-wiki).

works, but I get an error message that says that a previous wallpaper was not found.

and nothing I put in startup

gnome-applets $ 

et al

will make anything come up when I restart.


Why is this so easy for you all, but not me? Am I totally missing something? The files I edit are in /home/bill/.fluxbox

---

### Post by BLTicklemonster on 2006-11-29
> **kerry_s said:**
> Sounds like you need to run-> update-menus

Open a terminal(you can use failsafe, or log in to your regular)
type->
sudo apt-get update
sudo apt-get install menu
sudo update-menus
update-menus

 then log back in to fluxbox.


... do I have to sudo update-menus, update-menus each time I edit my startup file? Just asking, because that's the only thing I can think of that would be causing me problems. (I booted to dapper now, and am installing, reading this thread so I make sure I get it right, and saw that, and it dawned on me that perhaps that was the problem I had all along)

---

### Post by kerry_s on 2006-11-29
> **BLTicklemonster said:**
> A combination of



and



works, but I get an error message that says that a previous wallpaper was not found.

and nothing I put in startup

gnome-applets $ 

et al

will make anything come up when I restart.


Why is this so easy for you all, but not me? Am I totally missing something? The files I edit are in /home/bill/.fluxbox


A combination? You should only be running 1, the difference is 1 you set manually & 1 you just click, They both run the same command "fbsetbg".The error is because you didn't click a background in the menu so it knows you have set a background, which will then be saved as the last.

For gnome-applets, that's a collection of little apps more geared towards gnome. In fluxbox i would use something else, for instance the dock apps, fluxbox loves doc apps, thats the main purpose of the slit. Most of them are in the repos, here's a sight were you can look at them & if you like just install it from the repos, If there not in the repo i don't recommend you use it.-> [http://dockapps.org/](http://dockapps.org/)

---

### Post by kerry_s on 2006-11-29
> **BLTicklemonster said:**
> ... do I have to sudo update-menus, update-menus each time I edit my startup file? Just asking, because that's the only thing I can think of that would be causing me problems. (I booted to dapper now, and am installing, reading this thread so I make sure I get it right, and saw that, and it dawned on me that perhaps that was the problem I had all along)

No, update-menus is for programs you install/remove. You shouldn't need to do the sudo one if you moved it to use the one in your home directory.Here's what my current menu looks like on this test install of feisty->

```
[begin] (Fluxbox)

[exec] (Files) {emelfm} 

[exec] (Terminal) {xterm} 
 
[submenu] (Net)
 [exec] (Firefox) {firefox}
 [exec] (Dillo) {dillo}
 [exec] (Gaim) {gaim}
 [exec] (Prozilla) {xterm -T "Prozilla" -e dproz}
[end]

[submenu] (Sound)
 [exec] (Mplayer) {gmplayer}
 [exec] (Wmix) {wmix}
[end]

[submenu] (Admin)
 [exec] (Synaptic) {gksu synaptic}
 [exec] (Root-Files) {gksu emelfm}
 [exec] (Terminal-Root) {gksu xterm}
[end]

[submenu] (Settings)
  [restart] (Restart)
  [config] (Configuration)
   [submenu] (Styles)
      [stylesdir] (/usr/share/fluxbox/styles)
      [stylesdir] (~/.fluxbox/styles)
   [end]
 [submenu] (Backgrounds)
  [wallpapers] (/usr/share/fluxbox/backgrounds)
  [wallpapers] (~/.fluxbox/backgrounds)
 [end]
[end]

[separator]
[exec] (Run Program) {fbrun}
[exec] (Keyboard) {xvkbd -no-keypad}

[submenu] (ScreenShots)
 [exec] (Snap) {scrot %T.jpg}
 [exec] (Select) {scrot -s -b %T.jpg}
 [exec] (Wait 5) {scrot -d 5 %T.jpg}
[end]

[separator]
[submenu] (Debian-menu)
 [exec] (Update-menus) {update-menus}
 [include] (~/.fluxbox/fluxbox-menu)
[end]


[separator]
[exec] (Screen Off) {/home/user/.screen-off}
[exit] (Exit)
[exec] (Reboot) {sudo shutdown now -r -f}
[exec] (Shutdown) {sudo shutdown now -h}
[end]

```

---

### Post by BLTicklemonster on 2006-11-29
Just what is slit? 

I have a background showing up so I'm leaving all that alone now, and moving on to startup. Why do I add stuff and I can't see where it is? If I put something in, like 

thunar $

then where will it be when I restart? Or do I log out and go do fluxbox?

And there's two places where files are, /etc/X11 and /home/me.. which one do I use, /home/me, right?

*edit:

I really like usp, ubuntu system panel, and use it from the command line a lot. From there, I have gottem themes that I normally use in gnome, and I go to desktop background and bam, I have a background. So that much is cool, but still, WHERE IS THE STUFF I HAVE PUT IN STARTUP? I'm in dapper now, starting from scrtatch, and nothing is cooperating here, either.

---

### Post by yabbadabbadont on 2006-11-29
> **BLTicklemonster said:**
> Just what is slit?

[http://www.fluxbox.org/docbook/en/html/chap-slit.html](http://www.fluxbox.org/docbook/en/html/chap-slit.html)

---

### Post by BLTicklemonster on 2006-11-29
lmao, I'm getting nowhere fast here. 

Thanks for the link. I now know that a slit is. Not how to use it, make it happen, adorn it with flowers, scold it when it behaves badly, but by golly, I know what a slit is.

Still, my biggest question is, what's up with the startup file? where are the things that I put in there?

---

### Post by kerry_s on 2006-11-30
> **BLTicklemonster said:**
> Just what is slit? 

I have a background showing up so I'm leaving all that alone now, and moving on to startup. Why do I add stuff and I can't see where it is? If I put something in, like 

thunar $

then where will it be when I restart? Or do I log out and go do fluxbox?

And there's two places where files are, /etc/X11 and /home/me.. which one do I use, /home/me, right?

*edit:

I really like usp, ubuntu system panel, and use it from the command line a lot. From there, I have gottem themes that I normally use in gnome, and I go to desktop background and bam, I have a background. So that much is cool, but still, WHERE IS THE STUFF I HAVE PUT IN STARTUP? I'm in dapper now, starting from scrtatch, and nothing is cooperating here, either.

 Try-> thunar &

Use "&" as in "and", not the $ dollar sign.

---

### Post by kerry_s on 2006-11-30
> **BLTicklemonster said:**
> lmao, I'm getting nowhere fast here. 

Thanks for the link. I now know that a slit is. Not how to use it, make it happen, adorn it with flowers, scold it when it behaves badly, but by golly, I know what a slit is.

Still, my biggest question is, what's up with the startup file? where are the things that I put in there?


You are putting it in .fluxbox/startup right? You put it where it says "# Applications you want to run with fluxbox." they even has some examples->

# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &

(Your app would go here.)-> thunar &

# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

---

### Post by BLTicklemonster on 2006-11-30
Yeah, my bad. I started messing around in icewm, and edited some stuff, and put the dollar sign up and thought about it, and realized what a fart I was putting dollar signs in instead of ampersands. Doh.

---

### Post by BLTicklemonster on 2006-11-30
Bingo. that's more like it. I have an xfce panel now, and found where to turn off the fluxbox toolbar.

Thanks guys!

---

### Post by BLTicklemonster on 2006-12-01
OH, by the way, it works great in feisty, too. No problems with the upgrade.

---

