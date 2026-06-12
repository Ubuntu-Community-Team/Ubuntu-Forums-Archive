---
title: "HOWTO use Workrave inside Unity"
date: 2012-04-29
forum: Desktop Environments
---

### Post by avl555 on 2012-04-29
This is a HOWTO to use programs like Workrave that require a good system tray to work in Unity. I was very annoyed by Unity's lack of a good system tray that I found a different solution.

Note: Workrave 1.10 will include a Unity indicator, but I wasn't able to compile that version. See it's [NEWS file]("https://github.com/rcaelers/workrave/blob/master/NEWS").

See the attached screenshot for what it will become.

[SIZE="2"]**1. Install packages**[/SIZE]
```
sudo apt-get install xfce4-panel wmctrl
```
You might need to install additional packages with 

[SIZE="2"]**2. Set up panel**[/SIZE]
[LIST=1]
[*] Start xfce4-panel inside a console (or via alt+f2).
[*] Select 'one empty panel' (or something like that) in the popup.
[*] Set the panel in a good location, for example, at the top.
[*] Set the height (in the panel preferences) to 24 pixels.
[*] Set the background to solid color and then the alpha to zero (fully transparent).
[*] Add the panel applet 'notification area' to the panel.
[/LIST]
Warning: don't use the Dash: it will overlay the panel. This will be fixed later.

[SIZE="2"]**3. Make the panel start at system start**[/SIZE]
Create a file somewhere in your home directory with this contents:
```

#!/bin/bash
xfce4-panel &
sleep 3;
wmctrl -l -G | /bin/egrep "*your-hostname* xfce4-panel$" | cut -d " " -f 1 | xargs -n 1 wmctrl -b add,above -i -r

workrave &
```

The line starting with 'wmctrl' does a bit of magic: it finds the window ID of the applet and makes it the topmost window. This way it won't disappear when you use the Dash (Windows/Super-key). Remember to replace the hostname in the *egrep* command. Run ```
wmctrl -l -G
``` to see what you have to grep for.

Make it executable:
```
sudo chmod +x your-panel-applet-script-filename.sh
```

And add it to the list of startup applications.

[SIZE="2"]**4. Bonus: hide letters under it (Firefox page titles etc.)**[/SIZE]
Set the background to the attached 'top bar.png' file. This is a screenshot of a part of the top bar. This hides long page titles of web pages etc.

[SIZE="2"]**5. Bonus: add analog Xfce clock**[/SIZE]
You can also use other panel applets, but the analog Xfce panel applet won't work (the clock is black with a dark-grey background). Use [this]("http://forum.xfce.org/viewtopic.php?pid=25934#p25934") solution to make it visible again. It makes the clock white.

---

### Post by superpico on 2012-06-08
Seeing as there's no reply yet, I wanted to say thank you for this post! It makes workrave usable on Ubuntu 12.04 :)

A small issue for me, I can't get my script to run as a startup application, I get the following error on login:
> The notification area lost selection
Most likely another widget took over the function of a notification area. This area will be unused.


---

### Post by avl555 on 2012-06-10
Superpico, I get that same error sometimes, but it keeps working (icons that are normally in the Unity tray have then moved to the Xfce panel tray.)
Maybe it helps putting a line
```
sleep 10
```
before
```
xfce4-panel &
```
as I have done.
(Actually, I start a lot of programs this way, by putting them in the bin/startup file and inserting [FONT="Courier New"]sleep[/FONT]s between them, this way preventing that the computer becomes very slow after logging in.)

---

### Post by karlrt on 2013-02-14
Hi, 

[https://launchpad.net/~rob-caelers/+archive/workrave](https://launchpad.net/~rob-caelers/+archive/workrave)

the ppa claims to fix this (also in 12.04) but if I enable the applet i dont see anything changing in the applet area :(

---

### Post by dda on 2013-03-13
karlrt, you need to enable it in dconf editor, add to desktop -> unity -> panel

---

### Post by Mikael_Fremling on 2014-02-10
On ubuntu 13.10 the path com.canonical.unity.panel has disapeared. Is there some other path to use?

In the flip side. The settings of workrave can be acceced directly from dconf through org.workrave.timers

---

### Post by rubo77 on 2014-11-30
I uploaded your attached Image here:
[IMG]http://i.imgur.com/IW1VUUU.png[/IMG]


I managed to compile workrave from source:
[http://askubuntu.com/questions/554724/compile-workrave-from-source](http://askubuntu.com/questions/554724/compile-workrave-from-source)

But still no Unity indicator
I guess this solution won't work since 13.10 so Is there a solution for Ubuntu 14.10 also?

As a workaround, I can access the settings by rightclicking on the indicator Window:

[IMG]http://i.imgur.com/wi4aFws.png[/IMG]

---

### Post by Ivan_Koldaev on 2015-04-03
> **rubo77 said:**
> 
As a workaround, I can access the settings by rightclicking on the indicator Window:

[IMG]http://i.imgur.com/wi4aFws.png[/IMG]
Also, if you accidentally closed the small indicator window, you would lost last option to access Workrave settings.
To restore the indicator window do following:
[LIST=1]
[*]```
dconf write /org/workrave/gui/main-window/enabled true
```
[*]```
sudo killall workrave
```
[*]Run workrave. The small indicator window (as pictured above) will appear.
[/LIST]

---

