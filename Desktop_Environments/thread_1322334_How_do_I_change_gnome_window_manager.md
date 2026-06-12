---
title: "How do I change gnome window manager?"
date: 2009-11-10
forum: Desktop Environments
---

### Post by valtert on 2009-11-10
I would like to use Fluxbox ALONG WITH Gnome. Yes, I want to switch Gnome window manager from metacity to fluxbox.

I've searched for this but nothing I read has worked.

Some said to use system > preferences > sessions, but there's no such a menu in my system.

So I read this other way to do it somewhere else, and tried myself:
I grep'd for metacity in my home directory and found this in two files:
```

.gconf/desktop/gnome/session/required_components/%gconf.xml:        <stringvalue>metacity</stringvalue>
.gconf/desktop/gnome/applications/window_manager/%gconf.xml:        <stringvalue>/usr/bin/metacity</stringvalue>
.gconf/desktop/gnome/applications/window_manager/%gconf.xml:        <stringvalue>/usr/bin/metacity</stringvalue>

```I changed these files to 'fluxbox' but then gnome will start up with no windows manager (no titlebar at all, no way to move windows...). If then I run fluxbox from a terminal, everything works ok, but it seems sometimes gnome and fluxbox dispute control over the mouse pointer, some flash plugins on firefox will miss clicks, and some other odd stuff happens.

I was a Slackware user and I used Fluxbox alone with no desktop manager, so I will hack up anything you tell me, no problem to edit files and stuff...

I just won't keep on using Fluxbox apart from Gnome because gnome has all this automount and network manager and all integrated, i'm tired of typing commands every time i have to interact with hardware.

Maybe i should try gnome forums, but i hope someone here can help me please!

Ubuntu Karmik Koala 9.10
Gnome 2.28.1
Fluxbox 1.1.1-2
(fresh ubuntu install)

---

### Post by unamanic on 2009-11-10
It's not flux, but if you install openbox, it will give you the option for gnome/openbox at login.

---

### Post by valtert on 2009-11-10
The following link has some instructions which seem deprecated:
[http://ubuntuforums.org/showthread.php?t=63734](http://ubuntuforums.org/showthread.php?t=63734)

The mentioned file desktop.session could not be located in my system.
Indeed, i found no '*.session' file anywhere in the disk.

Maybe should i give up and do this? (use fluxbox alone and run gnome-panel)
[http://ubuntuforums.org/showthread.php?t=147398](http://ubuntuforums.org/showthread.php?t=147398)

I would like to have all gnome daemon running as well
(those from System > Preferences > Startup Applications)
any clue?

---

### Post by valtert on 2009-11-10
Thank you unamanic, i'll try to install openbox and hack over that =)

**update:**
ok i'm getting bored.
Installed openbox and the option Gnome/openbox appeared on login screen BUT...
...login won't complete if i choose this option (screen blinks then go back to login screen)

I know nothing about gnome, where it's files reside, config, logs...

---

### Post by unamanic on 2009-11-10
gnome keeps it's user configs in sub directories in ~/.gconf and ~/.gconfd as well as ~/.gnome2 and ~/.gnome2_private  I haven't had it kick me back to the login screen like that before with gnome/openbox (but I've only used it to test) Typically I'll use stright gnome or KDE, unless I'm doing something that needs every CPU cycle I can spare (cinelerra) then I go to straight openbox.

---

### Post by valtert on 2009-11-10
Thanks again unamanic =)

I've found out this:
```
cat `which openbox-gnome-session`
#!/bin/sh

if test -n "$1"; then
    echo "Syntax: openbox-gnome-session"
    echo
    echo "See the openbox-gnome-session(1) manpage for help."
  exit
fi

# Run GNOME with Openbox as its window manager
export WINDOW_MANAGER="/usr/bin/openbox"
exec gnome-session --choose-session=openbox-session "$@"

```

Now i just need to find out which file was modified in order to add "gnome/openbox" option running "openbox-gnome-session" and add an option to do it with fluxbox =D

I'll update it when i manage to get it working properly.

---

### Post by valtert on 2009-11-11
So, why can't i just ctrl+alt+backspace??

I've added this to xorg but no success:

```
$cat /etc/X11/xorg.conf | grep -A1 -B1 Zap
Section "ServerFlags"
        Option         "DontZap" "False"
EndSection
```
**update****:**
ok, got it, i need to enable it from a gnome menu...
yeah almost giving up gnome, it's too intrusive!
i'd rather edit a file than struggle looking for things in menus...
but gnome config files are so messed up and keeps changing from a version to another!
that's why openbox won't work and i can't get fluxbox to work with gnome as well...
i've found out some more things, i'll post here soon

---

### Post by valtert on 2009-11-11
Ok, i spent all the day messing around with gnome files and now it's working, but i don't know how.

It seems it's just some happy coincidence, as when it wasn't working the "gnome/fluxbox" session i created was starting gnome with no window manager, and now there's fluxbox in the "startup applications".

It works, but i guess it's not the way it was supposed to be done.

For now i'll just go get a life. When i have the time i plan to install ubuntu under a virtual machine and try to reproduce the settings and get it documented.

**edit:**
on ~/.xsession-errors i get this message:
```
x-session-manager[13291]: WARNING: Unable to find provider 'fluxbox' of required component 'windowmanager'
```In my system x-session-manager is a symlink to gnome-session

**There's a but report telling gnome-session latest version lacks a --choose-session option**
[https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/272418](https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/272418)

Somebody has any idea on how can i make gnome-session aware of fluxbox?

---

### Post by valtert on 2009-11-12
Adding a fluxbox.desktop file to /usr/share/applications solved this error.

/usr/share/applications/fluxbox.desktop contents:
```
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=Fluxbox
Exec=startfluxbox
NoDisplay=true
# name of loadable control center module
X-GNOME-WMSettingsModule=fluxbox
# name we put on the WM spec check window
X-GNOME-WMName=Fluxbox
# back compat only 
X-GnomeWMSettingsLibrary=fluxbox
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=fluxbox
X-GNOME-Bugzilla-Component=general
X-GNOME-Autostart-Phase=WindowManager
X-GNOME-Provides=windowmanager
X-GNOME-Autostart-Notify=true
X-Ubuntu-Gettext-Domain=fluxbox

```

**edit:**
if someone know about a better value for any parameter please tell me, i've just copied metacity ones...

---

### Post by JohnE1 on 2009-11-13
> **valtert said:**
> Thank you unamanic, i'll try to install openbox and hack over that =)

**update:**
ok i'm getting bored.
Installed openbox and the option Gnome/openbox appeared on login screen BUT...
...login won't complete if i choose this option (screen blinks then go back to login screen)

I know nothing about gnome, where it's files reside, config, logs...

[B]GNOME Display Manager Reference Manual
[[COLOR="Blue"]http://library.gnome.org/users/gdm/2.14/index.html.en[/COLOR]]("http://library.gnome.org/users/gdm/2.14/index.html.en")
[/B]

---

### Post by hafbaked on 2009-11-13
based on an old thread, and this one, I got fluxbox working with gnome in ubuntu 9.10 fairly smoothly (to me, anyways). 


1) Install fluxbox
   [I]sudo apt-get install fluxbox
[/I]2) Edit gconf file to switch from compiz to fluxbox
   *sudo gedit *~/.gconf/desktop/gnome/applications/window_manager/\%gconf.xml
   replace "compiz" with "fluxbox"
3) (Not sure if this is actually required)  Created a fluxbox.desktop file
   *sudo cp /usr/share/applications/compiz.desktop* [I]/usr/share/applications/compiz.desktop
   sudo gedit [/I][I]/usr/share/applications/fluxbox.desktop
[/I]   change all references from "compiz" to "fluxbox"

Optional

1) To use fluxbox backgrounds, and allow the right-click fluxbox menu's, you must disable nautilus from drawing the desktop. 

   [I]sudo gconf-editor
   [/I]Click apps -> nautilus -> preferences
   Ensure "Show_Desktop" is not checked. 

2) If you want to use the fluxbox "slit" instead of a gnome toolbar. 
    
    right-click gnome-toolar, and click delete. 

3) If you want a similar "Human" theme for fluxbox, it was created by someone else and is available here: 

[http://ubuntuforums.org/showthread.php?t=317273](http://ubuntuforums.org/showthread.php?t=317273)

   Just extract the file into ~/.fluxbox/styles and then select it from the right-click fluxbox menu under "Styles"

4) When I did this, the Network Manager applet, Power Manager applet, and Volume Manager applet stopped appearing on my gnome menu bar.  So I added them to the fluxbox slit
   
   [I]sudo gedit ~/.fluxbox/startup
   [/I]paste in the following lines somewhere ABOVE the "exec fluxbox" line

  gnome-keyring-daemon &
  nm-applet &
  gnome-volume-control-applet &
  gnome-power-manager &

  I'm not sure if this is actually required, my knowledge of gnome is limited. 

This was my first attempt to integrate these two.  Usually I simply install fluxbox and use it standalone.  Its possible some further steps are required I'm not aware of.  For me, this works perfectly, as it gives me the extra power of fluxbox grouping, and allows me to use the fluxbox right-click menu, and my old fluxbox keybindings.

---

### Post by valtert on 2009-11-13
Thank you JohnE1, that definitely is going to help a lot!

Though it's working ok for me, when i get it working the "right way" i'm gonna write a little how-to for the community (when i get the time to, just you wait!)

=)

---

### Post by valtert on 2009-11-13
hafbaked posted simultaneously to my last post hehe

Thanks a lot hafbaked, good to know my scrambled info has been useful to you!

So here it is, the how-to =)

I belive that among all of the random tweaks i made, the ones hafbacked described are the necessary ones to make it happen.

And yeah, i was longing to disable nautilus desktop, i had to get i killed every login, thanks again hafbaked =D

The problem with network manager and volume and other applets.. i had this problem myself, but for now i've got a panel with a "Notification Area" and gnome start all this automatically and put the icon there.

This forum is great, thanks everyone!

---

