---
title: "Switching to Lubuntu via installing it."
date: 2010-03-16
forum: Desktop Environments
---

### Post by Sslaxx on 2010-03-16
Thinking of uninstalling GNOME/ubuntu-desktop and installing LXDE/lubuntu-desktop in its place. Just a couple of Qs. Got some hunches, just want to confirm/deny them:

* Does LXDE use GDM for login, or something else?
* Installing lubuntu-desktop would uninstall network-manager. Need to reboot if I do this, I take it?

Thanks.

---

### Post by kellemes on 2010-03-17
> **Sslaxx said:**
> Thinking of uninstalling GNOME/ubuntu-desktop and installing LXDE/lubuntu-desktop in its place. Just a couple of Qs. Got some hunches, just want to confirm/deny them:

* Does LXDE use GDM for login, or something else?
* Installing lubuntu-desktop would uninstall network-manager. Need to reboot if I do this, I take it?

Thanks.

* If you don't touch GDM.. LXDE will just be another entry in your session-list..
* I don't know.

Edit:
> **Sslaxx said:**
> Thinking of uninstalling GNOME/ubuntu-desktop (..)
Just be sure you don't uninstall GDM, it that's what you want to use.. You know you can also use another loginmanager? Like [SLiM]("http://slim.berlios.de/") for example.

---

### Post by Sslaxx on 2010-03-17
Yeah, was going to check out GDM alternatives. Thanks for the tip.

---

### Post by kerry_s on 2010-03-17
lubuntu uses lxdm.

add the lubuntu ppa:
[https://launchpad.net/~lubuntu-desktop/+archive/ppa](https://launchpad.net/~lubuntu-desktop/+archive/ppa)

lubuntu is still work in progress, you'll need to work through things to make it work right.

you might as well just install a fresh lubuntu, it's easier to work with when there's no extra junk in the way. it's only like 300+mb
[http://lubuntu.net/](http://lubuntu.net/)

i just got mine installed & i'm working out the kinks.

---

### Post by julio.tomaschitz on 2010-03-17
LXDE is very simple and light, great for using on usb stick, and old computers. there is everything you need to work and be alive. Well, my opinion: its the best cost-benefit.

---

### Post by dzon65 on 2010-03-17
Mentioned this before.If you're planning to install lxde or lubuntu,you might wanna install thunar and use that as file manager.There's a bug in lxde/lubuntu.Don't think it's already solved,but it's impossible to set defaults (open a picture with...,open that kind of file with.....).Gdm is no prob.I've got lxde installed,but replaced lx panel with gnome panel (there's hardly any difference in cpu/ram) and pcmanfm with thunar.Besides those litle annoyances it's a great distro,very fast and a low footprint.(think I'm at 1.5Gb fully packed).

---

### Post by kerry_s on 2010-03-17
> **dzon65 said:**
> Mentioned this before.If you're planning to install lxde or lubuntu,you might wanna install thunar and use that as file manager.There's a bug in lxde/lubuntu.Don't think it's already solved,but it's impossible to set defaults (open a picture with...,open that kind of file with.....).Gdm is no prob.I've got lxde installed,but replaced lx panel with gnome panel (there's hardly any difference in cpu/ram) and pcmanfm with thunar.Besides those litle annoyances it's a great distro,very fast and a low footprint.(think I'm at 1.5Gb fully packed).

:lolflag: you still got that problem? cause mine is a fresh install of lubuntu alpha 3, just installed yesterday & i still can select my programs. :lolflag:

your desktop is looking sweet though!

edit: dude, i just spotted this, you can even select the program in properties.

---

### Post by dzon65 on 2010-03-18
Hi there Kerry!Hmm,previous message didn't go through.Anyhow,updated and reinstalled lxde and yep,problem's still there.That's with the lxde-core,not lubuntu.Gonna give lubuntu a try.I'll let you know.

---

### Post by dzon65 on 2010-03-18
Okay,tried lubuntu desktop.........same thing.Ah well,thunar's doing a great job.

---

### Post by kerry_s on 2010-03-18
> **dzon65 said:**
> Okay,tried lubuntu desktop.........same thing.Ah well,thunar's doing a great job.

maybe because your installing on top of ubuntu? i used the lubuntu alpha 3 iso, used the "startup disk creator" to get it on usb, then installed, i don't have a cd/dvd drive on my nettop.

i got mine going pretty good, cleaned up synaptic & fixed the quick search, installed maximus, turned off the decorations, even took the time to create a little gui for lxshortcut to make launchers, there should be a gui default, so made the script then used it to make it's own launcher. lol

```
#!/bin/sh

name=`zenity --entry --text="Enter a Name"`

if [ "$name" ]; then
 lxshortcut -o $HOME/.local/share/applications/$name.desktop
else
 exit 0
fi
```

the usual pics:

---

### Post by dzon65 on 2010-03-18
This one's indeed on top of ubuntu.But,I did a minimal/lxde install on another pc with the same result.Tried before with the lubuntu iso and indeed,no prob there exept.....it was uninstallable.Gonna get me a new one and see how it turns out.Oh right,cd's....ran out of them.I'll let you kow..Like what you did with the launcher.

---

### Post by kerry_s on 2010-03-18
> Like what you did with the launcher.

i'm going crazy trying to find what feels comfortable, i just keep moving things till they fit the way i work.

so i got 2 auto hiding panels now, 1 just for the desktop pager. ;)

---

### Post by dzon65 on 2010-03-18
WOUHAHAHA.....Yeah,getting things right.Don't think it actually stops.Guess one keeps ajusting,there's always something "missing" or "to much".Have to hurry to back my stuff up.Quickly changing themes,icons,settings...you name it.The HD is on it's last breath.Quite frankly,I'm amazed it took sooo long.

---

### Post by kerry_s on 2010-03-18
i changed the lxshortcut script a little, cause my friend did not know exactly what it was for.

```
#!/bin/sh

name=`zenity --entry --text="Enter a Name (example: xterm)
	this will not be the name shown, it's only for the *.desktop file"`

if [ "$name" ]; then
 lxshortcut -o $HOME/.local/share/applications/$name.desktop
else
 exit 0
fi

```

so it looks like this now.

---

### Post by dzon65 on 2010-03-19
Hey,that looks nice!

---

### Post by kerry_s on 2010-03-19
i did a couple more for edit & delete to, just to make things easier after i had a couple of ooops, with bad command or just wanted to change the icon.

edit-launcher:
```
#!/bin/bash

scan=`ls $HOME/.local/share/applications | grep .desktop`
selected=`zenity --list --column=" " $scan`
lxshortcut -i $selected

```

delete-launcher:
```
#!/bin/bash

scan=`ls $HOME/.local/share/applications | grep .desktop`
selected=`zenity --list --column=" " $scan`

if [ $selected ]; then
 rm $HOME/.local/share/applications/$selected
 zenity --info --text="Launcher removed"
else
 exit 0
fi

```


it would have been nice to have been able to select where in the menu we wanted it, everything goes under "Other", my list might get long. :-|

---

### Post by dzon65 on 2010-03-19
Kerry.If I understand it correctly,you want to add it as a seperate menu?This was used to add a menu for the gdm/splash tweaking in karmic.Don't know if it helps but might inspire.
1) Install the script (or a wrapper for the script) in a bin directory.
     Code:
     install gdm-setup /usr/bin 
2) Put a Desktop item in /usr/share/applications/gdm-setup.desktop

A typical example of it's contents:
     Code:
     [Desktop Entry]
Version=1.0
Name=GDM2 Configuration Tool
Comment=Tool for editing Login Window
Categories=Application;System;
Exec=/usr/bin/gdm-setup
Terminal=false
Type=Application 
And it should appear in Applications->System->GDM2 Configuration Tool (by the guy formerly known as tinivole)

---

### Post by kerry_s on 2010-03-19
no, thats not what i mean.
i wish the lxshortcut gui would also do "Categories", i know i can add it manually, but that would not be user friendly. i think i will add that feature to the script, it should be easy enough using the "echo "Categories=$section;" >> whatever.desktop" i'll play with it later i just got up & got to cook breakfast for the kids, but i need some coffee & a cig in me first, it's also shopping day so got to get groceries. basically when i can, i'll get to it. :lolflag:

it should take like less then 5 minutes to add to the script to get that feature, but i was to tired yesterday, i really didn't think about it.

---

### Post by dzon65 on 2010-03-19
Been playing around with slitaz running in ram.That distro's been lying around and I didn't pay much more attention to it.Gave it another try and WHAM!This is lightning fast.(totally forgotten about it)Major drawback:screenresolution's only up to 1024X768.Found out why.Default setting is with the xvesa server,so need to install xorg.Wonder if the speed will decrease a lot though.But,that's for tommorow.
Oh,btw,good morning!

---

### Post by kerry_s on 2010-03-19
all right my friend revision #3 for the make-launcher, now you can can choose what section of the menu you want it to show in.
i went with a list instead of manual input, i hope i got most of the sections.

menu-launcher:
```
#!/bin/bash

name=`zenity --entry --text="Enter a Name (example: xterm)
	this will not be the name shown, it's only for the *.desktop file"`

if [ "$name" ]; then
 lxshortcut -o $HOME/.local/share/applications/$name.desktop
 select=`zenity --list --text="Choose the Menu Section" --column="" Utility Graphics Network Office AudioVideo System Settings Other`
 echo "Categories=$select;" >> $HOME/.local/share/applications/$name.desktop
else
 exit 0
fi

```

---

### Post by kerry_s on 2010-03-19
here's the new edit-launcher with the menu categories selection, so if you need to you can.

edit-launcher:
```
#!/bin/bash

scan=`ls $HOME/.local/share/applications | grep .desktop`
selected=`zenity --list --column=" " $scan`
if [ $selected ]; then
 lxshortcut -i $selected
 select=`zenity --list --text="Choose the Menu Section" --column="" Utility Graphics Network Office AudioVideo System Settings Other`
 echo "Categories=$select;" >> $HOME/.local/share/applications/$selected
else
 exit0
fi

```

---

### Post by kerry_s on 2010-03-19
you know what, i think i'll just combine all 3 scripts into 1 script where you select what you want to do, that way it will be easier to manage & make changes. i'll get on that later. ;)

---

### Post by kerry_s on 2010-03-19
okay this is it, the lxshortcut launcher to provide a gui way for the user to work with launchers. i keep my script in $HOME/bin, but you can put yours where ever you feel like. you can run the script itself to make the menu launcher for the launcher. :)

Lxshortcut Launcher:

```

#!/bin/bash

# this is a script to add some gui features to lxshortcut for a more user friendly experience
# created on lubuntu 3/19/2010
# it's a script to fill a need, you may do with it as you please
###

## this part is the choices to choose from ##

chose=`zenity --list --title="Lxshortcut-gui" --column="" "Make Launcher" "Edit Launcher" "Delete Launcher"`

## this part makes the launcher ##

if [ "$chose" = "Make Launcher" ]; then

	name=`zenity --entry --text="Enter a Name (example: xterm)
	this will not be the name shown, it's only for the *.desktop file"`

	if [ "$name" ]; then
	 lxshortcut -o $HOME/.local/share/applications/$name.desktop
	 select=`zenity --list --text="Choose the Menu Section" --column="" Utility Graphics 	Network Office AudioVideo System Settings Other`
	 echo "Categories=$select;" >> $HOME/.local/share/applications/$name.desktop
	else
	 exit 0
	fi
fi

## this part is to edit the launcher ##

if [ "$chose" = "Edit Launcher" ]; then

	scan=`ls $HOME/.local/share/applications | grep .desktop`
	selected=`zenity --list --column="" $scan`
	if [ $selected ]; then
	 lxshortcut -i $selected
	 select=`zenity --list --text="Choose the Menu Section" --column="" Utility Graphics 	Network Office AudioVideo System Settings Other`
	 echo "Categories=$select;" >> $HOME/.local/share/applications/$selected
	else
	 exit0
	fi
fi

## this part is to delete the launcher ##

if [ "$chose" = "Delete Launcher" ]; then

	scan=`ls $HOME/.local/share/applications | grep .desktop`
	selected=`zenity --list --column="" $scan`
	if [ $selected ]; then
	 rm $HOME/.local/share/applications/$selected
	 zenity --info --text="Launcher removed"
	else
	 exit 0
	fi
fi
exit 0


```

---

### Post by dzon65 on 2010-03-20
Hats of Kerry!I'm trying to get this slitaz working properly.It comes with lxde,openbox.....well,same as debian/lxde,only..faster.Gonna install it as only os on senior (that's a good resolution,damn,wish I could get the settings right on my laptop) and gonna use your script.You should post this as a tutorial or on the lxde forum.Think a lot of people could benefit from this.(from?.....my english is not really what it's suposed to be,Papua?).

---

### Post by kerry_s on 2010-03-20
> **dzon65 said:**
> Hats of Kerry!I'm trying to get this slitaz working properly.It comes with lxde,openbox.....well,same as debian/lxde,only..faster.Gonna install it as only os on senior (that's a good resolution,damn,wish I could get the settings right on my laptop) and gonna use your script.You should post this as a tutorial or on the lxde forum.Think a lot of people could benefit from this.(from?.....my english is not really what it's suposed to be,Papua?).

the scripts not perfect, my friend mentioned a problem with the echo command, if you edit a launcher you'll end up with "Categories=*;" listed several times in the file, not a problem as it uses the last 1, so the script still works, but it's messy. i tried using sed, but i can't get it to write to the file, my programming skills are very basic at best, but i can read good, so i manage. :lolflag:

i'm not to worried about posting it all over, if a person uses google to search "lxshortcut gui" we're at the top of the list. ;)

---

### Post by earthpigg on 2010-03-20
kerry,

that looks great!

you wouldn't mind if i tested/used/modified that for the next Masonux release would you?

want to formally declare a license? (GPL, public domain, BSD, etc)

---

### Post by dzon65 on 2010-03-20
Djeez kerry,seriously?...................quote:"my programming skills are very basic at best".Earthpig has a point.

---

### Post by kerry_s on 2010-03-20
> **earthpigg said:**
> kerry,

that looks great!

you wouldn't mind if i tested/used/modified that for the next Masonux release would you?

want to formally declare a license? (GPL, public domain, BSD, etc)

earthpigg, like it says do with as you please. 
grab the 1 from here:
[http://ubuntuforums.org/showthread.php?p=9000663#post9000663](http://ubuntuforums.org/showthread.php?p=9000663#post9000663)

i fixed it so the "Categories=*;" aren't duplicated in the edited launcher and i add height for less scrolling. enjoy!

i feel pcman done most of the work with lxshortcut, but why he just stopped short of a gui is beyond me, any kind of gui, i would even be happy if the gui was made with xmessage, it would be ugly, but still at least a gui. :lolflag:

---

### Post by earthpigg on 2010-03-20
sweet. if anyone wants to make it a more 'native' part of their system, just toss it in /usr/bin and make it have the same permissions as the rest of the stuff in that folder.

0 - to uphold convention, rename it from .txt to have no extension. i called the file 'lxshortcut-gui'.
1 - sudo pcmanfm. or thunar, or whatever.
2 - drag+drop it into /usr/bin
3 - right click, properties
4 - make it have permissions identical to everything else


done.

now you can type lxshortcut-gui to run it... and promptly use it to create a menu entry for itself with the command "/usr/bin/lxshortcut-gui" as a test run.

---

### Post by kerry_s on 2010-03-20
> sweet. if anyone wants to make it a more 'native' part of their system, just toss it in /usr/bin and make it have the same permissions as the rest of the stuff in that folder.

0 - to uphold convention, rename it from .txt to have no extension. i called the file 'lxshortcut-gui'.
1 - sudo pcmanfm. or thunar, or whatever.
2 - drag+drop it into /usr/bin
3 - right click, properties
4 - make it have permissions identical to everything else


done.

now you can type lxshortcut-gui to run it... and promptly use it to create a menu entry for itself with the command "/usr/bin/lxshortcut-gui" as a test run.

try all 3 features let me know what you think, it probably could use some titles for the windows, i run nodecor so didn't bother, the scripts simple enough i'm sure can add them if you want. :)

---

### Post by earthpigg on 2010-03-22
they all seem to work. different versions of lxpanel that ship with different releases of ubuntu have different menu sections, so ill probably modify them accordingly when we see what ships with 10.04.

if i do end up playing with it, ill be sure to post it back here. (i commented my local copy of it to remind me :P )

---

### Post by BrokenTusk on 2011-02-04
Okay Kerry_S. Hey guys.
I toyed with Kerry's lxshortcut script and it became the LxMenuEditor.
LXDE is already fast, but wait till you clean up the app launchers... wowee!
I sincerely hope it boosts you all into warp speed too,
BT

```

#!/bin/sh
# Author : dave@meyer.LA
# Date   : 01/01/2011
#
# LxMenuEditor
# Finally, a complete, straightforward, bulletproof menu editor for LXDE
#
# Dependencies: lxshortcut, zenity


#Trap to ensure we stay clean
clean_up(){
unset IFS
unset LANG2
cd "$HOME/.local/share/applications"
rm -f tmpfile*
}

trap 'clean_up' EXIT INT TERM QUIT SIGINT SIGQUIT SIGTERM

#Preliminaries:
clean_up
LANG2=`echo $LANG | tr '.' '\t' | awk '{ print $1 }'`
export LANG2

#Functions:
SanityCheck(){
echo 10
#Bar none, the most reliable method to overcome the problems associated with multiple files with spaces is to rename.
cd "$HOME/.local/share/applications"
IFS=$'\n'
for FILE in `ls *.desktop | grep " "` ; do mv "$FILE" `echo $FILE | tr ' ' '_'` ; done
unset IFS
echo 20
#Ensure there are Name= and Name[lang]= tags
cd "$HOME/.local/share/applications"
for FILE in `ls *.desktop`
do NAM=`cat "$FILE" | grep -x ^Name=.* | sed -e 's/.*=//g'`
NAML=`cat "$FILE" | grep -x ^Name.$LANG2.=.* | sed -e 's/.*=//g'`
    if [ "$NAM" ] || [ "$NAML" ]; then
        if [ "$NAM" ] && [ -z "$NAML" ]; then
#Copy Name= to Name[lang]=
        echo "Name[$LANG2]=${NAM}" >> "$FILE"
        fi
        if [ "$NAML" ] && [ -z "$NAM" ]; then
#Copy Name[lang]= to Name= 
        echo "Name=${NAML}" >> "$FILE"
        fi
    fi
    if [ -z "$NAML" ] && [ -z "$NAM" ]; then    #REM The return status of AND and OR lists is the exit status of the last command executed in the list : *    with command1 && command2, command2 is executed only if command1 returns an exit status of zero (true)    *    with command1 &#9474;&#9474; command2, command2 is executed only if command1 returns a non-zero exit status (false)
        echo "Name=<empty>" >> "$FILE"
        echo "Name[$LANG2]=<empty>" >> "$FILE"
    fi
done
echo 30
for FILE in `ls *.desktop`
do COM=`cat "$FILE" | grep -x ^Comment=.* | sed -e 's/.*=//g'`
COML=`cat "$FILE" | grep -x ^Comment.$LANG2.=.* | sed -e 's/.*=//g'`
    if [ "$COM" ] || [ "$COML" ]; then
        if [ "$COM" ] && [ -z "$COML" ]; then
#Copy Name= to Name[lang]=
        echo "Comment[$LANG2]=${COM}" >> "$FILE"
        fi
        if [ "$COML" ] && [ -z "$COM" ]; then
#Copy Name[lang]= to Name= 
        echo "Comment=${COML}" >> "$FILE"
        fi
    fi
    if [ -z "$COML" ] && [ -z "$COM" ]; then
        echo "Comment=<empty>" >> "$FILE"
        echo "Comment[$LANG2]=<empty>" >> "$FILE"
    fi
done
echo 40
for ME in `grep -L ^Exec= *.desktop` ; do echo "Exec=<empty>" >> "$ME" ; done
for MCat in `grep -L ^Categories= *.desktop` ; do echo "Categories=<empty>" >> "$MCat" ; done
# All tagged not to show in LXDE get the NoDisplay=true for reliable filtering later
for OSI in `grep -H -E -l -x -e 'OnlyShowIn.*' *.desktop | xargs -L50 grep -L -e 'OnlyShowIn=.*LXDE *'`
do sed -e '/NoDisplay=.*/d' -e '/^$/ d' -i "$OSI"
echo "NoDisplay=true" >> "$OSI"
done
echo 50

#Dups
cd "$HOME/.local/share/applications"
#Remove duplicates
for FILE in *.desktop
do occ=`grep -c ^Name= "$FILE"`
#Non-integer trap.
echo "$occ" | grep "[^0-9]" > /dev/null 2>&1
echo $occ >tmpfile11 #found this to be req when debugging, go figure.
if [ "$?" -eq 1 ]; then
    return
else
    if [ "$occ" -gt 1 ]; then
        linetokeep=`grep -m 1 ^Name=.* "$FILE"`
        sed -e '/^Name=.*/d' -e '/^$/ d' -i "$FILE"
        echo "$linetokeep" >> "$FILE"
    fi
fi
done
echo 60
for FILE in *.desktop
do occ=`grep -c ^Exec= "$FILE"`
#Non-integer trap.
echo "$occ" | grep "[^0-9]" > /dev/null 2>&1
echo $occ >tmpfile11 #found this to be req when debugging, go figure.
if [ "$?" -eq 1 ]; then
    return
else
    if [ "$occ" -gt 1 ]; then
        linetokeep=`grep -m 1 ^Exec=.* "$FILE"`
        sed -e '/^Exec=.*/d' -e '/^$/ d' -i "$FILE"
        echo "$linetokeep" >> "$FILE"
    fi
fi
done
echo 70
for FILE in *.desktop
do occ=`grep -c ^Comment= "$FILE"`
#Non-integer trap.
echo "$occ" | grep "[^0-9]" > /dev/null 2>&1
echo $occ >tmpfile11 #found this to be req when debugging, go figure.
if [ "$?" -eq 1 ]; then
    return
else
    if [ "$occ" -gt 1 ]; then
        linetokeep=`grep -m 1 ^Comment=.* "$FILE"`
        sed -e '/^Comment=.*/d' -e '/^$/ d' -i "$FILE"
        echo "$linetokeep" >> "$FILE"
    fi
fi
done
echo 80
for FILE in *.desktop
do occ=`grep -c ^Categories= "$FILE"`
#Non-integer trap.
echo "$occ" | grep "[^0-9]" > /dev/null 2>&1
echo $occ >tmpfile11 #found this to be req when debugging, go figure.
if [ "$?" -eq 1 ]; then
    return
else
    if [ "$occ" -gt 1 ]; then
        linetokeep=`grep -m 1 ^Categories=.* "$FILE"`
        sed -e '/^Categories=.*/d' -e '/^$/ d' -i "$FILE"
        echo "$linetokeep" >> "$FILE"
    fi
fi
done
echo 90
for FILE in *.desktop
do occ=`grep -c ^Name.$LANG2.= "$FILE"`
#Non-integer trap.
echo "$occ" | grep "[^0-9]" > /dev/null 2>&1
echo $occ >tmpfile11 #found this to be req when debugging, go figure.
if [ "$?" -eq 1 ]; then
    return
else
    if [ "$occ" -gt 1 ]; then
        linetokeep=`grep -m 1 ^Name.$LANG2.=.* "$FILE"`
        sed -e '/Name\['"$LANG2"'\]=.*/d' -e '/^$/ d' -i "$FILE"
        echo "$linetokeep" >> "$FILE"
    fi
fi
done
echo 95
for FILE in *.desktop
do occ=`grep -c ^Comment.$LANG2.= "$FILE"`
#Non-integer trap.
echo "$occ" | grep "[^0-9]" > /dev/null 2>&1
echo $occ >tmpfile11 #found this to be req when debugging, go figure.
if [ "$?" -eq 1 ]; then
    return
else
    if [ "$occ" -gt 1 ]; then
        linetokeep=`grep -m 1 ^Comment.$LANG2.=.* "$FILE"`
        sed -e '/Comment\['"$LANG2"'\]=.*/d' -e '/^$/ d' -i "$FILE"
        echo "$linetokeep" >> "$FILE"
    fi
fi
done
echo 101
}

SanityCheck | zenity --progress --auto-close --auto-kill --width=500 --title="Applying sanity checks and auto-corrections" --text="This essential step ensures LXDE operates error-free. \n\nIt speeds up .desktop file processing and menu access. \n\nPlease, it's worth the wait..."
EXIT=$?
    if [ $EXIT -ne 0 ] ; then
        exit 0
    fi

TurnOn(){
cd "$HOME/.local/share/applications"
#To show comment out:
#"NotShowIn" lines that include "LXDE" with a single "#"
#"OnlyShowIn" lines that do not include "LXDE" with a single "#"
#"Hidden=true" with a single "#"
#rm NoDisplay=true
for FILE in `echo "$ToTurnOn"` ; do sed '
                            s/NotShowIn.*LXDE/#&/g
                            /^##/s/#//1
                            /LXDE/!s/OnlyShowIn/#&/g
                            /^##/s/#//1
                            s/Hidden=true/#&/g
                            /^##/s/#//1
                            /NoDisplay=.*/d 
                            /^$/ d' -i "$HOME/.local/share/applications"/"$FILE" ; done
#This may generate a minor error like "Output line too long" . Barnette @ http://www.grymoire.com/Unix/Sed.html#uh-41 considers this a bug, and has reported it to Sun.
}

TurnOff(){
cd "$HOME/.local/share/applications"
#To hide: 
#rm "NoDisplay=" and prevent duplicates
#add "NoDisplay=true"
for FILE in `echo "$ToTurnOff"` ; do sed -e '/NoDisplay=.*/d' -e '/^$/ d' -i "$HOME/.local/share/applications"/"$FILE" ; done
for FILE in `echo "$ToTurnOff"` ; do echo "NoDisplay=true" >> "$HOME/.local/share/applications"/"$FILE" ; done
}

MainMenuLoop(){
while :
do

#Choices choices choices...
chose=`zenity --list --height="260" --width="250" --title="LXDE Menu Editor" --text="What do you want to do? \n\nClick <b>CANCEL</b> to <b>EXIT</b>." --column="" "Create a launcher" "Edit a launcher" "Show or Hide launcher(s)" "Delete existing launcher(s)" "Override system-wide launchers"`
#Clicking CANCEL or empty OK exits the script
    EXIT=$?
    if [ $EXIT -ne 0 ] ; then
        exit 0
    fi
if [ -z "$chose" ]; then
        exit 0
fi

if [ "$chose" = "Create a launcher" ]; then
DefineName(){
    itemname=`zenity --entry --text="Enter a name (example: lxterminal) \n\nNote that capital letters are filed before lower case letters. \n\n(This name is only for the *.desktop file.)"`
#Clicking CANCEL loops back, OK asks again
        EXIT=$?
        if [ $EXIT -ne 0 ] ; then
            MainMenuLoop
        else
            FileExists
        fi
}

FileExists(){
    cd "$HOME/.local/share/applications"
    if [ -e "$itemname".desktop ]; then
        zenity --question --title="Warning" --width="200" --text="${itemname}.desktop already exists. \n\n<b>Overwrite?</b>"
#Clicking CANCEL loops back, OK continues
        EXIT=$?
        if [ $EXIT -ne 0 ] ; then
            DefineName
        else
            Create
        fi
    else
        Create
    fi
}

Create(){             
        if [ "$itemname" ]; then
            cd "$HOME/.local/share/applications"
            lxshortcut -o "$itemname".desktop
#Sanity check: test if the new launcher is more than an empty file
            SANCHK=`du -b "$itemname".desktop | awk '{ print $1 }'`
#If no then rm and notify of cancelation before returning to main menu
            if [ "$SANCHK" -lt 110 ]; then
                rm "$HOME/.local/share/applications"/"$itemname".desktop
                zenity --info --title="Warning" --width="200" --text="${itemname}.desktop was empty and was therefore DISCARDED. \n\n\nPlease try again."
            else
                select=`zenity --list --height="330" --width="400" --text="Choose the LXMenu Section(s) to file ${itemname}.desktop under." --checklist --multiple --separator=";" --hide-column=2 --print-column=2 --column="" --column="Returned Output" --column="Category" FALSE Utility Accessories FALSE Graphics Graphics FALSE Network Internet FALSE Office Office TRUE Other Other FALSE AudioVideo "Sound & Video" FALSE System "System Tools" FALSE Accessibility "Universal Access" FALSE Settings "System -> Preferences" FALSE SystemSetup "System -> Administration"`
#Failure to select at least one checkmark results in the Categories tag being set to Other
                if `grep -qw "^Categories=;" "$itemname".desktop` ; then
                    sed -e '/^Categories=.*/d' -e '/^$/ d' -i "$itemname".desktop
                    echo "Categories=Other;" >> "$HOME/.local/share/applications"/"$itemname".desktop
                    zenity --info --title="Note" --width="200" --text="${itemname}.desktop filed under <i>Other</i> by default."
                else
                echo "Categories=${select};" >> "$HOME/.local/share/applications"/"$itemname".desktop
                fi
#Sanity Check: test if the new launcher is more than an empty file
                SANCHK=`du -b "$itemname".desktop | awk '{ print $1 }'`
#If no then delete and notify of cancelation before returning to main menu
                    if [ "$SANCHK" -lt 123 ]; then
                    rm "$HOME/.local/share/applications"/"$itemname".desktop
                    zenity --info --title="Warning" --width="200" --text="${itemname}.desktop was empty and was therefore DISCARDED. \n\n\nPlease try again."
                    fi
            fi
#Failure to select a file yet clicking OK
        elif [ !"$itemname" ]; then
            zenity --question --title="Note" --width="200" --text="Please enter a name."
            EXIT=$?
            if [ $EXIT -ne 0 ] ; then
                MainMenuLoop
            else
                DefineName
            fi
        fi
}

DefineName
#rm spaces in new name.
cd "$HOME/.local/share/applications"
IFS=$'\n'
for FILE in `ls *.desktop | grep " "` ; do mv "$FILE" `echo $FILE | tr ' ' '_'` ; done
unset IFS
fi
# Loop back to the main menu to continue

if [ "$chose" = "Edit a launcher" ]; then
#Rescan to reflect changes since the last operation
    scan_OFF=`grep -H -E -l -x -e 'NoDisplay=true' -e 'Hidden=true' -e 'NotShowIn.*LXDE.*' *.desktop`
    scan_ON=`ls *.desktop | grep -v "$scan_OFF"`
    scan_ON_displayname=`echo "$scan_ON" | xargs grep -x ^Name.$LANG2.=.* | sed -e 's/.*=//g'`
    scan_ON_command=`echo "$scan_ON" | xargs grep -x ^Exec=.* | sed -e 's/.*=//g'`
    scan_ON_comment=`echo "$scan_ON" | xargs grep -x ^Comment.$LANG2.=.* | sed -e 's/.*=//g'`
    scan_ON_categories=`echo "$scan_ON" | xargs grep -x ^Categories=.* | sed -e 's/.*=//g'`
#Format to suit zenity's rigidly anal --list input requirements
    echo "${scan_ON_displayname}" | sed -e 's/^$/<empty>/g' > tmpfile1
    echo "${scan_ON}" > tmpfile2
    echo "${scan_ON_command}" | sed 's/^$/<empty>/g' > tmpfile3
    echo "${scan_ON_comment}" | sed 's/^$/<empty>/g' > tmpfile4
    echo "${scan_ON_categories}" | sed 's/^$/<empty>/g' > tmpfile5
    zlist=`pr -m -t -s"|" tmpfile1 tmpfile2 tmpfile3 tmpfile4 tmpfile5 | awk '{print $0}' | sed -e 's/|/\n/g'`

IFS=$'\n'
selected=`zenity --list --height="700" --width="1300" --title="Launchers currently showing" --text="Select the launcher to <b>EDIT</b>" --print-column=2 --column="Display Name" --column=Filename --column=Command --column="Tooltip Comment" --column=Categories $zlist`
unset IFS
#Clicking CANCEL loops back to main menu
    EXIT=$?
    if [ $EXIT -ne 0 ] ; then
        MainMenuLoop
    fi
    if [ $selected ]; then
#Test if Categories exist, if not asign to Other
    NOCAT=`grep -L ^Categories= $selected`    
        if [ "$NOCAT" = $selected ]; then
            echo "Categories=Other;" >> "$HOME/.local/share/applications"/$selected
        fi
    lxshortcut -i $selected
#ensure default tags correspond to language-set tags for Comment= tags
    TAG1=`grep "^Name.$LANG2.=.*" "$HOME/.local/share/applications"/"$selected" | sed 's/^Name.*=//'`
    if [ "$TAG1" ]; then
        #rm Name= line
        sed -e '/^Name=/d' -e '/^$/ d' -i "$HOME/.local/share/applications"/"$selected"
        #copy Name[en_US]= tag to Name= tag
        echo "Name=${TAG1}" >> "$HOME/.local/share/applications"/"$selected"
    fi
    TAG2=`grep "^Comment.$LANG2.=.*" "$HOME/.local/share/applications"/"$selected" | sed 's/^Comment.*=//'`
    if [ "$TAG2" ]; then
        #rm Comment= line
        sed -e '/^Comment=/d' -e '/^$/ d' -i "$HOME/.local/share/applications"/"$selected"
        #copy Comment[en_US]= tag to Comment= tag
        echo "Comment=${TAG2}" >> "$HOME/.local/share/applications"/"$selected"
    fi
        BEFORE=`grep Categories $selected`
        if `grep Categories $selected | grep -qw Utility` ; then a1=TRUE ; else a1=FALSE ; fi
        if `grep Categories $selected | grep -qw Graphics` ; then b1=TRUE ; else b1=FALSE ; fi
        if `grep Categories $selected | grep -qw Network` ; then c1=TRUE ; else c1=FALSE ; fi
        if `grep Categories $selected | grep -qw Office` ; then d1=TRUE ; else d1=FALSE ; fi
        if `grep Categories $selected | grep -qw Other` ; then e1=TRUE ; else e1=FALSE ; fi
        if `grep Categories $selected | grep -qw AudioVideo` ; then f1=TRUE ; else f1=FALSE ; fi
        if `grep Categories $selected | grep -qw System` ; then g1=TRUE ; else g1=FALSE ; fi
        if `grep Categories $selected | grep -qw Accessibility` ; then h1=TRUE ; else h1=FALSE ; fi
        if `grep Categories $selected | grep -qw Settings` ; then i1=TRUE ; else i1=FALSE ; fi
        if `grep Categories $selected | grep -qw SystemSetup` ; then j1=TRUE ; else j1=FALSE ; fi
        select=`zenity --list --height="330" --width="400" --text="Choose the LXMenu Section(s) to file $selected under." --checklist --multiple --separator=";" --hide-column=2 --print-column=2 --column="" --column="Returned Output" --column="Category" $a1 Utility Accessories $b1 Graphics Graphics $c1 Network Internet $d1 Office Office $e1 Other Other $f1 AudioVideo "Sound & Video" $g1 System "System Tools" $h1 Accessibility "Universal Access" $i1 Settings "System -> Preferences" $j1 SystemSetup "System -> Administration"`
            EXIT=$?
            if [ $EXIT -ne 0 ] ; then
                AFTER="$BEFORE"
            else 
                AFTER=`echo "Categories=${select};"`
            fi
            if [ "$BEFORE" != "$AFTER" ]; then
                sed -e '/^Categories=.*/d' -i $selected
                echo "Categories=${select};" >> "$HOME/.local/share/applications"/$selected
            fi
#Failure to select at least one checkmark results in the Categories tag being set to Other
        if `grep -qw "^Categories=;" $selected` ; then
            sed -e '/^Categories=.*/d' -i $selected
            echo "Categories=Other;" >> "$HOME/.local/share/applications"/$selected
            zenity --info --title="Note" --width="200" --text="$selected filed under <i>Other</i> by default."
        fi
#Failure to select a file yet clicking OK
    elif [ !"$selected" ]; then
        zenity --info --title="Note" --width="200" --text="No launcher selected to edit."
    fi
fi
#Loop back to the main menu to continue

if [ "$chose" = "Show or Hide launcher(s)" ]; then
#Rescan to reflect changes since the last operation
    scan_OFF=`grep -H -E -l -x -e 'NoDisplay=true' -e 'Hidden=true' -e 'NotShowIn.*LXDE.*' *.desktop`
    scan_ON=`ls *.desktop | grep -v "$scan_OFF"`
    scan_ON_displayname=`echo "$scan_ON" | xargs grep -x ^Name.$LANG2.=.* | sed -e 's/.*=//g'`
    scan_ON_command=`echo "$scan_ON" | xargs grep -x ^Exec=.* | sed -e 's/.*=//g'`
    scan_ON_comment=`echo "$scan_ON" | xargs grep -x ^Comment.$LANG2.=.* | sed -e 's/.*=//g'`
#Format to suit zenity's rigidly anal --list input requirements
    echo "${scan_ON_displayname}" | sed -e 's/^$/<empty>/g' -e 's/^/TRUE|/g' > tmpfile1
    echo "${scan_ON}" > tmpfile2
    echo "${scan_ON_command}" | sed 's/^$/<empty>/g' > tmpfile3
    echo "${scan_ON_comment}" | sed 's/^$/<empty>/g' > tmpfile4

    scan_OFF_displayname=`echo "$scan_OFF" | xargs grep -x ^Name.$LANG2.=.* | sed -e 's/.*=//g'`
    scan_OFF_command=`echo "$scan_OFF" | xargs grep -x ^Exec=.* | sed -e 's/.*=//g'`
    scan_OFF_comment=`echo "$scan_OFF" | xargs grep -x ^Comment.$LANG2.=.* | sed -e 's/.*=//g'`
#Format to suit zenity's rigidly anal --list input requirements
    echo "${scan_OFF_displayname}" | sed -e 's/^$/<empty>/g' -e 's/^/FALSE|/g' > tmpfile5
    echo "${scan_OFF}" > tmpfile6
    echo "${scan_OFF_command}" | sed 's/^$/<empty>/g' > tmpfile7
    echo "${scan_OFF_comment}" | sed 's/^$/<empty>/g' > tmpfile8
    zlist1=`pr -m -t -s"|" tmpfile1 tmpfile2 tmpfile3 tmpfile4 | awk '{print $0}' | sed -e 's/|/\n/g'`
    zlist2=`pr -m -t -s"|" tmpfile5 tmpfile6 tmpfile7 tmpfile8 | awk '{print $0}' | sed -e 's/|/\n/g'`

    IFS=$'\n'
    selected2=`zenity --list --checklist --height="700" --width="1300" --title="All launchers" --text="Select the launcher(s) to <b>SHOW</b>" --print-column=3 --column="Sort" --column="Display Name" --column=Filename --column=Command --column="Tooltip Comment" $zlist1 $zlist2`
    unset IFS
#Clicking Cancel or selecting nothing yet clicking OK loops the script back to the main menu
    EXIT=$?
    if [ $EXIT -eq 0 -a "$selected2" ] ; then
        echo "$selected2" | sed 's/|/\n/g' > tmpfile9
        ToTurnOn=`diff -T tmpfile2 tmpfile9 | grep ">".* | awk '{print $2}'`
        ToTurnOff=`diff -T tmpfile2 tmpfile9 | grep "<".* | awk '{print $2}'` 
            if [ "$ToTurnOn" ]; then
                TurnOn
            fi
            if [ "$ToTurnOff" ]; then
                TurnOff
            fi
    else
        MainMenuLoop    
    fi
fi
#Loop back to the main menu to continue

if [ "$chose" = "Delete existing launcher(s)" ]; then
    scan_ALL=`ls "$HOME/.local/share/applications" | grep .desktop | grep -v wine-extension | grep -v userapp` #exclude userapp and wine-extension
      selected3=`zenity --list --height="600" --width="400" --text="Select launcher(s) to <b>DELETE</b> \n-->Use ctrl+ or shift+click for multiple selection" --multiple --separator=$'\n' --print-column=ALL --column="All launchers" $scan_ALL`
#Clicking Cancel loops the script back to the main menu
    EXIT=$?
    if [ $EXIT -ne 0 ] ; then
        MainMenuLoop
    fi
    if [ "$selected3" ]; then
        zenity --question --title="Warning" --text="You are about to permanently <b>REMOVE</b>: \n\n$selected3. \n\nDo you want to proceed? \n\nIf you're unsure: hide DON'T remove."
        CONF=$?
            if [ $CONF -eq 0 ] ; then
                cd "$HOME/.local/share/applications"
                rm $selected3
                zenity --info --title="Info" --text="$selected3 \n\n...permanently REMOVED"
            fi
#Failure to select a file yet clicking OK
    elif [ !"$selected3" ]; then
        zenity --info --title="Note" --width="200" --text="Nothing was deleted. \n\nPlease select at least one launcher and press OK."
    fi
fi
#Loop back to the main menu to continue

if [ "$chose" = "Override system-wide launchers" ]; then
    zenity --question --width=580 --title="Warning" --text="This will import root launchers so they can be configured for this user. \n\nAs a nice side-effect, it will also speed up rendering of the menu in lxpanel. \n\nIt is recommended to <b>DO THIS ONCE</b>. \n\nImporting will NOT overwrite user-configured launchers. \n\nDo you want to proceed?"
    CONF2=$?
    if [ $CONF2 -eq 0 ] ; then
        cd "$HOME/.local/share/applications"
        zenity --info --width=580 --title="Note" --text='Find the directory that contains the *.desktop files you wish to gain control of. Sub-directories will NOT be imported. \n\nKDE users BEWARE: You must checkmark -Only Show In KDE- using the KDE menu editor (ie: kmenuedit) or your menus will show duplicates. \n\nThis operation is much quicker and easier through the CLI.\nOpen a terminal in the KDE directory containing the .desktop files and usually found in /usr/share/applications. As root issue the following: \n\n(Use Copy-Paste but replace your-kde-directory.)\n\nfor FILE in `grep -L ^OnlyShowIn= *.desktop` ; do echo "OnlyShowIn=KDE;" >> /usr/share/applications/your-kde-directory/"$FILE" ; done'
        rootDIR=`zenity --file-selection --title="Confirmation request" --directory --filename=/usr/share/applications/`
echo $rootDIR
            EXIT=$?
            if [ $EXIT -ne 0 ] ; then
                MainMenuLoop
            fi
            if [ "$rootDIR" ]; then
                cd $rootDIR
                for launcher in `ls *.desktop` ; do cp -n $rootDIR/"$launcher" "$HOME/.local/share/applications/"; done
#add any default changes to set after ";" and before "done" ie: echo "OnlyShowIn=LXDE;" >> "/$HOME/.local/share/applications/$launcher;
                cd "$HOME/.local/share/applications" 
            fi
    fi
SanityCheck | zenity --progress --auto-close --auto-kill --width=500 --title="Applying sanity checks and auto-corrections" --text="This essential step ensures LXDE operates error-free. \n\nIt speeds up .desktop file processing and menu access. \n\nPlease, it's worth the wait..."
EXIT=$?
    if [ $EXIT -ne 0 ] ; then
        exit 0
    fi
fi
done
}
MainMenuLoop
clean_up
exit 0

```

---

