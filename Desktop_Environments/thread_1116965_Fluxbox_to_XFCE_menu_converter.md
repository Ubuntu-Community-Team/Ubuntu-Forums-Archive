---
title: "Fluxbox to XFCE menu converter"
date: 2009-04-05
forum: Desktop Environments
---

### Post by theLured on 2009-04-05
Does anyone have a script to convert a Fluxbox menu to an XFCE one?

The short story of my stupidity. I copy and pasted from fluxmenu to XFCE menu editor and accidentally had my menu deleted at the end. I can't be bothered spending ages copying and pasting again and would like to know if there is a script that would do it instantly?

This site says that it has one, but the link seems to be dead.
[http://vsbabu.org/mt/archives/2003/08/09/trying_out_xfce4_.html](http://vsbabu.org/mt/archives/2003/08/09/trying_out_xfce4_.html)

Any help would be great.

---

### Post by theLured on 2009-04-05
Okay, I guess that no one has a script.
So in the traditional geek style, I avoided copying and pasting for 10 minutes and dedicated a good hour of time to writing a script(at the bottom of this post) and this post. The script just uses sed.


If you are going to use the script, Please read all the below.
If you are going to use this, just pass the file you want to use as an argument. so
./fluxbox-to-xfce fluxbox_menu
would make a new menu called fluxbox_menu.new and leave the original menu alone.

This is not a complete converting script as I am a crap bash scripter. It basically just changes the executable lines and submenu lines. Icons are kept too.
I didn't convert the [include] line

You might have to change the sed lines to match your files layout. My fluxbox menu was made using fluxmenu so if you used that then it should be fine. This is the layout I used. The spaces between the brackets, curly braces and angle brackets are needed.
```
[begin] (Main Menu) {} <>
    [exec] (Synaptic) {sudo synaptic} </usr/share/pixmaps/synaptic.png>
    [exec] (uRxvt) {urxvt} </usr/share/pixmaps/urxvt_16x16.xpm>
    [submenu] (Fluxconf) {} <>
        [exec] (fluxbare) {fluxbare} <>
        [exec] (fluxconf) {fluxconf} <>
        [exec] (fluxmenu) {fluxmenu} <>
    [end]
    [include] (/path/to/menu) {} <>
[end]
```
and becomes
```
<menu name="Main Menu"/>
    <app name="Synaptic" cmd="sudo synaptic" icon="/usr/share/pixmaps/synaptic.png"/>
    <app name="uRxvt" cmd="urxvt" icon="/usr/share/pixmaps/urxvt_16x16.xpm"/>
    <menu name="Fluxconf"/>
        <app name="fluxbare" cmd="fluxbare" icon=""/>
        <app name="fluxconf" cmd="fluxconf" icon=""/>
        <app name="fluxmenu" cmd="fluxmenu" icon=""/>
    </menu>
    [include] (/path/to/menu"/>
</menu>
```
Notice how the [include] line is a bit messed up.
YOU WILL ALSO need to remove the '/' from the end of every '<menu name=' line.

Only do these changes AFTER the script has run. The script will change the menu into a sub menu.
To change it back to the main menu change the first line
from
```
<menu name="Main Menu">
```
to
```
<?xml version="1.0" encoding="UTF-8"?>
<xfdesktop-menu>
```

and the last line
from
```
</menu>
```
to
```
</xfdesktop-menu>
```
The final menu should look like
```
<?xml version="1.0" encoding="UTF-8"?>
<xfdesktop-menu>
    <app name="Synaptic" cmd="sudo synaptic" icon="/usr/share/pixmaps/synaptic.png">
    <app name="uRxvt" cmd="urxvt" icon="/usr/share/pixmaps/urxvt_16x16.xpm">
    <menu name="Fluxconf">
        <app name="fluxbare" cmd="fluxbare" icon="">
        <app name="fluxconf" cmd="fluxconf" icon="">
        <app name="fluxmenu" cmd="fluxmenu" icon="">
    </menu>
</xfdesktop-menu>
```


So here is the script
```
#!/bin/bash
if [ "$1" != '' ]; then
	#first change the submenu
	new_menu="$1.new"
	cp "$1" "$new_menu"

	#Change the[ begin] line
	sed -e 's/\[begin\] (/<menu name="/' -i $new_menu
	#Change all the submenu ends
	sed -e 's/\[end\]/\<\/menu\>/' -i $new_menu
	#Change the submenu line
	sed -e 's/\[submenu\] (/<menu name="/' -i $new_menu
	sed -e 's/) {} <>/">/' -i $new_menu

	#Change the Exec line to app
	sed -e 's/\[exec\] (/<app name="/' -i $new_menu
	sed -e 's/) {/" cmd="/' -i $new_menu
	sed -e 's/} </" icon="/' -i $new_menu
	sed -e 's/>$/"\/>/' -i $new_menu

	#There will be some lines ending with ""> when they need to end with ">.
	#Correcting this, and still let =""> stay the same.
	sed -e 's/""\/>/"\/>/' -i $new_menu
	sed -e 's/="\/>/=""\/>/' -i $new_menu
	# The menu also has something on the end
	sed -e 's/<\/menu"\/>/<\/menu>/' -i $new_menu

else
	echo "supply the menu file as an argument. The new menu will be put it filename.new"
	echo "This is not a proper script. It will just make converting a little easier. You will still need to tidy it up."
	echo "NOTE: YOU WILL HAVE TO CHANGE THE LAST LINE FROM </menu> TO </xfdesktop-menu>"
	echo "There is probably more you will need to do, but the main items in the menu should be fine."
fi
```

---

