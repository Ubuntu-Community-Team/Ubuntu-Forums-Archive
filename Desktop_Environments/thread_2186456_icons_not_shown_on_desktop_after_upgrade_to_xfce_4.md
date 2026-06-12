---
title: "icons not shown on desktop after upgrade to xfce 4.11"
date: 2013-11-07
forum: Desktop Environments
---

### Post by landersohn-m on 2013-11-07
I have a few items on my desktop for program I installed which do not show icons in xfce 4.11.
the app.desktop file has a valid entry for 
icon=\path\to\the\icon.png

If I do a right click, properties, the icon shows up in the top left corner of the property dialog but on the desktop itself it just shows a default icon, not the one the icon=....
entry points to. Selecting the icon from the property dialog also does not work.

Anybody else have this problem?

---

### Post by landersohn-m on 2013-11-07
I just also noted that I can not create a new launcher using the right click - New Launcher function on the desktop

---

### Post by Toz on 2013-11-07
Hello and welcome to the forums.

Is xfdesktop running? Open a terminal window, type in the following command and post back the results:
```
 ps -ef | grep xfdesktop | grep -v grep
```
...if it doesn't show xfdesktop, you can try starting it up via:
```
xfdesktop &
```

Otherwise, there is a log file in your home directory, **~/.xsession-errors**. Can you post back the contents of that file - there might be some useful information there to help identify the problem.

---

### Post by landersohn-m on 2013-11-07
yes, xfdesktop is running. Output from ps -ef is

myuserid  14554  2813  0 10:58 ?        00:00:07 xfdesktop --display :0.0 --sm-client-id 2aa0792f7-37fa-4c22-b5d7-054d2908df6c


.xsession_errors is attached. I get a bunch of errors because I did the trick disabling access to the recently_used_files.xbel file.

---

### Post by landersohn-m on 2013-11-07
.... and I deleted the recently used files errors from the attachment

---

### Post by landersohn-m on 2013-11-07
Some more info. Below is one of the offending desktop files:


[Desktop Entry]
Encoding=UTF-8
Name=Google Earth
GenericName=3D planet viewer
Comment=Explore, search and discover the planet
Exec=/home/myuserid/google-earth/googleearth %f
Terminal=false
MultipleArgs=false
Type=Application
Icon=/home/andersl/google-earth/googleearth.png
Categories=Application;Network
MimeType=application/vnd.google-earth.kml+xml;application/vnd.google-earth.kmz;application/earthviewer;application/keyhole


the png-file in the Icon= - line does exist.

---

### Post by Toz on 2013-11-07
> sys:1: Warning: invalid cast from `XfdesktopRegularFileIcon' to `XfdesktopFileIconManager'
How did you upgrade to 4.11?

> I just also noted that I can not create a new launcher using the right click - New Launcher function on the desktop 
What happens when you try?

---

### Post by landersohn-m on 2013-11-07
Updated using synaptic from the 4.12 ppa
actually, the launchers did get created but I could see them only after I briefly changed the icon type in Destop Settings from File to something else and back.
So the launchers seem fine.

---

### Post by Toz on 2013-11-07
A couple of things to try:

1. Try reloading xfdesktop to see if that helps:
```
xfdesktop --reload
```

2. Try clearing out your sessions cache. To do so, log out and go to the first console (Ctrl+Alt+F1) and log in there (text console). Once logged in:
```
cd .cache
rm -rf sessions
```
...then go back to the gui console (Ctrl+Alt+F7), login and see if there is a difference. Post back your .xsession-errors file again at this time.

EDIT: From the [4.12 PPA]("https://launchpad.net/~xubuntu-dev/+archive/xfce-4.12"):
> You MUST enable the 4.10 PPA ([https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10)) as well.
Did you first enable the 4.10 PPA?

---

### Post by landersohn-m on 2013-11-07
no change clearing cache or reloading xfdesktop.

and yes, the 4.10 PPA is enabled, too

---

### Post by landersohn-m on 2013-11-07
here are the new session errors

---

### Post by Toz on 2013-11-07
With respect to your .xsession-errors file:
> /usr/sbin/lightdm-session: 29: /etc/profile: [[: not found
Can you post back the contents of your /usr/sbin/lightdm-session file? I'd like to see why you're getting this error.


> (xfce4-session:27791): xfce4-session-WARNING **: Unable to launch "gnome-sound-applet" (specified by autostart/Volume Control.desktop): Failed to execute child process "gnome-sound-applet" (No such file or directory)
I don't believe its responsible, but you might want to remove gnome-sound-applet from your startup to eliminate this error.


> (xfce4-session:27791): xfce4-session-WARNING **: Unable to launch "/usr/share/screenlets-manager/screenlets-daemon.py" (specified by autostart/Screenlets Daemon.desktop): Failed to execute child process "/usr/share/screenlets-manager/screenlets-daemon.py" (No such file or directory)
Ditto with this one, you might want to remove "Screenlets Daemon" from your startup apps.

---

### Post by landersohn-m on 2013-11-07
/etc/profile has the line below:
[[ -f "/etc/autopackage/paths-bash" ]] && . "/etc/autopackage/paths-bash"


lightdm-session attached

I deleted the two apps from startup that threw the error

---

### Post by landersohn-m on 2013-11-07
maybe I should add, the google earth example I sent above does have the correct icon in the Applications Menu, just not on the destop. Not sure whether that helps or is even related.

---

### Post by Toz on 2013-11-07
> **landersohn-m said:**
> /etc/profile has the line below:
[[ -f "/etc/autopackage/paths-bash" ]] && . "/etc/autopackage/paths-bash"
Is that all that's in your /etc/profile? 
Did you add that line?
What version of Ubuntu are you running?
(I'm not convinced this is the cause of your problem, I'm curious because I haven't seen this error messge before.)


What icon theme are you using? Have you tried changing the icon theme to see if it makes a difference? You might also want to try updating the icon cache:
```
gtk-update-icon-cache /path/to/theme/directory/
```
...where /path/to/theme/directory/ is the actual path to your icon theme directory.

---

### Post by Toz on 2013-11-07
> **landersohn-m said:**
> maybe I should add, the google earth example I sent above does have the correct icon in the Applications Menu, just not on the destop. Not sure whether that helps or is even related.
Sounds so much like a problem with xfdesktop, but I'm not sure what to suggest. You could try opening a bug report with the PPA, but they do state:
> Please note that these are pre-release versions, which may contain annoying bugs and/or crash. Use them at your own risk.

---

### Post by landersohn-m on 2013-11-08
Toz,
in regards to /etc/profile: no there is actually more in there:
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).


if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi


if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
	. /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi


umask 022
[[ -f "/etc/autopackage/paths-bash" ]] && . "/etc/autopackage/paths-bash"


I don't remember ever editing it by hand. the profile.d directory jut has the bash completion script and some speechd-user-port.sh script which just exports a variable


Updating the icon cash didn't do anything. Not too surprising since the icon supposed to be loaded isn't in the theme directory in the first place but a file in somewhere in my home directory.

---

### Post by Toz on 2013-11-08
> I don't remember ever editing it by hand. the profile.d directory jut has the bash completion script and some speechd-user-port.sh script which just exports a variable
It must have been put there by another package - I don't think its related to your problem now.

If you log in with another account, does the problem also happen (meaning, is it a system problem or a problem with your profile)? Might help to try to determine the scope of the issue.

---

### Post by landersohn-m on 2013-11-08
created a new account, same problem

---

### Post by landersohn-m on 2013-11-08
I am not sure it's related or not, but after installing the xubuntu desktop, my greeter gives me the option for "XFCE seswsion" or "Xubuntu session". From what I can tell there is not a bit of difference, my desktop looks the same and the icons we were talking about don't show up in either.
Is there a difference between the two sessions? different desktops running or configurations being read?

---

### Post by Toz on 2013-11-08
Then its a system problem. Don't know what else to suggest to fix it. Perhaps a bug report against the 4.12 PPA?

---

### Post by landersohn-m on 2013-11-08
Toz,
thanks very much for your help, I appreciate it

---

