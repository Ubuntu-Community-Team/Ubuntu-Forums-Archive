---
title: "How to acces to toolbar configuration file?"
date: 2011-01-16
forum: Desktop Environments
---

### Post by pakito15191 on 2011-01-16
I had a problem and I think the easiest-quicker way to solve it is re-installing ubuntu, but I know that I'd take some time and headaches configuring all the toolbars and etc, so, where is the file with the toolbars configuration (no, no internet toolbar or other, I mean desktop toolbars) in my ubuntu system? I'm looking for a path to a file (or files), and Google didn't help me.
My idea was to copy it in a USB, and then, after reinstallation, to paste it in the place (deleting the one that was created), is this even possible?
I've tried some other things to re-install my system, but I'm just looking for this, please don't post other ways to do it except if this is impossible. I've tried UCK (it didn't work), RemasterSys and I looked at google for this. None work.

---

### Post by stinkeye on 2011-01-16
Do you mean the panel?

Anyway, this is a script that can save and restore the panel as well as set it back to default.

Save as PanelRestore.sh
```
#!/bin/sh
#
# GNOME Panel Save / Restore
# Writen by PhrankDaChicken
#
# http://ubuntu.online02.com
#
#
# Updated to add restore defaults by jimjimovich
# http://www.starryhope.com
#
#


DIR=$(pwd)
TITLE="PanelRestore"

Main () {
	CHOICE=$(zenity --list --title "$TITLE" --hide-column 1 --text "What do you want to do?" --column "" --column "" \
"0" "Save Panel Settings" \
"1" "Restore Panel Settings" \
"2" "Restore Default Panel Settings")
	if [ $CHOICE = 0 ]; then
		Panel_Save
	fi
	if [ $CHOICE = 1 ]; then
		Panel_Restore
	fi
	if [ $CHOICE = 2 ]; then
		Panel_Defaults
	fi	
}

Panel_Restore () {
	FILE=$(zenity --title "$TITLE: Open File" --file-selection --file-filter "*.xml" )
	if [ -n "$FILE" ]; then 
		gconftool-2 --load "$FILE"
		killall gnome-panel
	fi
	Main
}

Panel_Save () {
	FILE=$(zenity --title "$TITLE: Save File" --file-selection --save --confirm-overwrite --filename "Gnome_Panel.xml" --file-filter "*.xml" )
	if [ -n "$FILE" ]; then 
		EXT=$(echo "$FILE" | grep "xml")
		if [ "$EXT" = "" ]; then
			FILE="$FILE.xml"
		fi
		gconftool-2 --dump /apps/panel > $FILE
		zenity --info --title "$TITLE: File Saved" --text "File saved as: \n $FILE"
	fi
	Main
}

Panel_Defaults () {
	zenity --question --text="Are you sure you want to restore the default top and bottom panels?"
	gconftool-2 --recursive-unset /apps/panel
	rm -rf ~/.gconf/apps/panel
	pkill gnome-panel
	exit
}

Main

# END OF Script
```

Right click on the saved file
Properties > permissions  and tick execute.

If you don't see the GUI you may need zenity.
```
sudo apt-get install zenity
```

---

### Post by pakito15191 on 2011-01-17
It has a little bug that made me config everything again xD, if you press the "Restore Default Panel Settings", and then, when it says "Are you sure you want to restore the default top and bottom panels?", if you press "No", it restore them anyway! hahaha
But thanks, it was exactly what I was looking for

---

