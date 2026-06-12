---
title: "How can I change mouse theme?"
date: 2012-01-13
forum: Desktop Environments
---

### Post by emptycoder on 2012-01-13
Hello everyone.
I have been trying to change mouse theme but so far, no luck.
I tried the old method, by adding mouse theme's folder (that I got from Gnome-look) to Icons folder on usr then choose that mouse theme via GNOME Tweaking Tool, and it didn't work, mouse cursors only change when I use Firefox but it changes back when I return to Desktop.
How I can use it with the whole system and not only with Firefox.
Thanks.
(Ubuntu 11.10 x64 GNOME 3)

---

### Post by Frogs Hair on 2012-01-13
Custom cursors have never worked on any Ubuntu release I have tried . They either work with the browser only or outside the browser , the later if Opera is in use. 

I gave up on custom cursors when using 10.04 . I'm curious if anyone has had success getting them to work with all applications .

---

### Post by stinkeye on 2012-01-13
I made this script which will list cursor themes in **/usr/share/icons**
and then allow you to just choose a number for your theme.
Save as change_cursor.sh and make executable.
```
#!/bin/bash

### Script to change cursors in /usr/share/icons ###

ls -R /usr/share/icons | grep "\/cursors:" | sed -e 's/\/cursors://g' -e 's/\/usr\/share\/icons\///g' > ~/.cursorlist.txt ## create installed cursor list text file
cat -b ~/.cursorlist.txt ## show a numbered list of cursors to choose from
 
	echo -e "\033[36mEnter your theme selection number:\033[0m"
	read CHOICE

CURSOR=$(cat ~/.cursorlist.txt | sed -n $CHOICE'p') ## match the theme selection number to the cursor name
	echo -e "\n\033[36mYou have selected ...$CURSOR\nContinue?(y/n):\033[0m"
	read Ans
if  [ "$Ans" != "y" ]; then
exit
else
### Change to selected  cursor ###
	gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR" &
	sudo sh -c "echo '[Icon Theme]\nInherits=$CURSOR' > /usr/share/icons/DMZ-White/cursor.theme"
fi
### Restart session to complete cursor change ###
	read -p "Do you wish to restartx? Save any work as you will now be logged out.(y/n):"
if  [ "$REPLY" != "y" ]; then 
	echo -e "\033[36m\nYou need to log out to complete cursor change.\033[0m";
else 
	sudo service lightdm restart
fi

```
It changes a dconf setting and the file **/usr/share/icons/DMZ-White/cursor.theme** to make the cursor consistent.

To run just click on the file and choose **Run in Terminal**.
The default cursor is **DMZ-White** if you want to change back.

---

### Post by linuxcoffeelover on 2012-11-09
> **stinkeye said:**
> I made this script which will list cursor themes in **/usr/share/icons**
and then allow you to just choose a number for your theme.
Save as change_cursor.sh and make executable.
```
#!/bin/bash

### Script to change cursors in /usr/share/icons ###

ls -R /usr/share/icons | grep "\/cursors:" | sed -e 's/\/cursors://g' -e 's/\/usr\/share\/icons\///g' > ~/.cursorlist.txt ## create installed cursor list text file
cat -b ~/.cursorlist.txt ## show a numbered list of cursors to choose from
 
    echo -e "\033[36mEnter your theme selection number:\033[0m"
    read CHOICE

CURSOR=$(cat ~/.cursorlist.txt | sed -n $CHOICE'p') ## match the theme selection number to the cursor name
    echo -e "\n\033[36mYou have selected ...$CURSOR\nContinue?(y/n):\033[0m"
    read Ans
if  [ "$Ans" != "y" ]; then
exit
else
### Change to selected  cursor ###
    gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR" &
    sudo sh -c "echo '[Icon Theme]\nInherits=$CURSOR' > /usr/share/icons/DMZ-White/cursor.theme"
fi
### Restart session to complete cursor change ###
    read -p "Do you wish to restartx? Save any work as you will now be logged out.(y/n):"
if  [ "$REPLY" != "y" ]; then 
    echo -e "\033[36m\nYou need to log out to complete cursor change.\033[0m";
else 
    sudo service lightdm restart
fi

```It changes a dconf setting and the file **/usr/share/icons/DMZ-White/cursor.theme** to make the cursor consistent.

To run just click on the file and choose **Run in Terminal**.
The default cursor is **DMZ-White** if you want to change back.
Thank you I have been trying to get this to work for so long and your script made it happen. you made my day.

---

