---
title: "How To: Replace LXDE Panel With Gnome Panel"
date: 2009-09-18
forum: Desktop Environments
---

### Post by Lukios on 2009-09-18
I have seen this question asked a few times without any real answer given, other then the fact that it can't be done. Some may ask, "why would you want to do this?" Simply put, the LXDE panel is ugly. The other question that my come to mind is "how will this effect my performance" Ironically, it wont. When running “top” the cpu and memory usage of gnome panel matches that of lxpanel which for me is usually around 2%. So if your concerned about performance on an older system, you should have no problems. I will also show you how to edit your mintMenu to logout of the lxsession instead of the gnome-session as well as how to completely replace nautilus with pcmanfm.



**Replacing lxpanel with gnome-panel:**

If you are running LXDE from the main version of Ubuntu or Mint: (which comes with Gnome)

```
sudo apt-get install lxde
```If you have not already done so.

Once you installed LXDE, log out and change your session to LXDE. In order to replace the LXDE panel with the Gnome panel we will have to edit the autostart file in /etc/xdg/lxsession/LXDE/ . You can do this by pasting the following in the terminal.

```
sudo leafpad /etc/xdg/lxsession/LXDE/autostart
```You should now see the following:

@lxde-settings
@xscreensaver -no-splash
[color=#ff0000]@lxpanel --profile LXDE[/color]
@pcmanfm -d

Simply replace "@lxpanel --profile LXDE" with "@gnome-panel". Save the file, logout, then log back in to your LXDE session and you should now see the Gnome panel in place of your LXDE panel. It should now look like this.

@lxde-settings
@xscreensaver -no-splash
[color=#ff0000]@gnome-panel[/color]
@pcmanfm -d
[i]
If you are running a version of Ubuntu or Mint that has kde, xfce, flux, etc. or if your installing from a mini.iso you will have to install gnome panel separately after installing LXDE.[/i] 

```
sudo apt-get install gnome-panel
```After you have installed gnome panel follow the same steps listed above.



**Editing Gnome Main Menu**

*Note: This is simply a workaround that allows your to easily be able to logout of lxde without having to recompile gnome-menu and editing the source.*

First you will have to download pessulus (don't worry you can remove it after we are done without effecting changes)

```
Sudo apt-get install pessulus
```Start up pessulus. You will see some tabs that should include General, Panel, Epiphany Web Browser, and Gnome Screensaver. Click on panel and check the box that says Disable logout. This program will also allow you to disable several other options such as applets, which you may want to do if you want to disable gnome specific ones.

Now you can remove the program if you would like

```
sudo apt-get remove pessulus
```Now we are going to make a custom logout button to go into the menu. Right click on the menu and select edit menu. You can put this logout anywhere you like but for easy access we will add it to the applications section. Simply click on applications, then the "new item" tab and add the following:

Name: Logout or shut down (which ever you prefer)
Command: lxsession-logout

Click ok and that's it. 


[b]
Editing the Gnome Bar Menu[/b]

This is the same as the above steps accept you will need to add the custom logout to the system part of the menu. I would also suggest cleaning up your menu by going to 

```
/usr/share/applications/
```and get rid of the About GNOME.desktop and help.desktop which will put your custom logout closer to the bottom where it should be.



**Editing mintMenu:**

**Go to**

```
 /usr/lib/linuxmint/mintMenu/plugins/system_management.py
```and edit 125 and 131, replace "gnome-session-save --logout-dialog" with "lxsession-logout" on both lines. 

Button5 = easyButton( "system-log-out", self.iconsize, [_("Logout")], -1, -1 )
Button5.connect( "clicked", self.ButtonClicked, "[color=#ff0000]gnome-session-save --logout-dialog[/color]" )
Button5.show()
self.systemBtnHolder.pack_start( Button5, False, False )
self.mintMenuWin.setTooltip( Button5, _("Log out or switch user") )

Button6 = easyButton( "system-shutdown", self.iconsize, [_("Quit")], -1, -1 )
Button6.connect( "clicked", self.ButtonClicked, "[color=#ff0000]gnome-session-save --shutdown-dialog[/color]" )
Button6.show()


**To**


Button5 = easyButton( "system-log-out", self.iconsize, [_("Logout")], -1, -1 )
Button5.connect( "clicked", self.ButtonClicked, "[color=#ff0000]lxsession-logout[/color]" )
Button5.show()
self.systemBtnHolder.pack_start( Button5, False, False )
self.mintMenuWin.setTooltip( Button5, _("Log out or switch user") )

Button6 = easyButton( "system-shutdown", self.iconsize, [_("Quit")], -1, -1 )
Button6.connect( "clicked", self.ButtonClicked, "[color=#ff0000]lxsession-logout[/color]" )
Button6.show()



**Replace nautilus with pcmanfm (mintMenu):**

*You can download the mintMenu and it's dependencies [here]("http://packages.linuxmint.com/")*

sudo leafpad /usr/lib/linuxmint/mintMenu/plugins/places.py

**Edit lines 104-105**

Button2 = easyButton( "user-home", self.iconsize, [_("Home Folder")], -1, -1 )
Button2.connect( "clicked", self.ButtonClicked, "[color=#ff0000]nautilus --no-desktop[/color]" )


**To**

Button2 = easyButton( "user-home", self.iconsize, [_("Home Folder")], -1, -1 )
Button2.connect( "clicked", self.ButtonClicked, "[color=#ff0000]pcmanfm[/color]" )


**and edit lines 135-136**

Button4 = easyButton( "gnome-fs-desktop", self.iconsize, [_("Desktop")], -1, -1 )
Button4.connect( "clicked", self.ButtonClicked, "[color=#ff0000]nautilus[/color] " + desktopDir )
[b]
To[/b]

Button4 = easyButton( "gnome-fs-desktop", self.iconsize, [_("Desktop")], -1, -1 )
Button4.connect( "clicked", self.ButtonClicked, "[color=#ff0000]pcmanfm[/color] " + desktopDir )

Note: To my knowledge, there is no "my computer" or "network" folders for pcmanfm, so if you would like to keep the functionability of the "computer" and "network" button then just keep nautilus for those settings which are in buttons 1 and 3. If this changes I will update this, but as of lxpanel 5.1 these features have not been implimented. There also no trash at this moment for pcmanfm so anything you do delete through the pcmanfm file manager will be permanently deleted and the trash so you can either delete lines 119-162, leave them alone, or wait till pcmanfm has the trash feature and edit these lines in the future. There are a few work arounds for adding a trash system in pcmanfm which I may add to the tutorial in the future. Let me know if I'm missing anything. 


**Replacing nautilus with pcmanfm (gnome-menu):**

**Step 1**

```
sudo leafpad /usr/share/applications/nautilus-computer.desktop
```**Edit the following lines**

[Desktop Entry]
Encoding=UTF-8
Name=Computer
Comment=Browse all local and remote disks and folders accessible from this computer
[color=#ff0000]TryExec=nautilus[/color]
[color=#ff0000]Exec=nautilus --no-desktop computer:[/color]
Icon=computer
Terminal=false
StartupNotify=true
Type=Application
Categories=GNOME;GTK;Core;
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
[color=#ff0000]X-GNOME-Bugzilla-Product=nautilus[/color]
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.26.2
[color=#ff0000]X-Ubuntu-Gettext-Domain=nautilus[/color]

**To**

[Desktop Entry]
Encoding=UTF-8
Name=Computer
Comment=Browse all local and remote disks and folders accessible from this computer
[color=#ff0000]TryExec=pcmanfm[/color]
[color=#ff0000]Exec=pcmanfm /[/color]
Icon=computer
Terminal=false
StartupNotify=true
Type=Application
Categories=GNOME;GTK;Core;
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
[color=#ff0000]X-GNOME-Bugzilla-Product=pcmafm[/color]
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.26.2
[color=#ff0000]X-Ubuntu-Gettext-Domain=pcmanfm[/color]

**Step 2**

```
sudo leafpad /usr/share/applications/nautilus-folder-handler.desktop
```[Desktop Entry]
Encoding=UTF-8
Name=Open Folder
[color=#ff0000]TryExec=nautilus[/color]
[color=#ff0000]Exec=nautilus --no-desktop %U[/color]
NoDisplay=true
Terminal=false
Icon=folder-open
StartupNotify=true
Type=Application
MimeType=x-directory/gnome-default-handler;x-directory/normal;inode/directory;application/x-gnome-saved-search;
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
[color=#ff0000]X-GNOME-Bugzilla-Product=nautilus[/color]
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.26.2
[color=#ff0000]X-Ubuntu-Gettext-Domain=nautilus[/color]

**To**

[Desktop Entry]
Encoding=UTF-8
Name=Open Folder
[color=#ff0000]TryExec=pcmanfm[/color]
[color=#ff0000]Exec=pcmanfm %U[/color]
NoDisplay=true
Terminal=false
Icon=folder-open
StartupNotify=true
Type=Application
MimeType=x-directory/gnome-default-handler;x-directory/normal;inode/directory;application/x-gnome-saved-search;
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
[color=#ff0000]X-GNOME-Bugzilla-Product=pcmanfm[/color]
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.26.2
[color=#ff0000]X-Ubuntu-Gettext-Domain=pcmanfm[/color]

---

### Post by Lukios on 2009-10-07
I have updated the tutorial

---

### Post by earthpigg on 2009-10-07
nice.

i linked to this thread [here]("http://sites.google.com/site/masonux/home/ease-of-use#TOC-Ubuntu-s-Default-Top-Panel").

---

### Post by Lukios on 2009-10-07
One thing to note is even though it does pull in some dependencies its really not all that much (106mb) and it does not effect performance either unless you have a whole bunch of applets running. The lxpanel runs about the same amount of resources, at least on the tests I have done. In any case, I'm glad I could contribute to your work.

---

### Post by Lukios on 2009-10-08
I have now updated this tutorial to include replacing the gnome logout with the lxde logout. Though there are still a few things that could be tweaked (much of which has to be done through editing and recompiling the source) you should now have a fully functional gnome-panel.

---

### Post by dzon65 on 2010-03-06
Yep,really nice.Tried several panels and docks,all had their problems.Since it doesn't use more resources,replacing lx with the gnome panel is a sane thing to do.
Kind regards,J.

---

### Post by amjjawad on 2011-09-07
I'm going to try this out just for me to see how things will work.
I prefer to keep the LXpanel as it's though but that's me :)

Thank you!

---

### Post by kerry_s on 2011-09-07
> **amjjawad said:**
> I'm going to try this out just for me to see how things will work.
I prefer to keep the LXpanel as it's though but that's me :)

Thank you!

i agree, lxpanel is good enough for the basics, just needs more love. ;)

i prefer a dock for launchers/taskmanager, lxpanel for the rest.
i also prefer xfce4 parts instead of gnome parts if i can. like swapping openbox for xfwm4, to get nicer window themes, plus it has it's own compositor for what ever dock you might want to use, i'm currently using plank, sure it's still young, but it is usable.

---

### Post by amjjawad on 2011-09-08
> **kerry_s said:**
> i agree, lxpanel is good enough for the basics, just needs more love. ;)

LXDE Project as a whole is great but yes, indeed it needs more care and support. I'm doing my best to support it as much as possible simple because I believe in it and looking forward to see it in much better position.
Lubuntu is being used more than Xubuntu as per distrowatch.com.
And LXDE is faster for sure.

> i prefer a dock for launchers/taskmanager, lxpanel for the rest.
i also prefer xfce4 parts instead of gnome parts if i can. like swapping openbox for xfwm4, to get nicer window themes, plus it has it's own compositor for what ever dock you might want to use, i'm currently using plank, sure it's still young, but it is usable.
When first I saw your screenshot, I thought it's GNOME or something but when I found the LXDE Logo, I figured out what is going on :D
SO NICE!
However, for me, I don't do anything to my Lubuntu Installation. I keep it as simple and easy as possible.

I just did this last night: [http://forum.lxde.org/viewtopic.php?f=8&t=31300](http://forum.lxde.org/viewtopic.php?f=8&t=31300)

As for Themes and stuff, I don't waste my time with it not because I don't like it, I do like it actually but because there are lots of themes and I need lots of time to try and see which one is better :)
But I don't mind if you please guide me through the steps of how to do that to LXDE Desktop? any link would be great at least I can direct someone else to it if needed :)

Thank you!

---

### Post by kerry_s on 2011-09-08
> But I don't mind if you please guide me through the steps of how to do that to LXDE Desktop? any link would be great at least I can direct someone else to it if needed 

dude, there's a lot of bending it to my will there. :lolflag:
i do a lot of things in a non-standard way.
for example, i prefer my autostart stuff in a file in my home folder so i don't have to be root to add entries. so my /etc/xdg/lxsession/Lubuntu/autostart looks like this.

```
@nm-applet
@lxpanel --profile Lubuntu
[B]@xset s off off
@xfce4-power-manager[/B]
@pcmanfm --desktop --profile lubuntu
@/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
**@$HOME/Scripts/lxde-autostart**

```

i got rid of xscreensaver cause i never use it, so changed to command there to just turn it off, swapped out gnome-power-manger for xfce4-power-manager like it is in lubuntu 11.10, then just add that 1 line to run my startup.
which looks like this:

```
#!/bin/sh

xfce4-settings-helper &
plank &
pidgin &
transmission-gtk -m &
sudo service ushare restart &

exit 0
```

changing the window manager is done in:
~/.config/lxsession/Lubuntu/desktop.conf
like i said, window themes in xfce4 just look nicer.

mine looks like this:
```

[Session]
window_manager=**xfwm4 --sm-client-disable --daemon**

[GTK]
sNet/ThemeName=Ambiance
sNet/IconThemeName=Faenza-Dark
sGtk/FontName=Ubuntu 11
iGtk/ToolbarStyle=3
iGtk/ButtonImages=1
iGtk/MenuImages=1
iGtk/CursorThemeSize=18
iXft/Antialias=1
iXft/Hinting=1
sXft/HintStyle=hintfull
sXft/RGBA=rgb

sGtk/ColorScheme=
iGtk/ToolbarIconSize=3
iNet/EnableEventSounds=1
iNet/EnableInputFeedbackSounds=1

sGtk/CursorThemeName=oxy-white

[Mouse]
AccFactor=20
AccThreshold=10
LeftHanded=0

[Keyboard]
Delay=500
Interval=30


```

the dock i'm using is very new, it's called plank:
[http://www.ubunturoot.com/2011/07/plank-lightweight-dock-app.html](http://www.ubunturoot.com/2011/07/plank-lightweight-dock-app.html)

it's still goofy, but there working on it, there have been updates like every other day. the main problem is the app indicator, that shows the app is running sometimes doesn't work, a quick restart brings it back, i have a script for that. also some apps don't have "keep in dock", so you have to manually add them, so i use zenity & some scripts for that.
there is no gui for plank, it's simple file editing.

ps: just a reminder if you ever do switch wm's, you need to use it's settings tools, like i have to xfce keyboard to create keyboard shortcuts etc...

why? i was bored & had time. :lolflag:

---

### Post by amjjawad on 2011-09-08
kerry_s,

You used to do all these stuff on Beta release? I guess you had so much free time :D hahahaha.

Needless to say that is very interesting to know and learn but I wish I could find some time for all that. I'm focusing on other stuff but I'll keep this thread in a folder for quick access in the future.

Thanks a lot for sharing and in case I got some time, I'll let you know ;)
I mean if I need some help :P

---

