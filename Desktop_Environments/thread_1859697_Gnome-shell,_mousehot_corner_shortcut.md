---
title: "Gnome-shell, mouse/hot corner shortcut"
date: 2011-10-14
forum: Desktop Environments
---

### Post by Guillaumeb on 2011-10-14
Hello, 

Do you know if there is a way to trigger the GNOME-Shell windows management with a mouse button (say the middle button) instead of the Windows key

I used to do this thru Compiz setting manager for Gnome classic but it does not seem to be working with GNOME-Shell

also, is it possible to change the top left hot corner and replace it to the right ?

thank you very much

---

### Post by RSparker on 2011-10-16
I'm also looking for the same thing, and I'm surprised it hasn't come up more often. As far as I can tell, there is no way to bind a mouse button to the overview toggle, which doesn't make much sense since modern mice have a gazillion buttons, but that's gnome shell for you.

Ditto for the hot corner.

---

### Post by drawkcab on 2011-10-16
For me it's the super(windows) button.

---

### Post by BazookaAce on 2011-10-16
Since this i nearly the same question, and i can't bother making a new thread, is it possible to get the "Windows overview", (when i put my mouse in a corner, and i get an overview of my open windows). It was possible with Compiz, but as we know, Compiz doesn't work in Gnome-Shell.. 

So, anybody?

---

### Post by Hakunka-Matata on 2011-10-16
If you have not yet installed 'gnome-tweak-tool', that may provide the functionality you're missing.  Installing it will give you an application named "Advanced Settings"

[http://ubuntuguide.net/gnome-tweak-tool-a-gui-to-customize-advanced-gnome-3-options](http://ubuntuguide.net/gnome-tweak-tool-a-gui-to-customize-advanced-gnome-3-options)

---

### Post by Guillaumeb on 2011-10-17
Well i'm not a hard core geek and though I do have the GNOME Tweak tool installed, I have not find an extension to plug to it relative to mouse shortcut. I did see some hot corner tweaks but for some reasons they did not work for me (probably my fault though)

Anyways, the upper left corner simply is anti-usable for the majority of us hand-righted

---

### Post by cbowman57 on 2011-10-20
There was a righthotcorner extension, as well as one to move the corner but it broke with gnome 3.2.  The author has stated that that he will update all the extensions within a couple weeks.

Keep your eye on this site. [http://www.fpmurphy.com/gnome-shell-extensions/](http://www.fpmurphy.com/gnome-shell-extensions/)

---

### Post by Rasa1111 on 2011-10-22
Can't wait to get the hot right corner back!

---

### Post by stinkeye on 2011-10-22
> **Guillaumeb said:**
> Hello, 

Do you know if there is a way to trigger the GNOME-Shell windows management with a mouse button (say the middle button) instead of the Windows key

I used to do this thru Compiz setting manager for Gnome classic but it does not seem to be working with GNOME-Shell

also, is it possible to change the top left hot corner and replace it to the right ?

thank you very much
You can set the super key to a mouse button using **easystroke** and **xdotool**.
```
sudo apt-get install easystroke xdotool
```

Open easy stroke and go to preferences.
Change the gesture button to 3(right mouse)
Go to additional buttons and click add.
Click your middle button in the pop up window.
Click ok and goto the actions tab.

Click on the add action button and enter the name with type:command.
Enter **xdotool key Super** as the command.
Hit the record stroke button and click your middle mouse.

If you hold down the middle button for a few secs while recording
it will cause a slight delay before the middle click action is initiated.
This allows the middle click paste feature to still be used with quick clicks.
Notice the difference in the second attachment of the stroke recording.


You can also use xdotool to trigger the super key when the mouse is placed in the top right corner with this script.
```
#!/bin/bash

while [ 1 ];
do
	m=`xdotool getmouselocation|sed 's/x:\(.*\) y:\(.*\) screen:.*/\1, \2/'`
	if [ "$m" = "[COLOR="Red"]1679[/COLOR], 0" ];
	then
                xdotool key Super
                sleep 1
                
	fi
done
```
This works with my screen resolution of 1680x1050
To get your x resolution
run this in the terminal while your mouse is in the top right corner
```
xdotool getmouselocation
```
and [COLOR="red"]adapt[/COLOR] the script accordingly.

[COLOR="Magenta"]**Note: [/COLOR] this is something I made used from other scripts I have downloaded and it looks like it uses a lot of CPU so 
may not be scripted properly.
May be a start though for someone who knows what they're doing.

---

### Post by btittelbach on 2012-02-06
instead of installing xdotool, you can also just execute the following:
```

dbus-send --session --type=method_call --dest=org.gnome.Shell /org/gnome/Shell org.gnome.Shell.Eval string:'Main.overview.toggle();'

```

---

