---
title: "Folder Background with Alpha Layer?"
date: 2009-08-31
forum: Desktop Environments
---

### Post by alejandro.mc on 2009-08-31
Hey, I'm trying to set a background image for the folders, the problem is that the image I want to use is a .png, with an alpha layer, in fact I want to use it because it would make a great transparent background.

So I've tried adding a pattern .png image, but it automatically turns it into a png without alpha layer, that is simply a solid color pattern.

Any ideas??

Thanks!

---

### Post by steveneddy on 2009-08-31
Cool idea.

Research a little about RGBA.

Here's a script for some RGBA stuff that I'm playing with.

[http://www.gnome-look.org/content/show.php/RGBA+Gtk%2B+module?content=100556](http://www.gnome-look.org/content/show.php/RGBA+Gtk%2B+module?content=100556)

Post your alpha .png if you like.

---

### Post by alejandro.mc on 2009-08-31
Hey Steve thanks a lot for replying so quickly, I believe it's what I was looking for! I'll be researching the RGBA scripts..

Right on the nail!

My .png is simply black with alpha, but I'm working on some intersting landscapes, as soon as I have them I'll upload!

Cheers! Bye!! Thanks again!

---

### Post by alejandro.mc on 2009-08-31
How come it's that hard to apply whatever it's being use to make the terminal transparent, in nautilus??

---

### Post by steveneddy on 2009-09-01
Screenshot

---

### Post by alejandro.mc on 2009-09-02
PLZ help?

=)

I'm trying to follow this that you showed me:

> 1) Compile it:
gcc -fPIC -shared librgba.c -o librgba.so `pkg-config --cflags --libs gtk+-2.0`
2) Copy librgba.so to /usr/lib/gtk-2.0/modules.
Set GTK_MODULES=rgba variable:
Add export GTK_MODULES=rgba to .profile
3) Install Cimitan\'s murrine engine and themes for it
4) Activate RGBA:
- Open gnome-color-chooser
- go to \"Engines\" tab
- set \"global\" checkbox
- Choose \"Murrine\"
- Click preferences
- set 2 RGBA checkboxes
5) Set environment variable GTK_RGBA_APPS

GTK_RGBA_APPS variable
- set it to colon separated list of applications to activate rgba ONLY in these apps:
GTK_RGBA_APPS=gedit:app2:app3

- append \"allbut\" to start to activate rgba in ALL apps except listed:
GTK_RGBA_APPS=allbut:gedit:app2:app3

FAQ
Q: Some applications does not work. Is it bug?
A: It is Ok, and not bug of RGBA Gtk+ module.
Not all apps can use RGBA.
You SHOULD set up GTK_RGBA_APPS variable.
For example:
GTK_RGBA_APPS=gedit:gcacltool:gnome-help - Activate RGBA ONLY in gnome edit, gnome calculator and gnome help.
or
GTK_RGBA_APPS=allbut:gedit:gcacltool:gnome-help - Activate RGBA in ALL applications except listed.

P.S. Sorry for bad English.



Changelog:
0.2
prints name of program to console when rgba activated.

0.1
first release



But I really don't know much about compiling etc..

If it doesn't take up too much of your time, at least maybe point me in any direction =)

THX Steve!

---

### Post by steveneddy on 2009-09-03
This is nothing more than a CP exercise. (copy and paste)

To copy and paste in Linux just highlight the test you want to copy and press the middle mouse button to paste.
Highlight text on web page, move to terminal, middle mouse button pastes in terminal.

OK - one the web page in the link provided above, about the middle of the page is a download link.

Download the file, which will open up a web page full of code. 

Alt + a will highlight the entire page. Ctrl + v will copy.

Open a text editor. ( Applications --> Accessories --> Text Editor )

Paste the previously highlighted text to the Text Editor.

Save it to your desktop and make sure it is named **librgba.c**.

In terminal perform this function:

```
cd ~/Desktop
```and hit the Enter key. ( this will move the terminal from /home to the Desktop )

Now run the first command:

**```
gcc -fPIC -shared librgba.c -o librgba.so `pkg-config --cflags --libs gtk+-2.0`
```**



Now for step two on the web page:

In Terminal:

**```
sudo cp librgba.so to /usr/lib/gtk-2.0/modules
```**


The next part of step two is:

[B]> Set GTK_MODULES=rgba variable:
Add **export GTK_MODULES=rgba** to .profile[/B]


So we simply open up our /home folder and hit the Ctrl + h keys to show the hidden folders and files.

Look for a file named .profile and open it up by double clicking it or right click and open with Text Editor.

Make it look like mine:

```

[COLOR=Red]export GTK_MODULES=rgba
export GTK_RGBA_APPS=gedit:gcalctool[/COLOR]

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
    . "$HOME/.bashrc"
    fi
fi

```the parts in [COLOR=Red]RED[/COLOR] copy and paste to YOUR .profile file

I believe the murrine theme engine is in the repos:
```

sudo apt-get install gtk2-engines-murrine
```If that doesn't work you need to install the Universe repos then repeat the last command.

Get you some [Murrine Themes]("http://cimi.netsons.org/media/download_gallery/MurrineThemePack.tar.bz2")

If you haven't yet, install gnome-color-chooser

```
sudo apt-get install gnome-color-chooser
```[B]> Activate RGBA:
- Open gnome-color-chooser
- go to \"Engines\" tab
- set \"global\" checkbox
- Choose \"Murrine\"
- Click preferences 
- set 2 RGBA checkboxes[/B]



Shut all windows and restart.

You should have Transparency in gedit and gcalctool (calculator)

Also install this plugin from this page:

[http://www.cimitan.com/murrine/node/90](http://www.cimitan.com/murrine/node/90)

for eye of gnome (gnome's pic viewer)

That should be it.

Now get all of your transparencies set with Emerald and Compiz and you'll have a rockin' desktop.

> ## make gnome bar true transparent

if you are using compiz (desktop effects), you can add true transparency.
go to System->Prefs->Advanced desktop effects settings
Click on General opts.->Opacity settings, and add the following entry at top of the list:
Opacity windows: type=dock
Opacity windows values: 80 (adjust this to your like)

if you dont have the advanced desktop settings util, just install it:
sudo apt-get install compizconfig-settings-manager

this will make entire panel transparent> 
## removing gnome panel drop shadow
You can set the Shadow Windows (Windows Decoration)option in CCSM Window Decorations from "any" to "any & !(type=dock)" to remove the shadow from the panel

## Also make panel and menus transparent

Open CCSM

Go to General Settings

Go to Tab - Opacity Settings

Settings as follows:

dock 67
Menu 90
DropdownMenu 92
popupmenu 93

Link: [http://wiki.compiz-fusion.org/WindowMatching](http://wiki.compiz-fusion.org/WindowMatching)Old stuff from the Beryl days but it still works in Compiz.

Good Luck and have fun.

---

