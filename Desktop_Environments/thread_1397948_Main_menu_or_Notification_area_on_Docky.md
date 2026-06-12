---
title: "Main menu or Notification area on Docky?"
date: 2010-02-03
forum: Desktop Environments
---

### Post by winchendonsprings on 2010-02-03
What I'd like to do is get rid of all panels and use Docky exclusively. In order for that to happen I'd need at least 1 thing that I cant seem to add to Docky and cant seem to find a current answer to.

1. I need a Main menu option. No need for "Places"  because everything in that menu can be done from inside a window. I need "Applications" and "System". 
Applications - because I don't want to forget I have something or forget a name.
System - because I need to get to Preferences and Administration.

Docky is essentially a large notification area so that isn't needed and a workspace switcher already exists.

---

### Post by nilarimogard on 2010-02-04
Until those will be developed, there is nothing you can do... Or you can use Avant Window Decorator (AWN) 0.4...

---

### Post by bananasareformonkeys on 2010-02-07
There are a couple of workarounds...

For a menu, I use an application browser.  To do this right-click on the desktop and create Launcher...
name it application browser (or whatever) and in the command put:
/usr/lib/gnome-main-menu/application-browser

Then just hit Ok, and drag it onto Docky.

Similarly, if you want a system menu, create another launcher (control center) and this time just use the command:
gnome-control-center


one other note, if you want a button to shutdown you can create a shutdown.desktop file and write this in it:

#!/usr/bin/env xdg-open

[Desktop Entry]
Name=Shut Down...
Type=Application
Exec=gnome-session-save --shutdown-dialog
Terminal=false
Icon=system-shutdown
Comment=Shut down or restart the computer
Categories=Utility;


Just drag that to the dock.  For logout use create a logout.desktop file:



#!/usr/bin/env xdg-open

[Desktop Entry]
Name=Session Logout Dialog
Comment=Prompt the user to log out of their session
Exec=gnome-session-save --logout-dialog
Terminal=false
Type=Application
Icon=system-log-out
Hidden=true
Categories=GNOME;Application;System;
OnlyShowIn=GNOME;
X-Ubuntu-Gettext-Domain=gnome-main-menu

---

### Post by stinkeye on 2010-02-07
> **winchendonsprings said:**
> What I'd like to do is get rid of all panels and use Docky exclusively. In order for that to happen I'd need at least 1 thing that I cant seem to add to docky and cant seem to find a current answer to.

1. I need a Main menu option. No need for "Places"  because everything in that menu can be done from inside a window. I need "Applications" and "System". 
Applications - because I dont want to forget I have something or Forget a name.
System - because I need to get to Preferences and Administration.

Docky is essentially a large notification area so that isn't needed and a workspace switcher already exsists.


If you need a main menu alt +F1 will bring up the menu at the mouse cursor if you don't have an icon on the panel.
I use [**_[COLOR="DarkRed"]easystroke[/COLOR]_**]("http://sourceforge.net/projects/easystroke/files/") to assign alt +F1 to a mouse gesture.
you can also add terminal commands to gestures.

If you use gnome-do you can enable the gnome session management plugin to run commands such as logout, restart and shutdown.

I use gnome-do in classic mode and Docky as my dock.

---

### Post by winchendonsprings on 2010-02-07
great

thanks a lot. bananasareformonkeys, the application and system menus are awesome. just what I was looking for. 

Now is there a way to disable the top panel?

---

### Post by winchendonsprings on 2010-02-07
I'd prefer a cleaner way than this - 

> **Re: Disable / Remove top panel**             
                                                                searched the forums, and  this is what *JohnnyD'* said about three days ago:

     Quote:
                    You can disable the gnome panel by going to Sessions-->Current Session and remove gnome panel from the list of running applications.

Then go to Session Options and click on the Remember button..                      

---

### Post by winchendonsprings on 2010-02-08
if anyone is interested this is what I've done for now - 

-remove everything from the panel
-turn the transparency of the panel all the way up so it is clear
-in the gconf editor I turned the unhide delay up to 100000 (located at /apps/panel/toplevels/top_panel_screen0 )

it's a simple solution and makes it easy to bring the panel back if i ever want to. only downfall is that there is a 1 pixel width row of clear panel at the top of the screen. unnoticeable to anyone but you

---

### Post by tylerannosaurus on 2010-09-10
This was recently covered on the OMG! Ubuntu blog. The link discusses AWN but you can do the same for Docky.

To COMPLETELY remove the gnome panel, open a terminal and type this command:

```
sudo mv /usr/bin/gnome-panel ~/gnome-panel
```

If you want to get the panel back, open a terminal and type this command:

```
sudo mv ~/gnome-panel /usr/bin/gnome-panel
```

If you have some sort of menu docklet like described above, it won't work anymore, however, if you've kept Docky updated there are a lot of useful helpers now. I use Gnome Do for any programs I don't access as often.

Source:

[OMG! Ubuntu]("http://www.omgubuntu.co.uk/2010/09/how-to-fully-replace-your-gnome-panels-with-awn/")

Edit:

Remember to either restart or log off and on again for the effect to take place.

There are also OTHER suggestions in the comments as to just change gconf. Either way. If you want to retain the ability to change preferences, you can always install Ubuntu Tweak and put that on the Dock or just search it up in Do.

---

### Post by stinkeye on 2010-09-11
A better way to remove gnome-panel is in 
gconf-editor /desktop/gnome/session/required_components_list
and remove "panel" from the list.
Double click on the value and a dialogue box comes up ,allowing you to remove "panel".

---

### Post by Teabicky on 2010-09-14
On my system I have gotten rid of the top panel.  I have added workspace, network manager and session manager docklets to docky.  Then I removed all of the applets from the top panel. I then right clicked on the top panel and opened properties.  In properties I was able to uncheck *Expand*, check *Autohide* and set *Orientation* to *Bottom*.

Now when I hover over the panel it appears as if to be part of Docky.  Its not perfect but I think its pretty good.

N.B. If you don't have Docky set to Autohide, or similar equivalent then there is no need to set *Autohide* in the panel preferences. 


Here's the screen shot...

[IMG]https://dl-web.dropbox.com/get/Photos/Screenshot2.png?w=9df406d5[/IMG]

---

### Post by ben2talk on 2011-02-07
Well there IS something you can do.

On my setup, I recently started up AWN and forgot to close docky.

I set AWN at the bottom of the screen (good that it's 1440 wide...) and in Preferences check the box to Expand the panel and set the icon size to 24 (or less), Style=NONE (leaves it blank in the middle - see later), behaviour is set to Window Dodge, Keep below and then I customised the icon effects (all set to 'classic' except for the attention which I set to squish)

If you have a wide docky, now's the time to remove stuff to make it smaller - set it to zoom 200% with smaller icons so it fits between the AWN areas nicely.

Lovely ;)
I removed 'task manager' and 'launchers' because this is Docky's domain - I love docky, especially now I worked out that I need to go into settings and enable Zeitgeist to get integration.

Icons - overlay best quality with app icon

Now with the applets, you need to put your Indicator Applet, and then an Expander in the centre - on the other side, put your Notification area. 

These will now appear in the two bottom corners, with Docky in the centre - it's very nice (replaced Trayer for me)

So the best of both worlds I think - add a nice Stacks applet to AWN, set Docky to auto or intellihide and you're onto a very clean desktop where the notifications don't hide.

Final settings on the AWN 'advanced' tab - Reflection offset 0
-Icon alpha 1.0
done.

---

### Post by bishop379 on 2011-07-03
> **stinkeye said:**
> If you need a main menu alt +F1 will bring up the menu at the mouse cursor if you don't have an icon on the panel.
I use [**_[COLOR=DarkRed]easystroke[/COLOR]_**]("http://sourceforge.net/projects/easystroke/files/") to assign alt +F1 to a mouse gesture.
you can also add terminal commands to gestures.

If you use gnome-do you can enable the gnome session management plugin to run commands such as logout, restart and shutdown.

I use gnome-do in classic mode and Docky as my dock.

Like the desktop, and docklets.

---

### Post by isbiyanto on 2012-02-17
omg....

---

