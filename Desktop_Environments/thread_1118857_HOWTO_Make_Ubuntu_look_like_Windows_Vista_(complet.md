---
title: "HOWTO: Make Ubuntu look like Windows Vista (complete)"
date: 2009-04-07
forum: Desktop Environments
---

### Post by Jakey_TheSnake on 2009-04-07
Today we will turn this:

[[IMG]http://img228.imageshack.us/img228/104/ubuntuscreenshot.th.png[/IMG]](http://img228.imageshack.us/img228/104/ubuntuscreenshot.png)

Into this:

[[IMG]http://img217.imageshack.us/img217/3835/screenshotymr.th.png[/IMG]](http://img217.imageshack.us/img217/3835/screenshotymr.png)
(click for enlarge)

And I will explain it to you completely step-by-step, perfect for the linux newbie. Hopefully we'll learn some things along the way, too! 

It may look long, but that's just because everything is walked through completely, most of you will not need to read half of it, but it is there for those who do. 

[SIZE="4"]**_Panels + Start Menu_**[/SIZE]

Firstly, open up a terminal (Applications > Accessories > Terminal). Now enter:
```
gconftool-2 --dump /apps/panel > ~/settings/ubuntu.entries
```
(please create a folder named "settings" in your /home/username/ folder first). 
This saves your gnome-panel (i.e. the top/bottom menus) configuration - menus, applets, positioning etc. for loading later, as it can be a pain to change back and forth manually. To load at a later stage, use:
```
## loads settings into gconf
  gconftool-2 --load ~/settings/ubuntu.entries
## kills the gnome-panel so it restarts with the new gconf settings
  killall gnome-panel
## restart gnome network monitor applet which dies after killall gnome-panel
  nm-applet &
```

Now right-click your current panel, and select "New Panel". Move this new panel to the bottom of your screen, and delete your old one. 

Right-click your New Panel, select "Properties" and in the "Size" box change the value to 32. 

Now to give it its vista feel: download the aero-clone.tar.gz theme that is located [[COLOR="Blue"]here.[/COLOR]](http://gnome-look.org/CONTENT/content-files/57352-aero.tar.gz) To apply it, right-click on your Desktop, select "Change Desktop Background". Click the "Themes" tab at the top, press "Install" and then select "aero-clone.tar.gz" and "open". When it asks you whether you want to apply the new theme, press yes. Your panel should now look black and shiny. 

For the vista start-menu, we will need to install "GnoMenu":
[COLOR="Blue"][http://launchpad.net/gnomenu/trunk/1.6/+download/gnomenuthemes_1.6-1_all.deb](http://launchpad.net/gnomenu/trunk/1.6/+download/gnomenuthemes_1.6-1_all.deb)
[http://launchpad.net/gnomenu/trunk/1.6/+download/gnomenu_1.6-2_all.deb](http://launchpad.net/gnomenu/trunk/1.6/+download/gnomenu_1.6-2_all.deb)
[http://launchpad.net/gnomenu/trunk/1.6/+download/gnomenu-themes-gnomelook_0.1-2~20081214_all.deb](http://launchpad.net/gnomenu/trunk/1.6/+download/gnomenu-themes-gnomelook_0.1-2~20081214_all.deb)[/COLOR]

After downloading them, you can install by double clicking, then pressing "Install". You will be prompted for root password. Install in this order: gnomenuthemes_1.6-1_all.deb, gnomenu_1.6-2_all.deb, gnomenu-themes-gnomelook_0.1-2~20081214_all.deb. 

Now right click on your panel, and select "Add to Panel". Find "GnoMenu" and press add. Right click on your GnoMenu icon, and press "Preferences". Under "Menu Theme" select "Vista", for "Icon Theme" choose "Vista", for "Panel Button" - you guessed it - "Vista". Leave "Program Widgets" as "Classic". Press OK, you will be told that GnoMenu will restart, hit okay. 

A dialog box may now appear telling you of an error, and that GnoMenu needs to be restarted (it may be below an active window of yours at the time - minimize everything if GnoMenu does not appear) and press "Restart". Now right-click on it, press "Move" and drag it along until it is an appropriate distance from the left of the screen, then left-click to stop dragging. Now right-click it again and select "Lock to Panel". You can now press your start menu button to your hearts content - but one more thing before you're done with it - the user picture. Open up a terminal and type:
```
gksudo nautilus
```
You will be prompted for root password. We need this as we will be editing files that belong to the system, and will not have the correct permissions otherwise. Once it has opened, navigate to /usr/share/gnomenu/Themes/Icon/Vista. Delete the "no-user-image.png" file. To replace it, simply rename the image you would like "no-user-image" and click and drag it into the folder where the original was. Make sure your image is 48x48 pixels and saved as a .png file, this can be done in your favourite image editing suite, such as Photoshop or GIMP. 

IF your icon sometimes looks disjointed, this is because you have shadow effects enabled, and the gnome-panel's shadow is causing problems. To fix this, open up System > Preferences > CompizConfig Settings Manager and select "Window Decoration". In the "Shadow windows" box, replace "any" with "!type=dock". 

Now you can add a couple of launchers to the right of your start-button, like the launcher area that Windows has. I chose Firefox and a filebrowser launcher. Right-click on your panel > Add to Panel > Application Launcher..., (press add) then find Firefox in "Internet". Right-click on the Firefox icon and select properties, as it looks a bit clunky with our Vista panel, click on the firefox image to change it, I used this one: [img]http://img139.imageshack.us/img139/6127/42825891.png[/img]. Now repeat the move/lock steps as with the GnoMenu. 
Right-click the panel > Add to Panel > Custom Application Launcher (press add), then in the "Name" and "Comments" box type: "Filebrowser" or something similar, in the "Command" box type: "nautilus" (the picture should change to a shell). Click on the picture, and select something you feel is fitting (or create one), I selected the drawer. Now repeat the move/lock steps as with the GnoMenu. 

Now to add your list of windows on the panel: right-click > add to panel > window list > add. Right-click the separator (vertical line just before first window starts) and move it until you're happy with its location, then lock. 

Right-click > Add to Panel > Clock > add. Right-click it > preferences, adjust to how you'd like it. I think it looks best with the date, weather and temperature showing, but without seconds. Click the "Locations" tab at the top, then "Add". Start typing, pick your location (or nearest other) out of the drop-down list, then hit okay (Vista does not have this feature, but it looks Vista-ish anyway and is cool). Do the move/lock. 

Repeat steps for the volume control and network manager etc, too. For Update Manager, you'll have to create a custom launcher, and enter "/usr/bin/update-manager" in the "Command" box. 

After you've done this, repeat the first step and save your gnome-panel, but as vista.entries this time, so enter into the terminal:
```
gconftool-2 --dump /apps/panel > ~/settings/vista.entries
```

[SIZE="4"]**_Window Decoration, Icons, Cursors_**[/SIZE]

First things first, I know you've all been waiting on the window decorations - one of the nicest things about vista in the first place. 

You need to install the Segoe UI font that vista uses first, download from here: [COLOR="Blue"][http://home.arcor.de/salnet/segoe_ui.zip](http://home.arcor.de/salnet/segoe_ui.zip)[/COLOR]
Right-click the file, press extract and then copy the two .ttf files into /home/username/.fonts (NB, you will need to show hidden files, click on the "View" menu at the top to select this option). If .fonts does not exist, create it. 

You'll need to have emerald theme manager installed, so open up a Terminal and type: 
```
sudo apt-get install emerald
```
Now download [[COLOR="Blue"]Vista.emerald from here[/COLOR]](http://www.fileden.com/files/2007/5/20/1096740/Vista.emerald). Open up emerald theme manager by going to System > Preferences > Emerald Theme Manager. Choose the "Install" option, and navigate to the vista.emerald file, then hit OK. Click on the "Vista" theme (Note: nothing will happen yet). On the tab at the top, press "Emerald Settings", and out of the checkboxes, leave only the top (Show Tooltips for Buttons) checked. Titlebar Double-Click Action you can set to whatever you prefer, Vista has it as maximize/minimize, but I prefer shade. Set Compiz Decoration Blur Type to All Decoration. 

To apply this theme (and make it launch on start-up) go to System > Preferences > Sessions > add. Name: Emerald, Command: "emerald --replace" Comment: Vista. NOW REBOOT YOUR COMPUTER.

Now we need to add the icon theme, and the cursor theme. Download this iconset: [COLOR="Blue"][http://nuovext.pwsp.net/files/nuoveXT.2.2.tar.bz2](http://nuovext.pwsp.net/files/nuoveXT.2.2.tar.bz2)[/COLOR]
And download any black-icon set you wish, although I think the Mac4Lin cursor set works best with this theme, I have attached it with this post (ironic, as its a Mac cursor theme). 

Right-click on your desktop > Change Desktop Background > "Theme" tab and press "Install". Select the nuoveXT.2.2.tar.bz2 icon theme, and then apply when it asks you. Repeat for your cursor theme. Your "Fonts" tab should have Segoe UI as the window title font, mine looks like this: 
[img]http://img26.imageshack.us/img26/4710/screenshotappearancepre.png[/img]
The other fonts are Mac OSX fonts, part of [[COLOR="Blue"]this[/COLOR]](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23) tutorial will explain how to get them. 

[SIZE="3"]_OPTIONAL_[/SIZE]

Add the Windows Vista reflection image to your Window Decoration. You can download the reflection image from [[COLOR="Blue"]here[/COLOR]](http://www.gnome-look.org/CONTENT/content-files/91903-ccc6d283beaae42e0a3d9c6f82352f57.jpg) (right-click, save as). 

Open System > Preferences > CompizConfig Settings Manager, enable reflection. Click it, and replace the default reflection image with yours (hit the browse button and select it). 

[SIZE="4"]**_Screenlets and Background_**[/SIZE]

First off, background. I used this: 
[[IMG]http://img228.imageshack.us/img228/8311/vista.th.png[/IMG]](http://img228.imageshack.us/img228/8311/vista.png)
Save it, right-click on Desktop, Change Background, Add, select file. You can find loads more vista wallpapers simply by google-ing. 

Now screenlets. To install, type into a terminal:
```
sudo apt-get install screenlets
``` 

Now open the screenlets daemon: (Applications >) Accessories > Screenlets. Select "DigiClock" and on the left, check the boxes "Start/Stop" and "Auto start on login". Click and drag your DigiClock where you want it to go (see my [[COLOR="Blue"]final screenshot[/COLOR]](http://img217.imageshack.us/img217/3835/screenshotymr.png) as a reference). After it's where you want, right click it and select "Properties". Under the Options tab, check all of these boxes (and leave the rest unchecked): Stick to Desktop, Lock Position, Keep below, Skip Pager, Skip Taskbar. 

Now start the "Calendar" screenlet, and repeat the exact same steps as above. 

Download [[COLOR="Blue"]this CPU meter[/COLOR]](http://www.gnome-look.org/CONTENT/content-files/64599-CPU_Meter.tar.bz2), and then in the Screenlets Manager press "Install", select this and OK. Find "CPUMeter", and apply the same settings as above, then right-click it, and under "theme" select "vista". 

You may also choose to start other screenlets, such as the Places one like I have, or the weather screenlet, but these are the most common ones that Vista uses. If you're having trouble getting the weather screenlet to work, hold tight, I'm about to write a tutorial for that too, I will edit the link in here as soon as it's up. 


PLEASE let me know if I have forgotten anything, as I had a hell of a lot to try and remember to include, you can pm me here or email me at [[COLOR="Blue"]clampstand@gmail.com[/COLOR]](mailto:clampstand@gmail.com), thanks people.

---

