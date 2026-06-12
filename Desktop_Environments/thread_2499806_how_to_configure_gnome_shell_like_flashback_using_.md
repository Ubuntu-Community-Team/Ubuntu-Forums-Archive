---
title: "how to: configure gnome shell like flashback using regular icons"
date: 2024-08-11
forum: Desktop Environments
---

### Post by Claus7 on 2024-08-11
Hello,

the following is a guide about using two panels under gnome-shell 46 and substituting symbolic icons with regular ones. 
There are some changes from gnome shell 46 to previous versions, yet most of the changes here will be applicable to previous versions as well.

edit1 
Some corrections about nautilus icons: there are different icons for the left hand side of nautilus and in the center. For example recent items, when empty show an icon on the center of nautilus. This has different size with the one on the left hand side. In some applications recent items icon is greater size, so this was fixed. The same for the trash icon.
edit2
One of the "troublesome" icons are those on the right hand side of the top panel. If 1em size is chosen under gnome shell theme, then one has to wait for a couple of minutes until they take the correct form. If specific size is provided, then they take the right form almost right away.

1) Extensions needed: 
```
gnome-extensions list

```

> 
blur-my-shell@aunetx -> window list extension blur should be enabled
[email]burn-my-windows@schneegans.github.com[/email]
[email]caffeine@patapon.info[/email]
[email]compiz-windows-effect@hermes83.github.com[/email]
[email]compiz-alike-magic-lamp-effect@hermes83.github.com[/email]
[email]CoverflowAltTab@palatis.blogspot.com[/email]
[email]mute-unmute@mcast.gnomext.com[/email]
[email]Panel_Favorites@rmy.pobox.com[/email]
quick-settings-avatar@d-go
[email]Move_Clock@rmy.pobox.com[/email]
[email]CustomizeClockOnLockScreen@pratap.fastmail.fm[/email]
[email]AddCustomTextToWorkSpaceIndicators@pratap.fastmail.fm[/email]
quick-settings-tweaks@qwreey
[email]RecentItems@bananenfisch2.net[/email]
[email]minimizeall@scharlessantos.org[/email]
[email]date-menu-formatter@marcinjakubowski.github.com[/email]
[email]quick-lang-switch@ankostis.gmail.com[/email]

[email]ding@rastersoft.com[/email]
[email]ubuntu-appindicators@ubuntu.com[/email]
[email]apps-menu@gnome-shell-extensions.gcampax.github.com[/email]
[email]drive-menu@gnome-shell-extensions.gcampax.github.com[/email]
[email]places-menu@gnome-shell-extensions.gcampax.github.com[/email]
[email]user-theme@gnome-shell-extensions.gcampax.github.com[/email]
[email]window-list@gnome-shell-extensions.gcampax.github.com[/email]

two modifications are needed:
i) correct window list fonts-background and add space on the left hand side for show desktop button
> DARK

/*
 * SPDX-FileCopyrightText: 2012 Florian Müllner <fmuellner@gnome.org>
 * SPDX-FileCopyrightText: 2013 Giovanni Campagna <gcampagna@src.gnome.org>
 *
 * SPDX-License-Identifier: GPL-2.0-or-later
 */

.window-list {
	spacing: 2px;
	font-size: 13pt;/*10pt;*/
	padding-left: 42px; /*this alone solves padding problem in any case*/
}

.bottom-panel {
	background-color: #000000;
	border-top-width: 0px;
	padding: 2px;
}

.window-button {
	padding: 1px;/*2px, 1px;*/
}

.window-button:first-child:ltr {
	padding-left: 2px;
}

.window-button:last-child:rtl {
	padding-right: 2px;
}

.window-button-box {
	spacing: 4px;
}

.window-button > StWidget,
.window-picker-toggle > StWidget {
	color: #bbb;
	background-color: #1d1d1d;
	border-radius: 4px;
	padding: 3px 6px 1px;
    transition: 100ms ease;
}

.window-button > StWidget {
	-st-natural-width: 18.75em;
	max-width: 18.75em;
}

.window-button:hover > StWidget,
.window-picker-toggle:hover > StWidget {
	color: #fff;
	background-color: #303030;
}

.window-button:active > StWidget,
.window-button:focus > StWidget {
	color: #fff;
	background-color: #3f3f3f;
}

.window-button.focused > StWidget,
.window-picker-toggle:checked > StWidget {
	color: #fff;
	background-color: #3f3f3f;
}

.window-button.focused:active > StWidget,
.window-picker-toggle:checked:active > StWidget {
	color: #fff;
	background-color: #3f3f3f;
}

.window-button.minimized > StWidget {
	color: #666;
	background-color: #161616;
}

.window-button.minimized:active > StWidget {
	color: #666;
	background-color: #161616;
}

.window-button-icon {
	width: 24px;
	height: 24px;
}

.window-list-workspace-indicator .status-label-bin {
	background-color: rgba(200, 200, 200, 0.3);
	padding: 0 3px;
	margin: 3px;
}

.window-list-workspace-indicator .workspaces-box {
	spacing: 3px;
	padding: 3px;
}

.window-list-workspace-indicator .workspace {
	width: 30pt;/*52px;*/
	border-radius: 4px;
	background-color: #1e1e1e;
}

.window-list-workspace-indicator .workspace.active {
	background-color: #3f3f3f;
}

.window-list-window-preview {
	background-color: #bebebe;
	border-radius: 1px;
}

.window-list-window-preview.active {
	background-color: #d4d4d4;
}

.notification {
	font-weight: normal;
}

LIGHT

/*
 * SPDX-FileCopyrightText: 2013 Florian Müllner <fmuellner@gnome.org>
 * SPDX-FileCopyrightText: 2015 Jakub Steiner <jimmac@gmail.com>
 *
 * SPDX-License-Identifier: GPL-2.0-or-later
 */

@import url("stylesheet-dark.css");

#panel.bottom-panel {
    border-top-width: 1px;
    border-bottom-width: 0px;
    height: 1.8em;/*2.25em ;*/
    padding: 2px;
  }

  .bottom-panel .window-button > StWidget,
  .bottom-panel .window-picker-toggle > StWidget {
    color: #bbb;/*#2e3436;*/
    background-color: black;/*#eee;*/
    border-radius: 2px;/*3px;*/
    padding: 3px 6px 1px;
    box-shadow: inset 1px 1px 4px rgba(255,255,255,0.5);/*none;*/
    text-shadow: 1px 1px 4px rgba(0,0,0,0.5);/*none;*/
    /*border: 1px solid rgba(0,0,0,0.2);*/
  }

  .bottom-panel .window-button > StWidget {
    -st-natural-width: 12em;/*18.7em;*/
    max-width: 12em;/*18.75em;*/
  }

  .bottom-panel .window-button:hover > StWidget,
  .bottom-panel .window-picker-toggle:hover > StWidget {
    color: white;
    background-color: #1f1f1f;/*background-color: #f9f9f9;*/
  }

  .bottom-panel .window-button:active > StWidget,
  .bottom-panel .window-button:focus > StWidget {
    box-shadow: inset 2px 2px 4px rgba(255,255,255,0.5);/*inset 0 1px 3px rgba(0,0,0,0.1);*/
  }

  .bottom-panel .window-button.focused > StWidget,
  .bottom-panel .window-picker-toggle:checked > StWidget {
    background-color: white;/*#ccc;*/
    box-shadow: inset 1px 1px 4px rgba(255,255,255,0.7);/*inset 0 1px 3px rgba(0,0,0,0.1);*/
  }

  .bottom-panel .window-button.focused:hover > StWidget {
    background-color: #e9e9e9;
  }

  .bottom-panel .window-button.minimized > StWidget {
    /*color: #888;*/
    box-shadow: inset -1px -1px 4px rgba(255,255,255,0.5);/*none;*/
  }

/* workspace switcher */
.window-list-workspace-indicator .workspace {
  border: 2px solid #f6f5f4;
  background-color: #ccc;
}

.window-list-workspace-indicator .workspace.active {
  border-color: #888;
}

.window-list-window-preview {
  background-color: #ededed;
  border: 1px solid #ccc;
}

.window-list-window-preview.active {
  background-color: #f6f5f4;
}

ii) add show desktop button on the left hand side of window list extension
from extension Minimize All -> change extension.js file

> /*
  Copyright (c) 2013-2021, Charles Santos Silva (oi@charles.dev.br)

  Redistribution and use in source and binary forms, with or without
  modification, are permitted provided that the following conditions are met:
    * Redistributions of source code must retain the above copyright
      notice, this list of conditions and the following disclaimer.
    * Redistributions in binary form must reproduce the above copyright
      notice, this list of conditions and the following disclaimer in the
      documentation and/or other materials provided with the distribution.

  THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND
  ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
  WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
  DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER BE LIABLE FOR ANY
  DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
  (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
  LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
  ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
  (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
  SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
*/

import St from 'gi://St'; 
import * as Main from 'resource:///org/gnome/shell/ui/main.js';
import Gio from 'gi://Gio';
import {Extension} from 'resource:///org/gnome/shell/extensions/extension.js';
import * as Layout from 'resource:///org/gnome/shell/ui/layout.js';

let text, button;

function _hide() {
    Main.uiGroup.remove_actor(text);
    text = null;
}

function canMinimize(window, c_minimized) {
	if (c_minimized && window.minimized)
		return false;

	if (window.is_skip_taskbar !== undefined)
		return !window.is_skip_taskbar();

	if (window.can_minimize == undefined)
		return true;

	return window.can_minimize();

}

function _click(){
        let windows = global.workspace_manager.get_active_workspace().list_windows();

	if (windows.length == 0) {
 		Main.overview.hide();
		return;
	}

	// Check if has any window not minimized
	let minimize = global.workspace_manager.get_active_workspace().list_windows().filter(function(w){return canMinimize(w, true);}).length > 0 || Main.overview._shown;

	global.display.sort_windows_by_stacking(windows).filter(function(w){return canMinimize(w, false);}).forEach(function(window){
		if (minimize)
			window.minimize();
		else
			window.unminimize();
	});

	if (minimize)
		Main.overview.hide();
}


function init(extensionMeta) {

}

let ht=40; /*height: 30 desk, 40 lap*/
let wi=40; /*width: 34 desk, 40 lap*/

export default class extends Extension {

        enable() {
	button = new St.Bin({ style_class: 'panel-button', name: 'desktopButton', reactive: true, can_focus: true, track_hover: true, height: ht, width: wi }); /*added name (for css file), height and width*/
	/*let gicon = Gio.icon_new_for_string(Me.path + '/icons/minimize-symbolic.svg');*/
	let icon = new St.Icon({ icon_name: 'desktop',
                                 style_class: 'system-status-icon' });
	button.set_child(icon);
	button.connect('button-press-event', _click);

	/*Main.panel._rightBox.insert_child_at_index(button, 0);*/
        let pMonitor = Main.layoutManager.primaryMonitor; /*define it here so as to use pMonitor later)*/
        
        button.set_position(1,pMonitor.height-wi); /*994 or 1038 for laptop, distance of icon from left and...*/
                                                   /*...top of the screen (screen resolution- ~button height)*/

	Main.layoutManager.addChrome(button,{
	affectsInputRegion: true,
	trackFullscreen: true
	});	
	
}

        disable() {
	/*Main.panel._rightBox.remove_child(button);
	button.destroy();
	button = null;*/
	Main.layoutManager.removeChrome(button);
	}

}

2) install gnome icons and copy it under ~/.icons
name it as Gnome_noble_blue
change the name also in the index file

download humanities icon from gnome look org 

use the following script to add regular icons
```

#transfer icon files from Humanities blue to Gnome blue noble
#Folder icons under Places menu
#16
i=16
echo $i
cd ~/.icons
cd Gnome_blue_noble
cd ${i}x${i}/places
rm ./*
cp ~/.icons/Humanities-Blue/places/${i}/* ./

#22
i=22
echo $i
cd ~/.icons
cd Gnome_blue_noble
cd ${i}x${i}/places
rm ./*
cp ~/.icons/Humanities-Blue/places/${i}/* ./

#24
i=24
echo $i
cd ~/.icons
cd Gnome_blue_noble
cd ${i}x${i}/places
rm ./*
cp ~/.icons/Humanities-Blue/places/${i}/* ./

#32
i=32
echo $i
cd ~/.icons
cd Gnome_blue_noble
cd ${i}x${i}/places
rm ./*
cp ~/.icons/Humanities-Blue/places/${i}/* ./

#48
i=48
echo $i
cd ~/.icons
cd Gnome_blue_noble
cd ${i}x${i}/places
rm ./*
cp ~/.icons/Humanities-Blue/places/${i}/* ./

#icons under SETTINGS
icon_dir=Gnome_blue_noble

#scalable/apps
#the names of the symbolic icons of Settings are found under hicolor folder (highcolor/scalable/apps
#e.g. org.gnome.Settings-about-symbolic.svg)
#they go to: ~/.icons/Humanities-Blue/scalable/apps
cd /usr/share/icons/hicolor/scalable/apps
#write all icon files of settings in one file (which are symbolic no colored)
ls -a | sort | grep org.gnome.Settings > ~/.icons/settings.txt
cd ~/.icons/
#store their names in array lines
readarray lines < settings.txt
#substitute svg with png
linesg=("${lines[@]/svg/png}")

cd "$icon_dir"
mkdir -p scalable/apps

awk -i inplace '/^Directories/ {$0=$0",scalable/apps"}1' index.theme

echo " " >> index.theme

echo "[scalable/apps]
MinSize=1
Size=128
MaxSize=256
Context=Applications
Type=Scalable" >> index.theme

#the order of icons should be:
names=(
network
bluetooth
#--------
displays
sound
power
multitasking
appearance
#ubuntu desktop - added below specifically, found under: /usr/share/icons/Yaru/scalable/categories
#--------
applications
notifications
search
online-accounts
sharing
#--------
mouse 
keyboard
color
printers
#--------
accessibility
privacy
#system
region
time
users
#remote - added below explicitly, found under: /usr/share/icons/Yaru/scalable/categories
#secure utilities - - added below explicitly, found under: /usr/share/icons/Yaru/scalable/apps
about)

#download/copy the desired icons
#network
sudo convert -background none /usr/share/icons/Humanity/apps/48/gnome-network-properties.svg ~/.icons/network.png
#bluetooth
sudo convert -background none /usr/share/icons/Humanity/apps/48/bluetooth.svg ~/.icons/bluetooth.png

#displays
sudo convert -background none /usr/share/icons/Humanity/apps/48/gnome-display-properties.svg ~/.icons/displays.png
#sound
sudo convert -background none /usr/share/icons/Humanity/apps/48/preferences-sound.svg ~/.icons/sound.png
#power
sudo convert -background none /usr/share/icons/Humanity/apps/48/gnome-power-manager.svg ~/.icons/power.png
#multitasking
sudo convert -background none /usr/share/icons/hicolor/scalable/apps/org.rncbc.qpwgraph.svg ~/.icons/multitasking.png
#appearance
sudo convert -background none /usr/share/icons/Humanity/apps/48/gnome-settings-theme.svg ~/.icons/appearance.png
#ubuntu-desktop
sudo convert -background none /usr/share/icons/Humanity/categories/48/applications-viewers.svg ~/.icons/"$icon_dir"/scalable/apps/preferences-ubuntu-panel-symbolic.png

#applications
cp ~/Pictures/icons/apps.resized.png ~/.icons/org.gnome.Settings-applications-symbolic.png
#notifications
sudo convert -background none /usr/share/icons/Humanity/apps/48/gnome-panel-notification-area.svg ~/.icons/notifications.png
#search
sudo cp /usr/share/icons/gnome/48x48/actions/stock_search.png ~/.icons/search.png
#online accounts
sudo cp /usr/share/icons/Yaru/48x48/categories/preferences-desktop-online-accounts.png ~/.icons/online-accounts.png
#sharing
sudo cp /usr/share/icons/Yaru/48x48/categories/preferences-system-sharing.png ~/.icons/sharing.png

#mouse
sudo cp /usr/share/icons/gnome/48x48/devices/input-mouse.png ~/.icons/mouse.png
#keyboard
sudo cp /usr/share/icons/gnome/48x48/devices/keyboard.png ~/.icons/keyboard.png
#color
sudo cp /usr/share/icons/Yaru/256x256@2x/categories/preferences-color.png ~/.icons/color.png
#printer
sudo convert -background none /usr/share/icons/Humanity/devices/48/printer.svg ~/.icons/printers.png

#accessibility
sudo convert -background none /usr/share/icons/Humanity/apps/48/preferences-desktop-accessibility.svg ~/.icons/accessibility.png
#privacy
sudo cp /usr/share/icons/gnome/48x48/apps/preferences-system-privacy.png ~/.icons/privacy.png

#system
mkdir -p scalable/categories

awk -i inplace '/^Directories/ {$0=$0",scalable/categories"}1' index.theme

echo " " >> index.theme

echo "[scalable/categories]
MinSize=16
Size=128
MaxSize=256
Context=Categories
Type=Scalable" >> index.theme
#--
mkdir -p scalable/org.gnome.Settings

awk -i inplace '/^Directories/ {$0=$0",scalable/org.gnome.Settings"}1' index.theme

echo " " >> index.theme

echo "[scalable/org.gnome.Settings]
MinSize=16
Size=16
MaxSize=256
Context=Org.Gnome.Settings
Type=Scalable" >> index.theme


sudo convert -background none /usr/share/icons/Humanity/apps/48/locale.svg ~/.icons/region.png
sudo convert -background none /usr/share/icons/Humanity/apps/48/time-admin.svg ~/.icons/time.png
sudo convert -background none /usr/share/icons/Humanity/apps/48/system-users.svg ~/.icons/users.png
convert -background none ~/.icons/Humanities-Blue/apps/48/gnome-remote-desktop.svg ~/.icons/"$icon_dir"/scalable/org.gnome.Settings/org.gnome.Settings-remote-desktop-symbolic.png
convert -background none ~/.icons/Humanities-Blue/apps/48/gksu-root-terminal.svg ~/.icons/"$icon_dir"/scalable/apps/utilities-terminal-symbolic.png
sudo cp /usr/share/icons/Yaru/32x32/actions/help-about.png ~/.icons/about.png

cd ~/.icons/$icon_dir/32x32/apps/
cp preferences-system-privacy.png preferences-system-privacy-symbolic.symbolic.png

cd ~/.icons/ 

#match name of file (names) with the name it has to have to appear under settings (linesg)
for i in "${names[@]}";
do 
   for j in "${linesg[@]}";
   do 
      jc=${j#*-}  #remove from beginning
      jc=${jc%-*} #remove from end
      if [[ "$i" =~ "$jc"  ]]; 
      then echo "FOUND $i" ;cp $i.png $j; 
      else   
      echo "NOT FOUND $i $j" 
      fi 
   done   
done

#move icons to scalable folder
mv org.gnome.Settings* "$icon_dir"/scalable/apps/
find . -maxdepth 1 -type f -iname '*.png' -not -iname 'brand-logo-symbolic.png' -exec rm -f {} \;

#fix airplane mode under settings no icon
sudo cp /usr/share/icons/Yaru/scalable/status/airplane-mode-symbolic.svg ~/.icons/"$icon_dir"/scalable/status/

#fix under search -list- icon
cd "$icon_dir"
mkdir -p scalable/ui
sudo cp /usr/share/icons/Yaru/scalable/ui/list-drag-handle-symbolic.svg ~/.icons/"$icon_dir"/scalable/ui/

awk -i inplace '/^Directories/ {$0=$0",scalable/ui"}1' index.theme

echo " " >> index.theme

echo "[scalable/ui]
Context=UI
Size=16
MinSize=8
MaxSize=512
Type=Scalable" >> index.theme

#fix under sharing the edit icon - look underneath

#TOP PANEL
#cd "$icon_dir"
mkdir -p scalable/actions
sudo cp /usr/share/icons/Humanity/actions/16/system-shutdown.svg ~/.icons/"$icon_dir"/scalable/actions
cp ~/.icons/"$icon_dir"/scalable/actions/system-shutdown.svg ~/.icons/"$icon_dir"/scalable/actions/system-shutdown-panel.svg
cp ~/.icons/"$icon_dir"/scalable/actions/system-shutdown.svg ~/.icons/"$icon_dir"/scalable/actions/system-shutdown-symbolic.svg

awk -i inplace '/^Directories/ {$0=$0",scalable/actions"}1' index.theme

echo " " >> index.theme

echo "[scalable/actions]
MinSize=1
Size=128
MaxSize=256
Context=Actions
Type=Scalable" >> index.theme

#edit icon (it is a grey icon, yet it is displayed black)
sudo cp /usr/share/icons/Yaru/scalable/actions/document-edit-symbolic.svg ~/.icons/"$icon_dir"/scalable/actions/

#QUICK SETTINGS
#the name of notifications - do not disturb icon
#they go to: ~/.icons/Humanities-Blue/scalable/status
mkdir -p scalable/status
sudo cp /usr/share/icons/Yaru/scalable/status/notifications-disabled-symbolic.svg ./scalable/status

awk -i inplace '/^Directories/ {$0=$0",scalable/status"}1' index.theme

echo " " >> index.theme

echo "[scalable/status]
MinSize=1
Size=128
MaxSize=256
Context=Status
Type=Scalable" >> index.theme

#bluetooth
mkdir -p ~/.icons/"$icon_dir"/status/24/
sudo cp /usr/share/icons/Humanity/apps/24/bluetooth.svg ~/.icons/"$icon_dir"/status/24/bluetooth-active.svg
sudo cp /usr/share/icons/Yaru/24x24@2x/status/bluetooth-disabled.png ~/.icons/"$icon_dir"/status/24/

awk -i inplace '/^Directories/ {$0=$0",status/24"}1' index.theme

echo " " >> index.theme

echo "[status/24]
MinSize=1
Size=24
MaxSize=256
Context=Status
Type=Fixed" >> index.theme

#icons of NAUTILUS-FILES LEFT
rm -r ~/.icons/Gnome_blue_noble/256x256/places
#Recent - size does matter for non nautilus programs (and for center of nautilus the bigger the better, yet compromize)
mkdir -p ~/.icons/"$icon_dir"/categories/scalable/ 
cp ~/.icons/"$icon_dir"/22x22/actions/document-open-recent.png ~/.icons/"$icon_dir"/categories/scalable/document-open-recent-symbolic.png

awk -i inplace '/^Directories/ {$0=$0",categories/scalable"}1' index.theme

echo " " >> index.theme

echo "[categories/scalable]
MinSize=1
Size=24
MaxSize=256
Context=Categories
Type=Scalable" >> index.theme

mkdir -p ~/.icons/"$icon_dir"/places/scalable/ 
#cp ~/.icons/"$icon_dir"/48x48/actions/document-open-recent.png ~/.icons/"$icon_dir"/categories/scalable/document-open-recent-symbolic.png
#Recent icon in the center of nautilus
cp ~/.icons/"$icon_dir"/256x256/actions/document-open-recent.png ~/.icons/"$icon_dir"/scalable/actions/document-open-recent-symbolic.png

#starred
#already from gnome!

#Home, Desktop, Documents, Downloads, Music, Pictures, Videos, Trash
#Home 
cd ~/.icons/"$icon_dir"/places/scalable/

cp ~/.icons/"$icon_dir"/24x24/places/folder-home.svg ~/.icons/"$icon_dir"/places/scalable/
convert -background none folder-home.svg folder_home-symbolic.png 
#inkscape folder-home.svg -w 100 -h 100 -o folder_home-symbolic.png
#with inkspape nice icon, great size
ln -s folder_home-symbolic.png folder-home-symbolic.png 
ln -s folder_home-symbolic.png user-home-symbolic.png

#Desktop 
cp ~/.icons/"$icon_dir"/24x24/places/user-desktop.svg ~/.icons/"$icon_dir"/places/scalable/
convert -background none user-desktop.svg folder_desktop-symbolic.png
ln -s folder_desktop-symbolic.png folder-desktop-symbolic.png 
ln -s folder_desktop-symbolic.png user-desktop-symbolic.png

#Documents 
cp ~/.icons/"$icon_dir"/24x24/places/folder-documents.svg ~/.icons/"$icon_dir"/places/scalable/
convert -background none folder-documents.svg folder_documents-symbolic.png
ln -s folder_documents-symbolic.png folder-documents-symbolic.png 
ln -s folder_documents-symbolic.png user-documents-symbolic.png

#Downloads 
cp ~/.icons/"$icon_dir"/24x24/places/folder-downloads.svg ~/.icons/"$icon_dir"/places/scalable/
convert -background none folder-downloads.svg folder_download-symbolic.png
ln -s folder_download-symbolic.png folder-download-symbolic.png
ln -s folder_download-symbolic.png user-download-symbolic.png

#Music 
cp ~/.icons/"$icon_dir"/24x24/places/folder-music.svg ~/.icons/"$icon_dir"/places/scalable/
convert -background none folder-music.svg folder_music-symbolic.png
ln -s folder_music-symbolic.png folder-music-symbolic.png 
ln -s folder_music-symbolic.png user-music-symbolic.png

#Pictures 
cp ~/.icons/"$icon_dir"/24x24/places/folder-pictures.svg ~/.icons/"$icon_dir"/places/scalable/
convert -background none folder-pictures.svg folder_pictures-symbolic.png
ln -s folder_pictures-symbolic.png folder-pictures-symbolic.png 
ln -s folder_pictures-symbolic.png user-pictures-symbolic.png

#Videos 
cp ~/.icons/"$icon_dir"/24x24/places/folder-videos.svg ~/.icons/"$icon_dir"/places/scalable/
convert -background none folder-videos.svg folder_videos-symbolic.png
ln -s folder_videos-symbolic.png folder-videos-symbolic.png 
ln -s folder_videos-symbolic.png user-videos-symbolic.png

cd ~/.icons/"$icon_dir"/

awk -i inplace '/^Directories/ {$0=$0",places/scalable"}1' index.theme

echo " " >> index.theme

echo "[places/scalable]
MinSize=1
Size=24
MaxSize=256
Context=Places
Type=Scalable" >> index.theme

#Trash - size does matter for the left hand side of nautilus and other applications
#empty
mkdir -p symbolic/places
sudo cp /usr/share/icons/Yaru/16x16/places/user-trash.png ~/.icons/"$icon_dir"/symbolic/places/user-trash-symbolic.png

awk -i inplace '/^Directories/ {$0=$0",symbolic/places"}1' index.theme

echo " " >> index.theme

echo "[symbolic/places]
Context=Places
Size=16
MinSize=8
MaxSize=512
Type=Scalable" >> index.theme 

#full - left hand side of nautilus and other applications
mkdir -r symbolic/status
sudo cp /usr/share/icons/Yaru/16x16/status/user-trash-full.svg ~/.icons/"$icon_dir"/symbolic/status/user-trash-full-symbolic.png

awk -i inplace '/^Directories/ {$0=$0",symbolic/status"}1' index.theme

echo " " >> index.theme

echo "[symbolic/status]
MinSize=8
Size=16
MaxSize=256
Context=Status
Type=Scalable" >> index.theme 

#icons of NAUTILUS-FILES
mkdir -p ~/.icons/"$icon_dir"/places/

#22
cp -r ~/.icons/Humanities-Blue/places/22/ ~/.icons/"$icon_dir"/places/

awk -i inplace '/^Directories/ {$0=$0",places/22"}1' index.theme

echo " " >> index.theme

echo "[places/22]
MinSize=1
Size=22
MaxSize=256
Context=Places
Type=Fixed" >> index.theme

#24
cp -r ~/.icons/Humanities-Blue/places/24/ ~/.icons/"$icon_dir"/places/

awk -i inplace '/^Directories/ {$0=$0",places/24"}1' index.theme

echo " " >> index.theme

echo "[places/24]
MinSize=1
Size=24
MaxSize=256
Context=Places
Type=Fixed" >> index.theme

#32
cp -r ~/.icons/Humanities-Blue/places/32/ ~/.icons/"$icon_dir"/places/

awk -i inplace '/^Directories/ {$0=$0",places/32"}1' index.theme

echo " " >> index.theme

echo "[places/32]
MinSize=1
Size=32
MaxSize=256
Context=Places
Type=Fixed" >> index.theme

#48
cp -r ~/.icons/Humanities-Blue/places/48/ ~/.icons/"$icon_dir"/places/

awk -i inplace '/^Directories/ {$0=$0",places/48"}1' index.theme

echo " " >> index.theme

echo "[places/48]
MinSize=1
Size=48
MaxSize=256
Context=Places
Type=Fixed" >> index.theme

#64
cp -r ~/.icons/Humanities-Blue/places/64/ ~/.icons/"$icon_dir"/places/

awk -i inplace '/^Directories/ {$0=$0",places/64"}1' index.theme

echo " " >> index.theme

echo "[places/64]
MinSize=1
Size=64
MaxSize=256
Context=Places
Type=Fixed" >> index.theme

#128
cp -r ~/.icons/Humanities-Blue/places/128/ ~/.icons/"$icon_dir"/places/

awk -i inplace '/^Directories/ {$0=$0",places/128"}1' index.theme

echo " " >> index.theme

echo "[places/128]
MinSize=1
Size=128
MaxSize=256
Context=Places
Type=Fixed" >> index.theme

#change Top panel home icon
cp ~/.icons/Gnome_blue_noble/places/64/folder-home.svg ~/.icons/Gnome_blue_noble/scalable/apps/org.gnome.Nautilus.svg

#Top Panel Apps icons
mkdir -p ~/.icons/"$icon_dir"/categories/48/
sudo cp /usr/share/icons/Humanity/categories/48/applications-libraries.svg ~/.icons/"$icon_dir"/categories/48/

awk -i inplace '/^Directories/ {$0=$0",categories/48"}1' index.theme

echo " " >> index.theme

echo "[categories/48]
MinSize=1
Size=48
MaxSize=256
Context=Categories
Type=Fixed" >> index.theme

#Desktop Icons - Trash empty
sudo cp /usr/share/icons/Humanity/places/64/user-trash.svg ~/.icons/"$icon_dir"/scalable/places/
sudo cp /usr/share/icons/Humanity/places/48/user-trash-full.svg ~/.icons/"$icon_dir"/48x48/status/
#cp ~/.icons/"$icon_dir"/scalable/places/user-trash-full.svg ~/.icons/"$icon_dir"/scalable/places/edittrash.svg

#lock icon when compressing files
sudo cp /usr/share/icons/Yaru/16x16/categories/preferences-system-brightness-lock.png /home/claus/.icons/"$icon_dir"/scalable/actions/system-lock-screen-symbolic.png

#MIMES - how icons inside nautilus look like
sudo cp -r /usr/share/icons/Humanity/mimes/ ~/.icons/"$icon_dir"/

awk -i inplace '/^Directories/ {$0=$0",mimes/16"}1' index.theme

echo " " >> index.theme

echo "[mimes/16]
Size=16
Context=MimeTypes
Type=Fixed" >> index.theme

awk -i inplace '/^Directories/ {$0=$0",mimes/22"}1' index.theme

echo " " >> index.theme

echo "[mimes/22]
Size=22
Context=MimeTypes
Type=Fixed" >> index.theme

awk -i inplace '/^Directories/ {$0=$0",mimes/24"}1' index.theme

echo " " >> index.theme

echo "[mimes/24]
Size=24
Context=MimeTypes
Type=Fixed" >> index.theme

awk -i inplace '/^Directories/ {$0=$0",mimes/32"}1' index.theme

echo " " >> index.theme

echo "[mimes/32]
Size=32
Context=MimeTypes
Type=Fixed" >> index.theme

awk -i inplace '/^Directories/ {$0=$0",mimes/48"}1' index.theme

echo " " >> index.theme

echo "[mimes/48]
Size=48
Context=MimeTypes
Type=Fixed" >> index.theme

awk -i inplace '/^Directories/ {$0=$0",mimes/64"}1' index.theme

echo " " >> index.theme

echo "[mimes/64]
Size=64
Context=MimeTypes
Type=Fixed" >> index.theme

awk -i inplace '/^Directories/ {$0=$0",mimes/128"}1' index.theme

echo " " >> index.theme

echo "[mimes/128]
Size=128
Context=MimeTypes
Type=Fixed" >> index.theme

awk -i inplace '/^Directories/ {$0=$0",mimes/256"}1' index.theme

echo " " >> index.theme

echo "[mimes/256]
Size=256
Context=MimeTypes
Type=Fixed" >> index.theme

```

3) In order to use regular icons then in the desired Yaru theme, the following addition/change to gnome-shell.css should take place:
> 
/* Global Values */
* {
  -st-icon-style: regular !important; }
stage {
  font-size: 16.5px;
  color: #3D3D3D; }


4) Add icons to Apps extension for categories (it is language sensitive, so it is working only for english) by modifying extension.js file:

>     const APPLICATION_ICON_SIZE = 24; /*changes the size of subcategory application e.g. from Games Chess*/
    (if we want bigger icons then change 24 to 32 and change also the line):
    const MENU_HEIGHT_OFFSET = 182; /*changes height of menu 132*/
      
class CategoryMenuItem extends PopupMenu.PopupBaseMenuItem {
    static {
        GObject.registerClass(this);
    }

    constructor(button, category) {
        super();
        this._category = category;
        this._button = button;
        
        this._oldX = -1;
        this._oldY = -1;
             
        //Add icons to categories
        //
        //debug command: journalctl -f -o cat /usr/bin/gnome-shell
        //Icon = new St.Icon({icon_name: `applications-${catname}-symbolic.symbolic.png`, style_class: 'system-status-icon', icon_size: '24'}); } -> this
        //doesn't work because the e.g. Accessories in categories has capital A, whereas in the name of png file has small a
        
        let Icon = new St.Icon();

        if (this._category)
            {var catname = this._category.get_name();
            //print (catname)
            if (catname==='Accessories') 
                Icon = new St.Icon({icon_name: `applications-accessories-symbolic.symbolic.png`, style_class: 'system-status-icon', icon_size: '24'}); //style_class: 'icon-dropshadow'
           if (catname==='Games')
                //also copied /usr/share/icons/Yaru/24x24/categories/applications-games.png to ~/.icons/Humanities-Blue/categories/24
                //in order to change the games icon, no change of name was required     
                Icon = new St.Icon({icon_name: `applications-games-symbolic.symbolic.png`, style_class: 'system-status-icon', icon_size: '24'});
            if (catname==='Graphics') 
                Icon = new St.Icon({icon_name: `applications-graphics-symbolic.symbolic.png`, style_class: 'system-status-icon', icon_size: '24'});
            if (catname==='Internet') 
                Icon = new St.Icon({icon_name: `applications-internet-symbolic.symbolic.png`, style_class: 'system-status-icon', icon_size: '24'});
            if (catname==='Office') 
                Icon = new St.Icon({icon_name: `applications-office-symbolic.symbolic.png`, style_class: 'system-status-icon', icon_size: '24'});
            if (catname==='Other') 
                Icon = new St.Icon({icon_name: `applications-other-symbolic.symbolic.png`, style_class: 'system-status-icon', icon_size: '24'});
            if (catname==='Programming') 
                Icon = new St.Icon({icon_name: `applications-engineering-symbolic.symbolic.png`, style_class: 'system-status-icon', icon_size: '24'});
            if (catname==='Science') 
                Icon = new St.Icon({icon_name: `applications-science-symbolic.symbolic.png`, style_class: 'system-status-icon', icon_size: '24'});
            if (catname==='Electronics') 
                Icon = new St.Icon({icon_name: `applications-electronics-symbolic.symbolic.png`, style_class: 'system-status-icon', icon_size: '24'});
            if (catname==='Education') 
                Icon = new St.Icon({icon_name: `applications-libraries-symbolic.symbolic.png`, style_class: 'system-status-icon', icon_size: '24'}); 
            if (catname==='Sound & Video') 
                Icon = new St.Icon({icon_name: `applications-multimedia-symbolic.symbolic.png`, style_class: 'system-status-icon', icon_size: '24'});
            if (catname==='System Tools') 
                Icon = new St.Icon({icon_name: `applications-system-tools-symbolic.symbolic.png`, style_class: 'system-status-icon', icon_size: '24'});
            if (catname==='Utilities') 
                Icon = new St.Icon({icon_name: `applications-utilities-symbolic.symbolic.png`, style_class: 'system-status-icon', icon_size: '24'});
            if (catname==='Windows Applications') 
                Icon = new St.Icon({icon_name: `cxmenu-cxoffice-0-cxmenu-symbolic.symbolic.png`, style_class: 'system-status-icon', icon_size: '24'});
            if (catname==='Wine') 
                Icon = new St.Icon({icon_name: `wine-symbolic.symbolic.png`, style_class: 'system-status-icon', icon_size: '24'});}                             
        else
            Icon = new St.Icon({icon_name: 'emblem-favorite-symbolic.symbolic.png', style_class: 'system-status-icon', icon_size: '24'})            
        this.add_child(Icon);

	//from here on the same
        let name;
        if (this._category)
            name = this._category.get_name();

        else
            name = _('Favorites');
            
        this.add_child(new St.Label({text: name}));
        this.connect('motion-event', this._onMotionEvent.bind(this));
        this.connect('notify::active', this._onActiveChanged.bind(this));


The most important step is step 3, which will allow gnome-shell to accept regular icons instead of symbolic ones. With the script provided you will be able to change icons of nautilus (both inside and on the left hand side). 
For show desktop button, depending on the resolution you have, you might have to change a little bit the size and the position of the button.

Regards!

---

