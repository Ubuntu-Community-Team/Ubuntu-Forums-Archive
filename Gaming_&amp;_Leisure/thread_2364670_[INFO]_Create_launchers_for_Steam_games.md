---
title: "[INFO] Create launchers for Steam games"
date: 2017-06-26
forum: Gaming &amp; Leisure
---

### Post by CatKiller on 2017-06-26
Because of [this bug]("https://github.com/ValveSoftware/steam-for-linux/issues/5012"), Steam no longer creates launchers for games installed through Steam. Here is a quick summary of how to create them manually.

Launchers are [desktop files]("https://www.freedesktop.org/wiki/Specifications/desktop-entry-spec/"). Essentially, this simply means that they are plain text files with the .desktop extension that contain the text [Desktop Entry]. There are a number of standardised fields that control things like the displayed names and the icon that is used.

The easiest way to get your new launcher is to amend an existing one. Since it's just a text file, dragging-and-dropping from the menu to an open text editor window works well. Otherwise, they are kept in **~/.local/share/applications**.

As an example, here is my launcher for the Steam version of Guns of Icarus Online, **~/.local/share/applications/Guns of Icarus Online.desktop**
```
[Desktop Entry]
Name=Guns of Icarus Online
Comment=Play this game on Steam
Exec=steam steam://rungameid/209080
Icon=steam_icon_209080
Terminal=false
Type=Application
Categories=Game;ActionGame;
```

The things you'll be interested in changing are the **filename**, the **Name=** entry, the **Exec=** path, the **Icon=** location and probably the **Categories=** field.

You can call the **filename** anything you want, as long as there isn't another file with the same name, and as long as it ends with .desktop. I just call my files after the name of the game, with spaces but without other special characters. If you create it in **~/.local/share/applications** it should be picked up by the menu system.

The **Name=** entry will be what is displayed in the menu, and everywhere else. If you're feeling flash you can put different translations in for different locales. What's listed as **Name=** will be the default. If you make this very long, your menu may become very wide.

The **Exec=** path is the command that will be executed. You can see that, in this case, the command is simply **steam** with the GameID passed as a parameter. You will need to replace the GameID with the right one for the game that you want to launch. There may well be a sensible way to extract that information from Steam, but I tend to just use SteamDB, since I'll be going there anyway.

Icons should sensibly be placed in **~/.local/share/icons/hicolor**. If you have icons of different sizes they can go in the appropriately named sub-folders. Steam puts them in **~/.local/share/icons/hicolor/<size>/apps/** which is perfectly fine. You don't need to specify the file extension, and you don't need to specify the full path if you put the icons within hicolor. If you have icons of different sizes, the theming system will automatically pick the icon of the most appropriate size to be displayed, so you'll get a larger icon with more detail on the Desktop, say, than in the menu. Steam names the icons as **steam_icon_<GameID>**, which is fine. You may find that Steam has already downloaded the icons for you and just not created the launcher. In which case, simply put the correct name in the **Icon=** location. Otherwise, and for games that have the default Steam icon, you can go to [SteamDB]("https://steamdb.info/") and search for the game you're interested in. This will provide you with the GameID and allow you to download the icons for the game for different platforms. If the only icon available is in the .ico format, the [Export Layers]("http://registry.gimp.org/node/28268") plugin for GIMP is useful for extracting individual images to use with your launcher.

The **Categories=** field determines where in the menu the launcher will be displayed. The [available sub-menus]("https://www.freedesktop.org/wiki/Specifications/menu-spec/") for the Games menu are
```
ActionGame
AdventureGame
ArcadeGame
BoardGame
BlocksGame
CardGame
KidsGame
LogicGame
RolePlaying
Shooter
Simulation
SportsGame
StrategyGame
```
Putting one of those categories after **Categories=Game;** should put it in the appropriate sub-menu of your Games menu.

Once you've created and saved your .desktop file you may need to run ```
update-menus
``` to update the menus. If you've added new icons, you may need to run ```
update-icon-caches ~/.local/share/icons/hicolor/
``` to refresh the list of available icons.

That's it: how to create or change launchers for Steam games. I hope that this is useful until the Steam bug gets fixed.

---

### Post by again? on 2017-06-30
Thanks for this info on the Steam Exec commands CatKiller.
I'll post my created Counter-Strike desktop and a script I use to load some game settings which can be adapted to suit 
different systems and may be helpful to others.
The script is used as a toggle between desktop and game mode computer settings which I added as a quicklist launcher to the desktop file.
Among other things it sets the desktop background to black so you know what mode you're in.
_**csgo.desktop**_
```
[Desktop Entry]
Name=CSGO
Comment=Play this game on Steam
Exec=steam steam://rungameid/730
Icon=steam_icon_730
Terminal=false
Type=Application
Categories=Game;Shooter;

Actions=GameSettingsToggle;

[Desktop Action GameSettingsToggle]
Name=Game Settings Toggle
Exec=/home/glen/scripts/game-settings.sh
```

_**game-settings.sh**_
```
#!/bin/bash
#set -x

# sets the colors when org.gnome.desktop.background picture-options 'none'
gsettings set org.gnome.desktop.background primary-color '#000000'
gsettings set org.gnome.desktop.background secondary-color '#000000'
gsettings set org.gnome.desktop.background color-shading-type 'solid'

background=$(gsettings get org.gnome.desktop.background picture-options) # checks for 'none'


if [ "$background" == "'none'" ] 
	
	### desktop mode ###
	then
		killall steam &
		megasync &
		easystroke &
		altyo --id=org.gtk.altyo &
		kupfer --no-splash &
		artha &
		nvidia-settings --load-config-only &
		buckle -f &
		gsettings set org.gnome.desktop.background picture-options 'zoom' &
		gsettings set org.gnome.desktop.background picture-uri 'file:///usr/share/backgrounds/adapta/tri-fadeno.jpg' &
		dconf reset /org/gnome/desktop/session/idle-delay &
		/home/glen/conky/toggleconky-Gnome &



	### game mode ###
	else
		killall artha &
		killall kupfer &
		killall altyo & 
		killall buckle &
		killall easystroke &
		killall conky &
		killall megasync &
		nvidia-settings --no-write-config --assign DigitalVibrance=1023 &
		gsettings set org.gnome.desktop.background picture-options 'none' &
		dconf write /org/gnome/desktop/session/idle-delay 'uint32 0' &
		
fi
exit 0
```

---

### Post by again? on 2017-07-30
Something else I found recently is you can set launch options for your game in steam itself.
If you right click on your game in the steam>library you can run a script before the game starts and when you exit.
Running my script it looks like this in steam.
```
/home/glen/scripts/game-settings.sh; %command%; /home/glen/scripts/game-settings.sh
```

You could also just use 2 separate scripts of your own.
```
*script-to-run-game-start.sh*; %command%; *script-to-run-game-exit.sh*

```
So no need to manually run a script when starting and exiting a game.
Just click the csgo launcher.

---

### Post by spaceman1980 on 2017-09-25
For those who don't want to waste any time (me), I recommend installing an application called Alacarte. You'll find that it is included in many distros, renamed something like "Main Menu". It essentially does all this for you, in a modern UI where you can just type in info and select an image. It's included in the standard repositories, so just open up a terminal and type: ```
sudo apt install alacarte
```

Hope this helps! ;)

---

### Post by Perfect Storm on 2017-10-06
_**Another workaround**_

Install Gnome Games app, it will pick up steam games even if there's no shortcut. It's in the repositories on for Ubuntu 17.04 and 17.10 I'm not sure if it's available on Ubuntu 16.04

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=277004&stc=1&d=1507292523[/IMG]

---

### Post by fancydeveloper on 2019-07-10
> **Artificial Intelligence said:**
> _**Another workaround**_

Install Gnome Games app, it will pick up steam games even if there's no shortcut. It's in the repositories on for Ubuntu 17.04 and 17.10 I'm not sure if it's available on Ubuntu 16.04

[[IMG]https://ubuntuforums.org/attachment.php?attachmentid=277004&stc=1&d=1507292523[/IMG]]("https://begamedev.com")

Oh this is great and easy way to do it! My preferable option

---

