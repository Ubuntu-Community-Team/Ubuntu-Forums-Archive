---
title: "Desktop Launcher Icon won't change"
date: 2018-07-02
forum: Desktop Environments
---

### Post by mark199 on 2018-07-02
Firstly if I'm duplicating anything I apologise. I've tried searching and can't find anything so I don't think I am.

I run UBUNTU 16.04 lts.
I have a problem with the icon for one of my desktop launchers which refuses to change.
I have edited the .desktop file and it won't change.
I have gone into the properties and selected a totally different icon and it won't change.
I have three background process which each automatically changes the icons for some of 15 desktop launchers and all work perfectly except for this one.
I have deleted the .desktop file and re created it by copying and editing a working one but to no avail.
I have rebooted the system several times (not just for this)

It's starting to dive me mad. Can anyone advise what else I can do?

---

### Post by Xian on 2018-07-04
[COLOR=#000000]Desktop files in [/COLOR]~/.local/share/applications will override the ones of same name in /usr/share/applications.

If that has no impact then post the contents of this particular .desktop file.

---

### Post by mark199 on 2018-07-19
The files in question are in ~/Desktop

Here is the one that is giving trouble

#!/usr/bin/env xdg-open


[Desktop Entry]
Version=0.0
Encoding=UTF-8
Name=ONN7
Type=Application
Terminal=false
Exec=/usr/local/bin/onn7
Icon=/home/mark/Desktop/.onn_icons/ceh7566.png

And here is one that works

#!/usr/bin/env xdg-open


[Desktop Entry]
Version=0.0
Encoding=UTF-8
Name=ONN6
Type=Application
Terminal=false
Exec=/usr/local/bin/onn6
Icon=/home/mark/Desktop/.onn_icons/onn6222.png

---

### Post by monkeybrain20122 on 2018-07-19
> **mark199 said:**
> The files in question are in ~/Desktop

Here is the one that is giving trouble

#!/usr/bin/env xdg-open


[Desktop Entry]
Version=0.0
Encoding=UTF-8
Name=ONN7
Type=Application
Terminal=false
Exec=/usr/local/bin/onn7
Icon=/home/mark/Desktop/.onn_icons/ceh7566.png

And here is one that works

#!/usr/bin/env xdg-open


[Desktop Entry]
Version=0.0
Encoding=UTF-8
Name=ONN6
Type=Application
Terminal=false
Exec=/usr/local/bin/onn6
Icon=/home/mark/Desktop/.onn_icons/onn6222.png

You icon (picture) is in your desktop, but where is the .desktop file you edited? It seems that you are editing a file in /usr/local/share/applications but there is another one in ~/.local/share/applications that overrides it. BTW it seems strange to put your icon in your desktop (even in a hidden folder) I would put it in ~/.local/share/icons just for consistency even though functionally it doesn't matter where you put it.

---

### Post by mark199 on 2018-07-20
[IMG]https://www.dropbox.com/s/gak4ugrr1tgj144/Desktop.png?dl=0[/IMG]No. I'm talking about icons that overlay the desktop background. 
As I said above, the file I am editing is in ~/Desktop which is where all the desktop launcher files reside. 
The images for these particular ones are in ~/Desktop/.onn_icons 
Ones monitoring other things have images different directories.

[COLOR=#000000]/usr/local/share/applications and [/COLOR][COLOR=#000000]~/.local/share/applications are for icons on the launcher bar at the side of the screen.

[/COLOR][IMG]https://www.dropbox.com/s/gak4ugrr1tgj144/Desktop.png?dl=0[/IMG]https://www.dropbox.com/s/gak4ugrr1tgj144/Desktop.png?dl=0

---

### Post by monkeybrain20122 on 2018-07-20
> **mark199 said:**
> 
As I said above, the file I am editing is in ~/Desktop which is where all the desktop launcher files reside. 
[COLOR=#000000]/usr/local/share/applications and [/COLOR][COLOR=#000000]~/.local/share/applications are for icons on the launcher bar at the side of the screen.
[/COLOR]

?? I am not sure what you are talking about. So your .desktop file (a "launcher file") is in ~/Desktop?? The .desktop files should be in ~/.local/share/applications /usr/local/share/applications or /usr/share/applications  for the system to pick up so it appears in menu or the dash etc.

The picture (icon) can be anywhere as long as your Icon= line in the .desktop file uses its correct path. If you have .desktop files for the same application (same EXEC=) then the ones in one of the share/applications directory always take precedent (in order) so the one in ~/Desktop would be overridden. It is possible to create different launchers for the same application where you change the EXEC= line with different environmental variables, but it only works with some applications (I have tried that with rstudio for two different variations of R)

Which DE is that? I don't think it is even possible to put launchers on the Desktop for gnome shell (though I can be wrong on that)

---

### Post by mark199 on 2018-07-23
Yes, you are wrong. [https://askubuntu.com/questions/43246/how-to-configure-gnome-3-to-show-icons-on-desktop](https://askubuntu.com/questions/43246/how-to-configure-gnome-3-to-show-icons-on-desktop)
See my screen shot at [IMG]https://www.dropbox.com/s/gak4ugrr1tgj144/Desktop.png?dl=0[/IMG][COLOR=#000000]https://www.dropbox.com/s/gak4ugrr1tgj144/Desktop.png?dl=0
[/COLOR]
.desktop files in the applications directories are for menus. .desktop files for the desktop are in ~/Desktop. I currently have 39 of them. Of these 18 have their icon image changed by scripts for which 17 work and one does not. It is this lone one that is bugging me.

---

### Post by monkeybrain20122 on 2018-07-23
> **mark199 said:**
> Yes, you are wrong. [https://askubuntu.com/questions/43246/how-to-configure-gnome-3-to-show-icons-on-desktop](https://askubuntu.com/questions/43246/how-to-configure-gnome-3-to-show-icons-on-desktop)
See my screen shot at [IMG]https://www.dropbox.com/s/gak4ugrr1tgj144/Desktop.png?dl=0[/IMG][COLOR=#000000]https://www.dropbox.com/s/gak4ugrr1tgj144/Desktop.png?dl=0
[/COLOR]
.desktop files in the applications directories are for menus. .desktop files for the desktop are in ~/Desktop. I currently have 39 of them. Of these 18 have their icon image changed by scripts for which 17 work and one does not. It is this lone one that is bugging me.

But why would you clutter your Desktop with .desktop files like in Windows? All you need is to press the super key to see the launchers.if you put your .desktop files in the ..share/applications directories they will show up in the dash which functions like having your launchers on the desktop but they won't show up if you put them in ~/Desktop. I was a bit confused by your comment because I never put .desktop files in the Desktop, it is one reason I use unity (gnome shell has the same feature)


Edited: according to the last post of your link gnome 3.2.8 has removed the ability to put icons on .desktop. So which DE are you using??

---

### Post by mark199 on 2018-07-24
I don't clutter my desktop with Icons. I have them there because every single one serves a purpose. 
Most give me quick access to other systems.
The ones that have their image changed by scripts all give me a visual status of some system condition or other which I have decided I want to have.

I'm unsure what you mean by "which DE are you using?" If you mean which Linux distribution I put that right at the start of my original post. Ubuntu 16.04 LTS.

---

### Post by LitlWillie on 2019-03-03
):P  Did you ever solve this? I had a similar issue with a launcher.

I was able to solve this after looking at some postings in another forum. Here is what I learned:

The text after 'Icon= ' in the launcher .desktop config file does nothing until actually choose an icon in the Properties for the launcher.

1. You first right click on the launcher then left click on properties.

2. You left click on the icon that is displayed in the 'Basic' properties tab. A window opens that is titled: Select Custom Icon.

3. You then browse to the location of the icon you wish to use and highlight the file containing the icon. Which in my case was blender.png.

4. You then click on 'Open' in the upper right corner of the Select Custom Icon window.

This changes the icon in the launcher properties dialog.

Closing the dialog changes the icon on the desktop launcher.

---

### Post by coffeecat on 2019-03-04
The OP was trying to modify the config file for launchers on the actual desktop, rather than in the launcher bar. Why on earth they would want to contaminate the Unity desktop environment in that way is totally beyond me.

Anyway, the OP has not logged in since October and this is an old thread in the wrong place.

Closed to prevent further necromancy.

**Edit:** and moved from the chat forum to the appropriate support forum.

---

