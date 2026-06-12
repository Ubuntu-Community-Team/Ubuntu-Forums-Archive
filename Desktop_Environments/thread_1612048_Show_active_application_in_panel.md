---
title: "Show active application in panel"
date: 2010-11-02
forum: Desktop Environments
---

### Post by inflintor on 2010-11-02
I found the ApplicationMenu in Ubuntu Netbook Edition interesting and used this guide to enable it in my desktop setup: 
[http://askubuntu.com/questions/4681/how-do-i-enable-a-mac-style-global-application-menu-in-classic-desktop-edition](http://askubuntu.com/questions/4681/how-do-i-enable-a-mac-style-global-application-menu-in-classic-desktop-edition)

Seeing this OSX style menu made me think about if it would be possible to show the name of the focused application also in the top panel. I wasn't able to find ready made functionality for it, but putting it together with some hacks was actually surprisingly easy.

NOTE: This solution is far from perfect and I have no intentions to develop it further, but I wanted to share it anyway. If you aren't familiar with gconf-tool, you probably shouldn't try this.


[LIST=1]
[*]Enable indicator-applet-appmenu like in the link above (may require restart)
[*]Right click on the panel and select "Add to panel". Add new Clock to the panel next to ApplicationMenu
[*]Press Alt+F2 and type "gconf-editor" and click "Run"
[*]Navigate to settings of the new Clock applet,  apps/panel/applets/applet_1/prefs in my case
[*]Find setting called "format" and enter value "custom" for it. Additionally you can try to put some text to "custom-format" setting which should be visible in your Clock applet
[*]Install wmctrl with command "sudo apt-get install wmctrl"
[*]Create a new file, for example show-app.sh and put following script there (modify the gconftool command accordingly if your path to applet settings was different) ```
#!/usr/bin/env bash
# sudo apt-get install wmctrl
while [ true ];
do
ACTIVEWIN=$(wmctrl -va ":ACTIVE:" 2>&1 | grep -o -e "0x.*$");

LAST_APPLICATION=$APPLICATION;

APPLICATION=$(wmctrl -xl | grep $ACTIVEWIN | cut -d" " -f -4 -s | cut -d"." -f 2 -s);


if [ "$APPLICATION" != "$LAST_APPLICATION" ]; then
#echo $APPLICATION
gconftool -s /apps/panel/applets/applet_1/prefs/custom_format --type string "<b>$APPLICATION</b>"
fi

sleep 0.2;

done
```
[*]Give execution permissions for this file: "chmod +x app-show.sh"
[*]Execute the file: "./app-show.sh"
[*]Now when you click different windows, you should see the names of the applications changing in this applet.
[/LIST]
This cool idea of using Clock to show custom text was presented by konerx in thread [http://wwww.ubuntuforums.org/showthread.php?t=837612](http://wwww.ubuntuforums.org/showthread.php?t=837612). Also the script for controlling Spotify [http://sites.google.com/site/tommymattila/home/spotifycontrol](http://sites.google.com/site/tommymattila/home/spotifycontrol) was very usefull in finding out the focused window and as an example of basic bash scripting.

---

### Post by inflintor on 2010-11-02
And the result should be something like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=174353&stc=1&d=1288732791[/IMG]

---

### Post by mojo2012 on 2010-11-03
Thanks alot man, that's awesome ;-)

I don't understand why this isn't implemented in the indicator-appmenu already? Imho, it's very important to see the name of the current app, at least for desktop users.
It might be not that important for UNE users though.

---

### Post by mojo2012 on 2010-11-04
Unfortunately it turns out that after setting up the above mentioned panel applet, switching workspaces (with shortcuts) doesn't work anymore. :-(

If no window is open everything works normally. But as soon as you open the first window, you can't switch to another desktop via the "switch workspace" panel applet. It always takes you back to the desktop the windows was opened before.

Any solution to that?

---

### Post by inflintor on 2010-11-04
Yep, there seems to be this strange problem. I changed the script in the first message to update the text only when necessary, but it looks like the problem is in fact the wmctrl command.

Here is a quick hack for running other commands only if compiz process isn't active, but it makes this somewhat slower.

```
#!/usr/bin/env bash
# sudo apt-get install wmctrl
while [ true ];
do

COMPIZ_RUNNING=$(top -b -n 1 | sed 15q | grep compiz | wc -l);

if [ "$COMPIZ_RUNNING" == "0" ]; then

ACTIVEWIN=$(wmctrl -va ":ACTIVE:" 2>&1 | grep -o -e "0x.*$");

LAST_APPLICATION=$APPLICATION;

APPLICATION=$(wmctrl -xl | grep $ACTIVEWIN | cut -d" " -f -4 -s | cut -d"." -f 2 -s);

if [ "$APPLICATION" != "$LAST_APPLICATION" ]; then
#echo $APPLICATION
gconftool -s /apps/panel/applets/applet_1/prefs/custom_format --type string "<b>$APPLICATION</b>"
fi
fi

sleep 0.2;

done
```

---

