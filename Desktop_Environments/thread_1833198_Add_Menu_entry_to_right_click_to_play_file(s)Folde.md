---
title: "Add Menu entry to right click to play file(s)/Folder with Right-Click"
date: 2011-08-25
forum: Desktop Environments
---

### Post by fdrake on 2011-08-25
Add Menu entry to right click to play file(s)/Folder with Right-Click

How many times you wished to simply right-click a file/folder and select to play the media with mplayer on the terminal. Well I do often and I was tired to open the terminal , copy the name ,type mplayer., paste name…. press enter..

    * System info____________________

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION=”Ubuntu 10.04.3 LTS”
DESKTOP_SESSION=GNOME
mplayer package and gstreamer codecs installed

    * Commands____________________

sudo apt-get install nautilus-actions
mkdir ~/bash_scripts
cat >~/bash_scripts/play_all.sh
#!/bin/bash
cd “$2&#8243;
mplayer “$1&#8243;
mplayer “$1/”*
<press  Enter>
<press Cntrl +d>
chmod +x ~/bash_scripts/play_all.sh
nautilus-actions-config-tool

   1. define new action with name: play all
   2. Select Action tab and check “Display Item in selection context menu” and “Display Item in location context menu”. Make sure “Enable” is checked
   3. Select Command tab, and in the PATH field put: gnome-terminal. In the PARAMeters : –command=”~/bash_scripts/play_all.sh %f %d”
   4. Select Conditions tab. Check that “both” and “Appears if selection has multiple files or folders” are checked.
   5. Select Advanced conditions, and check all the entries.
   6. Select File>Save

Logout-Login and right-click select on folder(s) (containing music files), or files and play them.

---

