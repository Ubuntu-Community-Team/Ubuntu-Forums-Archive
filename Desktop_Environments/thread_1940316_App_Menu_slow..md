---
title: "App Menu slow."
date: 2012-03-13
forum: Desktop Environments
---

### Post by ohnonot on 2012-03-13
Hello,

I'm using the standard Applications Menu in xfce4-panel and it's a bit slow sometimes, hovering over submenus forces loading of all icons, small freezes.

it seems that the menu is not loaded into memory by default; can that be changed?
Or some popup delay on mouse hover?

I don't see any gui or .conf or man-page....

any help appreciated!

---

### Post by LewisTM on 2012-03-13
Yes, the menu is a bit slow the first time you open it. It's not made of a single file but of multiple text files and icons that Xfce has to seek on your hard drive, interpret and structure. The more apps the slower. This also applies to the Xfce Appplication Finder and to the right click desktop menu (if the Applications menu is enabled).

I think preloading it might needlessly increase the boot time.
You could disable icons in menus to speed things up. If you're in a hurry and know what you're looking for you could also use a seek-and-launch app like Synapse that doesn't build a menu but only searches through the items and returns relevant ones.

Cheers!

---

### Post by ohnonot on 2012-03-13
> **LewisTM said:**
> Yes, the menu is a bit slow the first time you open it. It's not made of a single file but of multiple text files and icons that Xfce has to seek on your hard drive, interpret and structure. The more apps the slower. This also applies to the Xfce Appplication Finder and to the right click desktop menu (if the Applications menu is enabled).

I think preloading it might needlessly increase the boot time.
You could disable icons in menus to speed things up. If you're in a hurry and know what you're looking for you could also use a seek-and-launch app like Synapse that doesn't build a menu but only searches through the items and returns relevant ones.

Cheers!Cheers!
so is it possible to preload it?
also i'm most definitely sure it doesn't happen only the first time after booting....
and i miss config options to adjust mouse hover popup delay.

are there alternatives? i liked mintmenu but can't install it anymore...

---

### Post by ohnonot on 2012-03-15
bump.

is it possible to preload the app menu?

are there alternatives for xfce?

---

### Post by Peripheral Visionary on 2012-03-15
> **ohnonot said:**
> 
is it possible to preload the app menu?

are there alternatives for xfce?

I don't know about the first question (I'm a newcomer), but I do know there are alternatives to Xfce! A really good description of alternatives can be found here: [a layman's guide to Linux desktops]("http://adoptedsidekick.wordpress.com/2012/03/14/linux-desktops/")

---

### Post by ohnonot on 2012-03-16
> **Peripheral Visionary said:**
> I don't know about the first question (I'm a newcomer), but I do know there are alternatives to Xfce! A really good description of alternatives can be found here: [a layman's guide to Linux desktops]("http://adoptedsidekick.wordpress.com/2012/03/14/linux-desktops/")i wrote alternatives *for* xfce!
and i meant: are there alternatives to the normal app menu for xfce.
meaning, i want to keep xfce/xubuntu but i don't particularly like the app menu (for reasons i explained in this post) and i hoped there was some alternative (which i can't find).

bump again.

btw, what happened to xfapplet, the panel plugin that allows one to use gnome panel plugins? i installed xfce4-goodies but it's nowhere...

---

### Post by LewisTM on 2012-03-16
An alternative for many things in Xfce would be Cairo-dock. It offers, among other things, a generic application menu that does feel faster. It also offers a more powerful Places menu called 'Shortcuts'.
In addition, Cairo offers an extra applet that supports the advanced [GnomMenu launcher]("https://launchpad.net/~gnomenu-team/+archive/ppa") which has to be installed sperately. 
[Drag this link on your dock to install it]("http://download.tuxfamily.org/glxdock/mediacolor/album7/1316892537_2cd5e89804/GnoMenu.tar.gz"). This link if for enabling Gnomenu in Cairo, not for installing Gnomenu on your system. For that:
```
sudo add-apt-repository ppa:gnomenu-team/ppa
```
Note that you will have to edit the contents of /etc/apt/sources.list.d/gnomenu-team-ppa-oneiric.list and change oneiric to natty because the PPA doesn't offer a package for 11.10
Then run 
```
sudo apt-get update && sudo apt-get install gnomenu -y
```

As for xfapplet, it's gone because GNOME 2 panel plugins are no longer offered .

Hope you find something that works for you!

---

### Post by ohnonot on 2012-03-16
thanks!
i tried cairo dock before but found it too resource-consuming on my old machine.
but i will try to install the gnome menu tomorrow.
and here's a :KS for you!

---

### Post by ohnonot on 2012-03-18
installing gnomenu.
adding the repository worked, edited oneiric to natty. OK
synaptic does not show gnomenu but installing from commandline worked. OK
GnoMenu came up once (in systray); after that, no more.
couple of reboots, nothing.

Did you actually mean this would work under xfce *without *cairo-dock?

---

### Post by Rodney9 on 2012-03-18
> **ohnonot said:**
> thanks!
i tried cairo dock before but found it too resource-consuming on my old machine.
but i will try to install the gnome menu tomorrow.
and here's a :KS for you!

For an old machine Lubuntu would run better and faster.

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by ohnonot on 2012-03-18
> **Rodney9 said:**
> For an old machine Lubuntu would run better and faster.

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR=Blue]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodneythanks, i had tried lubuntu before (as well as ubuntu and mint fluxbox and others) but i found it too light.
xubuntu offers the best from both extremes, to me.
anyhow other things are running smoothly, it's the menu that lags. and is not customizable.

---

### Post by LewisTM on 2012-03-18
> **ohnonot said:**
> installing gnomenu.
adding the repository worked, edited oneiric to natty. OK
synaptic does not show gnomenu but installing from commandline worked. OK
GnoMenu came up once (in systray); after that, no more.
couple of reboots, nothing.

Did you actually mean this would work under xfce *without *cairo-dock?
Run this command at startup:
```
GnoMenu.py run-in-tray
```

---

### Post by ohnonot on 2012-03-19
no, i tried that, it didn't work.```
~$ GnoMenu.py run-in-tray
gconf backend
python numpy not installed , some effects and gtk native colors wont be available
GnoMenu 2.9
settings load
gmenu found, using it as default menu parser
start
shaping window
Traceback (most recent call last):
  File "/usr/lib/gnomenu/GnoMenuTray.py", line 115, in <module>
    GnoMenu()
  File "/usr/lib/gnomenu/GnoMenuTray.py", line 51, in __init__
    self.hwg = Main_Menu(self.HideMenu)
  File "/usr/lib/gnomenu/Menu_Main.py", line 92, in __init__
    self.setup()
  File "/usr/lib/gnomenu/Menu_Main.py", line 344, in setup
    self.PGL = IconProgramList()
  File "/usr/lib/gnomenu/Menu_Widgets.py", line 1845, in __init__
    self.XDG = XDGMenu()
  File "/usr/lib/gnomenu/Menu_Items.py", line 113, in __init__
    self.Restart(item)
  File "/usr/lib/gnomenu/Menu_Items.py", line 147, in Restart
    self.ConstructMenu()
  File "/usr/lib/gnomenu/Menu_Items.py", line 425, in ConstructMenu
    self.SearchMenu(path)
  File "/usr/lib/gnomenu/Menu_Items.py", line 471, in SearchMenu
    if name.upper().count(self.Menu) != 0 or execute.upper().count(self.Menu) != 0:
TypeError: expected a character buffer object
```

---

### Post by LewisTM on 2012-03-19
Hmm, I don't get the numpy error, maybe that's what missing for you.
Install python-numpy and report back.

---

### Post by ohnonot on 2012-03-22
> **LewisTM said:**
> Hmm, I don't get the numpy error, maybe that's what missing for you.
Install python-numpy and report back.
```
~$ GnoMenu.py settings
gconf backend
GnoMenu 2.9
settings load
Killed
~$ GnoMenu.py run-in-window
Traceback (most recent call last):
  File "/usr/lib/gnomenu/GnoMenu.py", line 26, in <module>
    from gi.repository import PanelApplet as gnomeapplet
  File "/usr/lib/python2.7/dist-packages/gi/__init__.py", line 23, in <module>
    from ._gi import _API, Repository
ImportError: could not import gobject (error was: ImportError('When using gi.repository you must not import static modules like "gobject". Please change all occurrences of "import gobject" to "from gi.repository import GObject".',))
~$ GnoMenu.py run-in-tray
gconf backend
GnoMenu 2.9
settings load
gmenu found, using it as default menu parser
start
shaping window
Traceback (most recent call last):
  File "/usr/lib/gnomenu/GnoMenuTray.py", line 115, in <module>
    GnoMenu()
  File "/usr/lib/gnomenu/GnoMenuTray.py", line 51, in __init__
    self.hwg = Main_Menu(self.HideMenu)
  File "/usr/lib/gnomenu/Menu_Main.py", line 92, in __init__
    self.setup()
  File "/usr/lib/gnomenu/Menu_Main.py", line 344, in setup
    self.PGL = IconProgramList()
  File "/usr/lib/gnomenu/Menu_Widgets.py", line 1845, in __init__
    self.XDG = XDGMenu()
  File "/usr/lib/gnomenu/Menu_Items.py", line 113, in __init__
    self.Restart(item)
  File "/usr/lib/gnomenu/Menu_Items.py", line 147, in Restart
    self.ConstructMenu()
  File "/usr/lib/gnomenu/Menu_Items.py", line 425, in ConstructMenu
    self.SearchMenu(path)
  File "/usr/lib/gnomenu/Menu_Items.py", line 471, in SearchMenu
    if name.upper().count(self.Menu) != 0 or execute.upper().count(self.Menu) != 0:
TypeError: expected a character buffer object
```...i have no clue.
are you sure you're using this with xfce? do you have gnome-desktop installed?

---

### Post by LewisTM on 2012-03-22
Yes I'm running in Xfce, no Gnome-desktop installed. I do have Nautilus installed but I doubt that would affect anything.
Works on two Xubuntu 11.10 machine, in which I get this, then a tray icon appears:
```
~$ GnoMenu.py run-in-tray
gconf backend
GnoMenu 2.9
settings load
gmenu found, using it as default menu parser
Error: Could not connect to Zeitgeist.
start
shaping window
Error reading web bookmarks

```
I must say this solution is probably not ideal, the app is no longer supported in 11.10 and it's not clear what kind of configuration it really needs to run.

---

### Post by Toz on 2012-03-22
With respect to the slowness of the xfce menu, does adding:
```
gtk-menu-popup-delay = 0
gtk-menu-popdown-delay = 0
```
...to ~/.gtkrc-2.0 have an effect on the sluggishness of the menu (you may need to logout an back in again for it to take effect)?

---

### Post by ohnonot on 2012-03-24
> **Toz said:**
> With respect to the slowness of the xfce menu, does adding:
```
gtk-menu-popup-delay = 0
gtk-menu-popdown-delay = 0
```...to ~/.gtkrc-2.0 have an effect on the sluggishness of the menu (you may need to logout an back in again for it to take effect)?no, it doesn't.

i installed [classicmenu-indicator]("http://ubuntuforums.org/showpost.php?p=11726806&postcount=14")
- it shows up in the notification area, which i don't like so much - and i can't change the icon - but it's snappy fast. it takes 4-5 MB of RAM and just sits there, waiting for me to click it.

now *that *i would like to achieve with my xfce-appmenu and i just don't understand why that's not possible
:confused:

PS: if anyone wants to do the same in xubuntu (or possible any other not-gnome-setup), there's a little nag:
some apps don't show up in classicmenu-indicator because they have a line in the .desktop file that says: OnlyShowIn=...
you can comment that line out for all .desktop files (usually in /usr/share/applications)
with this 1-liner:```
find . -type f -name "*desktop" | xargs perl -pi -e 's/OnlyShowIn+/# OnlyShowIn/g';
```and i recommend to make a backup of the whole applications folder before doing that!

PPS: found out that some also have a "NotShowIn"

---

### Post by lakona on 2013-02-19
> **LewisTM said:**
> Yes, the menu is a bit slow the first time you open it. It's not made of a single file but of multiple text files and icons that Xfce has to seek on your hard drive, interpret and structure. The more apps the slower. This also applies to the Xfce Appplication Finder and to the right click desktop menu (if the Applications menu is enabled).

I think preloading it might needlessly increase the boot time.
You could disable icons in menus to speed things up. If you're in a hurry and know what you're looking for you could also use a seek-and-launch app like Synapse that doesn't build a menu but only searches through the items and returns relevant ones.

Cheers!


Thank you Synapse is great (so far). It seems to be a perfect solution to the slow xfce-appfinder.

Cheers

---

### Post by wildmanne39 on 2013-02-20
Old thread closed.

---

