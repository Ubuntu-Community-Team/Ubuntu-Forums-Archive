---
title: "Power Button Missing"
date: 2010-02-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by monxster on 2010-02-10
Hi Guys,

As of today the little power button icon on the top right hand corner of my screen has disappeared leaving an empty space right next to the time.

I can still power off the PC using Ctrl + Alt + Del but it would be great to have the button back.  Does anyone know how to do this and why it is gone?

Also I have already tried adding to the panel but that results in my having a power button to the right of the time and weather icons and not having the power button where it is by default.

Thanks!
Monxster

---

### Post by Satoru-san on 2010-02-10
This is posted in the wrong location.

[http://ubuntuforums.org/forumdisplay.php?f=329](http://ubuntuforums.org/forumdisplay.php?f=329)

You might want to click the report button on your post and ask to have it moved to "Desktop Enviornments"

I thought you were saying that the powerbutton on your computer didnt function.

---

### Post by mikewhatever on 2010-02-11
Well, you have to decide if the power (Shut Down I guess) button is or is not missing. If it is, add it to the panel, and if you don't like the place, move it by simple dragging. Please note, there is no correct location for the Shut Down button.

---

### Post by gbrainin on 2010-02-11
In order to move an item on the panel to the right of the default items (network icon, time, etc.), you first need to unlock those items.  You can then move the power button where you want, then re-lock everything.

---

### Post by novum on 2010-02-18
I've had the same "problem" with the latest update of Ubuntu Jaunty, power button just disappeared, couldn't find it when I wanted to turn off the PC.

Here's what happened: it was moved to the menus - look in the system menu :) If you don't like it there, you can add or move it as suggested above, to the top right corner or wherever you're used to having it - or rather them, as I think there's no simple way to have it exactly as before.

---

### Post by MetalTim on 2010-02-23
I know what you're saying.  This happened to me just a few days ago!?  Could it be an update gone wrong?  This is typical of Windoze, not Ubuntu.  For a temporary solution, I right-clicked the top panel, clicked "Add to Panel", and chose Main Menu.  This creates a new Ubuntu icon on your panel, and there you'll see the lock screen and logout/shutdown options.  But it also has every other program files and controls along with it.  I am with you, I would like my little button back to lock my screen or shutdown my computer.  I hope somebody has an answer.

---

### Post by novum on 2010-02-23
@MetalTim
nothing is really gone wrong, the button was just moved. Check in the system menu, where you have Preferences and Administration (and Help) - now there are also Lock Screen, Log Out and Shut Down buttons. If you'd like to have it where it was, one solution is what you mentioned, another is to add Lock Screen, Log Out and/or Shut Down buttons - but you can only add them separately, there is no Power Button like before. You can create something similar though: add Drawer to the panel and then right-click it and click Add to Drawer, then add whatever buttons you want in there.

---

### Post by micmac303 on 2010-04-01
Same thing has happened to me and I have added the shut down button but it's not the same as it was.

Is it really not possible to have things back as they were?

10.04 comes out soon - will an update to this sort out the problem?

---

### Post by mikebravo on 2010-06-13
Well MicMac, do not hold your breath. I had the 10/04 (Lucid) desktop for three days when the shutdown button disappeared. I went to control panel applets and now I have a big red bulls eye for a shutdown button. I am not a happy camper. I want my desktop back to stock. Ours is not an isolated problem nor is it a new problem. My first forum search reported ali.hammed having the problem back on 6July09. I will keep looking for an answer but so far all I have gotten from the highly caffeinated is a big shrug.
Later: found my answer. I am a noob so I might have this a little wrong but if the Synaptic Package Mgr. says you have the "indicator-applications" package installed, then all you should have to do is right click the control panel, select "add to panel" and scroll down and click on the not so intutively named "add indicator applet" Your name and stop button will reappear and if your panel is not locked you can drag them to where you want them.

FYI I think my name and icon went south after I removed the packages left behind after I removed K3b. Why would I do that you ask? Because it installed a menu item called "Akonaditray" that was to all appearances non functional. Cluttering my menues with something that does nothing really jacks my jaws.

---

### Post by mikebravo on 2010-06-13
> **Satoru-san said:**
> This is posted in the wrong location.

[http://ubuntuforums.org/forumdisplay.php?f=329](http://ubuntuforums.org/forumdisplay.php?f=329)

You might want to click the report button on your post and ask to have it moved to "Desktop Enviornments"

I thought you were saying that the powerbutton on your computer didnt function.

----------------------------------------------------------

Why do we even have a Dell forum? Dell's are just computers are they not? Why does having Ubuntu installed make them special? The guy probably has a Dell and so figures this is where his post belongs. Yes, it should be in "Desktop Environsment".

---

### Post by Wooley on 2010-06-21
Been having this problem in 10.04. I found changing to a new theme and then back again restore the power button.

---

### Post by rushtoshankar on 2010-07-08
To overcome this problem, right click the panel->select 'Add to panel..', a new window will popup. Select 'Indicator Applet Session', click add. Move the item to your desired place. Enjoy!

---

### Post by spillage2 on 2010-08-01
adding the indicator applet session will fix it sort of but i dont think this is the answer. I too have just had this happen in 10.04 lucid.

it used to show just the grey power circle but adding the session applet includes extras like the name and a box for chat sessions which takes up more room and looks untidy.

I dont even have a red button to add to my panel.

UPDATE...

follow the above thread to add the session applet but add it twice and delete the first one with chat options and name of user. The second add will only add the power button..

---

### Post by cbrs70 on 2010-09-01
I have found the solution to the missing power button problem.  Right click on the panel and select properties.  click on "Show hide buttons", this will bring back your missing power button, then you can un-check this if you wish.  Power button stays.  
I did notice this only became a problem after compiz management was installed.  however since the fix, I've not had a problem.

---

### Post by dbldub on 2010-10-05
> **mikebravo said:**
> Well MicMac, do not hold your breath. I had the 10/04 (Lucid) desktop for three days when the shutdown button disappeared. I went to control panel applets and now I have a big red bulls eye for a shutdown button. I am not a happy camper. I want my desktop back to stock. Ours is not an isolated problem nor is it a new problem. My first forum search reported ali.hammed having the problem back on 6July09. I will keep looking for an answer but so far all I have gotten from the highly caffeinated is a big shrug.
Later: found my answer. I am a noob so I might have this a little wrong but if the Synaptic Package Mgr. says you have the "indicator-applications" package installed, then all you should have to do is right click the control panel, select "add to panel" and scroll down and click on the not so intutively named "add indicator applet" Your name and stop button will reappear and if your panel is not locked you can drag them to where you want them.

FYI I think my name and icon went south after I removed the packages left behind after I removed K3b. Why would I do that you ask? Because it installed a menu item called "Akonaditray" that was to all appearances non functional. Cluttering my menues with something that does nothing really jacks my jaws.

Thanks =)!!! This worked for me although it is  now in two parts, 'Indicator Applet' and 'Indicator Applet Session'. I was missing the Indicator Applet Session.

---

### Post by spillage2 on 2010-10-05
I found this to be a great little bit of kit for restoring you panels.

just save it as a new file called panelrestore.sh and double click to run:

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

---

### Post by dmurphy787 on 2010-11-06
I have Ubuntu 10.04 and I have the same problem with the power button but I have noticed it usually only happens when an update is due.  To fix it I go to "System-Administration-Update Manager" and install any updates.  I then press "ctrl+alt+del" and restart if the button has not restored.  When the pc restarts the button is back to normal.
The issue is a little annoying but if you do what I do, you will keep the integrity of your original look and make your life easier.

---

