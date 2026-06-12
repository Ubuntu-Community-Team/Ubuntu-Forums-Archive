---
title: "UKubuntizald Tutorial: Ubuntu + KDE Plasma Workspace + Compiz + Emerald"
date: 2009-10-14
forum: Desktop Environments
---

### Post by lovinglinux on 2009-10-14
> [COLOR="DarkRed"]**Note:**[/COLOR]This is for Karmic

**[COLOR="DarkRed"]Objective[/COLOR]**: 

The objective of this tutorial is to explain how to setup Ubuntu Karmic Koala to run with KDE Plasma Workspace, Compiz and Emerald (UKubuntizald :)).

**[COLOR="DarkRed"]Target Audience:[/COLOR]**
[LIST]
[*]those who want the eye candy and widgets of KDE but don't want to fully switch or login into each desktop environment separately.
[*]those seeking alternatives for replacing the upcoming gnome-shell and thus retaining the ability to use compiz inside gnome.
[/LIST]

[COLOR="DarkRed"]**Screenshot**[/COLOR]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=131895&stc=1&d=1255518251[/IMG]




[COLOR="DarkRed"]**Instructions**[/COLOR]

[COLOR="DarkRed"]
1) Enable proprietary drivers for your graphics card[/COLOR]

Go to "System >> Administration >> Hardware Drivers" and select the latest driver, then click activate.


[COLOR="DarkRed"]2 ) Enable Visual Effects[/COLOR]

Go to "System >> Preferences >> Appearance >> Visual Effects" and select the "Extra" mode.


[COLOR="DarkRed"]3) Install required applications[/COLOR]

Open "Applications >> Accessories >> Terminal" then paste the code below and run it to install the required packages:

```
sudo apt-get install compiz compizconfig-settings-manager emerald fusion-icon kde-minimal compiz-kde kdeplasma-addons plasma-scriptengine-python gtk2-engines-qtcurve
```


[COLOR="DarkRed"]4) Create scripts to launch each desktop[/COLOR]

**gnome-desktop**

```
gedit ~/Desktop/gnome-desktop.sh
```

Paste the code below and save it:

```
#!/bin/bash

killall fusion-icon
killall gnome-panel
killall plasma-desktop
gnome-panel &
fusion-icon &
```


**plasma-desktop**

```
gedit ~/Desktop/plasma-desktop.sh
```

Paste the code below and save it:

```
#!/bin/bash

killall fusion-icon
killall gnome-panel
killall plasma-desktop
plasma-desktop &
fusion-icon &
```

Make them executable:

```
chmod +x ~/Desktop/plasma-desktop.sh 
chmod +x ~/Desktop/gnome-desktop.sh
```


[COLOR="DarkRed"]5) Prevent the gnome-panel from auto-spawning[/COLOR]

Open gconf-editor from the terminal:

```
gconf-editor
```

Open "desktop >> gnome >> session >> required_components", then double-click the "panel" option, then remove the "gnome-panel" value and close it.

This will prevent the gnome-panel from auto-spawning when killing it.


[COLOR="DarkRed"]6) Install an emerald theme[/COLOR]

Download an emerald theme from gnome-look.org then open "System >> Preferences >> Emerald Theme Manager" then click "Import" and select the downloaded file.


[COLOR="DarkRed"]7) Kill gnome-panel and launch plasma-desktop[/COLOR]

Double-click the **plasma-desktop.sh** script in your desktop and select the "Run" option to kill gnome-panel and launch the plasma-desktop. To revert and go back to default gnome desktop, double-click the **gnome-desktop.sh** script.


[COLOR="DarkRed"]8- Replace the KDE Window Manager with Compiz and Emerald[/COLOR]

Right-click the fusion-icon in the tray, then "Select Window Manager >> Compiz", then "Select Window decorator >> Emerald".


[COLOR="DarkRed"]9) Configure the KDE applications to use the GTK engine[/COLOR]

From the KDE menu, select "Favorites >> System Settings >> Style" then select GTK+ in the "Widget style" option. Click "Apply". Then select the "Icons" options, select the "Humanity" icon set and click "Apply"


[COLOR="DarkRed"]**Appendix**[/COLOR]

The is the complete list of packages installed by this tutorial:

```
compiz compizconfig-backend-gconf compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compiz-wrapper libdecoration0 compizconfig-settings-manager python-compizconfig emerald libemeraldengine0 kde-minimal akonadi-server dolphin exiv2 kappfinder kde-icons-oxygen kde-minimal kde-window-manager kdebase kdebase-bin kdebase-data kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdebase-workspace-libs4+5 kdelibs-bin kdelibs5 kdelibs5-data kdepasswd kdepim-runtime kdepim-runtime-data kdepim-runtime-libs4 kdepimlibs-data kdepimlibs5 kdm kfind khelpcenter4 klipper konqueror konqueror-nsplugins konsole ksysguard ksysguardd kwrite libakonadiprivate1 libboost-program-options1.38.0 libclucene0ldbl libexiv2-5 libkdecorations4 libknotificationitem1 libkonq5 libkonq5-templates libkonqsidebarplugin4 libkwineffects1 liblzma0 libmodplug0c2 libmpcdec3 libplasma3 libpolkit-qt0 libqimageblitz4 libqt4-designer libqt4-network libqt4-opengl libqt4-phonon libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-webkit libsoprano4 libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x mysql-server-core-5.1 phonon-backend-xine plasma-dataengines-workspace plasma-widget-folderview plasma-widgets-workspace soprano-daemon systemsettings ttf-dejavu ttf-dejavu-extra compiz-kde compizconfig-backend-kconfig exiv2 kde-icons-oxygen kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-libs4+5 kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data khelpcenter4 libavahi-qt3-1 libclucene0ldbl libexiv2-5 libkdecorations4 libknotificationitem1 liblua50 liblualib50 liblzma0 libmodplug0c2 libmpcdec3 libplasma3 libqt3-mt libqt4-designer libqt4-network libqt4-opengl libqt4-phonon libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-webkit libsoprano4 libstreamanalyzer0 libstreams0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x phonon-backend-xine soprano-daemon ttf-dejavu ttf-dejavu-extra kdebase-workspace-wallpapers kdeplasma-addons kdewallpapers libkexiv2-7 liblancelot0 libmarble4 marble-data plasma-dataengines-addons plasma-runners-addons plasma-wallpapers-addons plasma-widget-lancelot plasma-widgets-addons libqt4-assistant libqt4-help libqt4-scripttools libqt4-test libqt4-xmlpatterns plasma-scriptengine-python python-kde4 python-qt4 python-sip4 gtk2-engines-qtcurve kde-style-qtcurve kwin-style-qtcurve
```

---

### Post by NRDNick on 2009-10-14
It's nice to know I'm not the only one a little worried about losing compiz when Ubuntu switches over to gnome-shell. Thanks for sharing this with everyone!

---

### Post by lovinglinux on 2009-10-14
> **NRDNick said:**
> It's nice to know I'm not the only one a little worried about losing compiz when Ubuntu switches over to gnome-shell. Thanks for sharing this with everyone!

Yep, I'm freaking out with gnome-shell :)

But I must say I'm really happy with this setup using plasma-desktop. I'm impressed with the quality of the widgets and the look of plasma-desktop. Right now I wouldn't switch completely to KDE, so this seems to be the perfect solution for me.

---

### Post by lovinglinux on 2009-10-15
> **lovinglinux said:**
> Right now I wouldn't switch completely to KDE, so this seems to be the perfect solution for me.

Strike that. I have fully switched to KDE and I couldn't be happier ;)

---

### Post by Joeb454 on 2009-11-15
Moved to Desktop Environments

---

### Post by Ms_Angel_D on 2009-11-15
Thanks so much for sharing this information, I wasn't aware that this was possible.

And Joeb454 thanks for moving the topic, now I can subscribe to it and not lose it ;)

---

### Post by lovinglinux on 2009-11-15
> **Joeb454 said:**
> Moved to Desktop Environments

Thanks. I forgot it was on Karmic development forum.

---

### Post by RazzyDaz on 2009-12-18
.

---

### Post by Struki on 2009-12-18
I tried the tutorial but some problems poped up. 
1. when I run the plasma script, al the gnome panels remain, my main panel and the AWN bar.
2. when I tried to unpack the theme downloaded from the site i got an error; 
         [I] gzip: stdin: not in gzip format
         tar: Child returned status 1
         tar: Exiting with failure status due to previous errors[/I]
3. I cant find the location: 
    Favorites >> System Settings >> Style
    to modify al that is said.    

But all in all it's an interesting concept and I sure would like to see it running on my lap. I would switch completley to kde but im just not ready, since im a fresh user.

---

### Post by Ero on 2010-01-01
Not so related question but, how GPU intensive is it top use this tweak. And, how much space would it require? I'm thinknig of doing this for my netbook Mini 9 but i'm not sure the GPU can handle it or if I even have the space for it.

Thanks

---

### Post by SuperSonic4 on 2010-01-01
According to htop plasma is using 0% of CPU (!) and 0.7% of RAM (which corresponds to 6.65mb)

KWin is using 5% CPU (0.646GHz) and 0.8% RAM (6.72mb). I am assuming KWin is roughly similar to compiz in this case.



I have to admit it looks very snazzy but I already have the KDE desktop - the integration is fantastic and long live dolphin!


EDIT: I think Lancelot would be better than Kicker for the menu on that setup

---

### Post by lovinglinux on 2010-01-01
> **SuperSonic4 said:**
> I have to admit it looks very snazzy but I already have the KDE desktop - the integration is fantastic and long live dolphin!

Yeah, I have switched to KDE too, after I wrote this tutorial. 

Long live dolphin, kate, ktorrent.... :)

---

### Post by lais on 2010-01-01
wow! this is amazing! I never knew that it is possible to have plasma running in Ubuntu.

One question though. If I dont use compiz and emerald, will it use KWin?

---

### Post by lovinglinux on 2010-01-01
> **lais said:**
> wow! this is amazing! I never knew that it is possible to have plasma running in Ubuntu.

One question though. If I dont use compiz and emerald, will it use KWin?

Yes, just don't install them and ignore steps 6 and 8.

---

### Post by lais on 2010-01-01
> **lovinglinux said:**
> Yes, just don't install them and ignore steps 6 and 8.

ok thanks. I was just curious. I am already using KDE. :)

---

### Post by GuitarPlayer2010 on 2010-04-28
I'm using Lucid 10.04 and Gnome 2.3, on a MacBook 2.1, and this worked for me. Thanks so much to the person who came up with this!
Its great using the plasma widgets on the desktop and the gnome ones in the upper panel. Truly the best of both worlds!
Best regards to the community.

---

### Post by lovinglinux on 2010-04-28
> **GuitarPlayer2010 said:**
> I'm using Lucid 10.04 and Gnome 2.3, on a MacBook 2.1, and this worked for me. Thanks so much to the person who came up with this!
Its great using the plasma widgets on the desktop and the gnome ones in the upper panel. Truly the best of both worlds!
Best regards to the community.

You are welcome. I haven't and won't be updating this tutorial, since I'm using full KDE now. But I'm glad it still working. Thanks for the feedback.

---

### Post by dh04000 on 2010-06-09
Anyway someone could make a spin of this modified Ubuntu as an installable iso using something like Remastersys backup?

For cowards like me, who are too intimidated to try this on their ubuntu install...

On Lucid, of coarse.

---

### Post by lovinglinux on 2010-06-09
> **dh04000 said:**
> Anyway someone could make a spin of this modified Ubuntu as an installable iso using something like Remastersys backup?

For cowards like me, who are too intimidated to try this on their ubuntu install...

On Lucid, of coarse.

Try on a Virtual Machine. You will need VirtualBox.

---

### Post by dh04000 on 2010-08-12
Here's my custom setup. 
[[IMG]http://img375.imageshack.us/img375/3184/screenshotgah.th.png[/IMG]](http://img375.imageshack.us/i/screenshotgah.png/)


Elementary eGTK, icons, and Nautilus
Plasma Desktop without panel
Gnome with top panel but no bottom
Awn with a glass-like setup
Loads of custom arrangements

---

### Post by Dobbie03 on 2010-10-17
Does anyone know if this will work on Maverick?

---

### Post by ALF102 on 2010-11-09
Letting you guys know that this works on Ubuntu 10.10 too. But with a few tweaks during one of the steps.

AT step 3:
lovinglinux shows that you need to paste this code into the terminal:

sudo apt-get install compiz compizconfig-settings-manager emerald fusion-icon **kde-minimal** compiz-kde kdeplasma-addons plasma-scriptengine-python gtk2-engines-qtcurve
note that when I try to execute this, it says that kde-minimal (the one I bold) won't install because is not avalaible anymore
So I install kde-plasma-desktop and with minimal set of application from the software center. Just search for "kde-minimal", it is somewhere in the technical items. 
Install that package first then execute the same code from step 3 in the terminal except have "kde-minimal" remove from the code.

Just in case after step 7 which is after you execute the plasma-esktop.sh and gnome-panel is still there, just log-out and log back in. Then run plasma-desktop.sh again.

Other than that, everything is working fine.


P:S in gnome, make sure you have plasma-desktop.sh set as startup application.

---

### Post by BryanFRitt on 2011-03-04
# Thanks for the tutorial!

# **KDE background vs GNOME background with this**
# Note: I did this on a system with a full installs of KDE, GNOME, and Compiz, logging in with the start GNOME login.
```
#!/bin/bash

# http://ubuntuforums.org/showthread.php?t=1291048

#killall fusion-icon # not installed
killall compiz
killall gnome-panel
killall plasma-desktop

# To get this to show gnome desktop, gnome icons must be set to be shown:
gconftool-2 --type boolean --set /apps/nautilus/preferences/show_desktop true
# otherwise only KDE desktop will be shown regardless of the order

# Stick the plasma-desktop one last you get a KDE desktop.
# Stick the gnome-panel one last you get a GNOME desktop.
# Also one can be used without the other.
plasma-desktop &
sleep 5
gnome-panel &

# sleep required so that Compiz can have use of edge where the panels are
# time may need to be adjusted for the computer you're trying this at
sleep 5
compiz &
#fusion-icon & # not installed


```

# Stick the plasma-desktop one last you get a KDE desktop.
# Stick the gnome-panel one last you get a GNOME desktop.
# Also one can be used without the other.

# There are lots of things that interact for this and you might want to write what happens down, and please post what you figure out
# Things to consider when messing with this:

# Rather or not the KDE pager is set to 'Different widgets for each desktop'
# Rather or not Compiz is set to more than one desktop,
#  note this is different from Compiz being set to more than one viewports
# Try running this from either by a GNOME login or a KDE login
# How to log out / Which menu to use
# Rather or not icons are set to be shown in either one, both, or none
# Shortcut usage, which shortcuts get activated in what situations
# Which Desktop/Viewport do applications get started from
# What background displayed when...
# When the panels disappear
# When does this freeze, and what to do about it


# You can set up system trays shortcuts / keyboard shortcuts, etc...
# gnome-panel_only
# plasma-desktop_only
# gnome-panel_plasma-desktop_combo
# plasma-desktop_gnome-panel_combo
# No_panels_at_all
# etc...

# ?you might need to kill your window decorator too?

# See also
#gconf-editor
#/desktop/gnome/session/required_components/windowmanager
# was
#Filemanaager	nautilus
#panel	gnome-panel
#windowmanager	gnome-wm

# Note: Doing this may be buggy, Don't blame me if things get messed up like KDE 'activities', GNOME 'Notification Area', KDE 'System Tray', 'Pannels', your Sanity, etc...

# To get out of a lot a freezes while playing around with this you can use commands like <Control><Alt>F2, then login info, then `TOP` k type in PID of item using too much CPU, then type q, then type `logout` then <Control><Alt>F7..F12 <-shortcut varies/changes

---

