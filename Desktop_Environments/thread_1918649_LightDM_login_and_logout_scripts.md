---
title: "LightDM login and logout scripts"
date: 2012-02-01
forum: Desktop Environments
---

### Post by ivan15 on 2012-02-01
Hello,

Please, is there any way to setup a login and logout script in LightDM, like there was in GDM by /etc/gdm/PreSession/Default and /etc/gdm/PostSession/Default

Thanks,
Ivan

---

### Post by Krytarik on 2012-02-01
This should do it, the bold-marked options, add them to your "/etc/lightdm/lightdm.conf":
```
#
# General configuration
#
# start-default-seat = True to always start one seat if none are defined in the configuration
# greeter-user = User to run greeter as
# minimum-display-number = Minimum display number to use for X servers
# minimum-vt = First VT to run displays on
# user-authority-in-system-dir = True if session authority should be in the system location
# guest-account-script = Script to be run to setup guest account
# log-directory = Directory to log information to
# run-directory = Directory to put running state in
# cache-directory = Directory to cache to
# xsessions-directory = Directory to find X sessions
# xgreeters-directory = Directory to find X greeters
#
[LightDM]
#start-default-seat=true
#greeter-user=lightdm
#minimum-display-number=0
#minimum-vt=7
#user-authority-in-system-dir=false
#guest-account-script=guest-account
#log-directory=/var/log/lightdm
#run-directory=/var/run/lightdm
#cache-directory=/var/cache/lightdm
#xsessions-directory=/usr/share/xsessions
#xgreeters-directory=/usr/share/xgreeters

#
# Seat defaults
#
# xserver-command = X server command to run
# xserver-layout = Layout to pass to X server
# xserver-config = Config file to pass to X server
# xserver-allow-tcp = True if TCP/IP connections are allowed to this X server
# xdmcp-manager = XDMCP manager to connect to (implies xserver-allow-tcp=true)
# xdmcp-port = XDMCP UDP/IP port to communicate on
# xdmcp-key = Authentication key to use for XDM-AUTHENTICATION-1 (stored in keys.conf)
# greeter-session = Session to load for greeter
# greeter-hide-users = True to hide the user list
# user-session = Session to load for users
# allow-guest = True if guest login is allowed
# guest-session = Session to load for guests (overrides user-session)
# session-wrapper = Wrapper script to run session with
# display-setup-script = Script to run when starting a greeter session (runs as root)
# greeter-setup-script = Script to run when starting a greeter (runs as root)
# [COLOR=DarkGreen]**session-setup-script = Script to run when starting a user session (runs as root)**[/COLOR]
# [COLOR=Red]**session-cleanup-script = Script to run when quitting a user session (runs as root)**[/COLOR]
# autologin-guest = True to log in as guest by default
# autologin-user = User to log in with by default (overrides autologin-guest)
# autologin-user-timeout = Number of seconds to wait before loading default user
# autologin-session = Session to load for automatic login (overrides user-session)
# exit-on-failure = True if the daemon should exit if this seat fails
#
[SeatDefaults]
#xserver-command=X
#xserver-layout=
#xserver-config=
#xserver-allow-tcp=false
#xdmcp-manager=
#xdmcp-port=177
#xdmcp-key=
#greeter-session=example-gtk-gnome
#greeter-hide-users=false
#user-session=default
#allow-guest=true
#guest-session=UNIMPLEMENTED
#session-wrapper=lightdm-session
#display-setup-script=
#greeter-setup-script=
#[COLOR=DarkGreen]**session-setup-script=**[/COLOR]
#[COLOR=Red]**session-cleanup-script=**[/COLOR]
#autologin-guest=false
#autologin-user=
#autologin-user-timeout=0
#autologin-session=UNIMPLEMENTED
#exit-on-failure=false

#
# Seat configuration
#
# Each seat must start with "Seat:".
# Uses settings from [SeatDefaults], any of these can be overriden by setting them in this section.
#
#[Seat:0]

#
# XDMCP Server configuration
#
# enabled = True if XDMCP connections should be allowed
# port = UDP/IP port to listen for connections on
# key = Authentication key to use for XDM-AUTHENTICATION-1 or blank to not use authentication (stored in keys.conf)
#
# The authentication key is a 56 bit DES key specified in hex as 0xnnnnnnnnnnnnnn.  Alternatively
# it can be a word and the first 7 characters are used as the key.
#
[XDMCPServer]
#enabled=false
#port=177
#key=

#
# VNC Server configuration
#
# enabled = True if VNC connections should be allowed
# port = TCP/IP port to listen for connections on
#
[VNCServer]
#enabled=false
#port=5900
#width=1024
#height=768
#depth=8
```
Source: "/usr/share/doc/lightdm/lightdm.conf"

Regards.

---

### Post by ivan15 on 2012-02-02
Yes, that worked well :D Thank you :)

---

### Post by Paddy Landau on 2012-11-26
I have this same problem.

However:

The [FONT=Lucida Console]session-cleanup-script[/FONT] does indeed run, but it runs *after* logging out instead of beforehand.

As I have an encrypted folder, this means that the script is unable to do what it is meant to do on my files.

How do I resolve that problem, and run the clean-up script *before* the actual logout, or at least before the decrypted folder is dismounted? Is there a run-level or some other mechanism?

---

### Post by johnklemen on 2013-04-06
Unfortunately this blog is the best documentation of the session-cleanup-script-option, that I found. That's why I'm posting my solution here.

I wanted a cleanup-possibility on a by-user-basis... this is how i did it:

in /etc/lightdm/lightdm.conf:
```

user-session=ubuntu
greeter-session=unity-greeter
session-cleanup-script=/usr/local/bin/lightdm_cleanup.sh

```

in /usr/local/bin/lightdm_cleanup.sh:
```

#! /bin/sh
if [ -e $HOME/.lightdm_cleanup.sh ]; then su -c "$HOME/.lightdm_cleanup.sh" $USER; fi

```

now every user can create his own .lightdm_cleanup.

---

### Post by Paddy Landau on 2013-04-07
> **johnklemen said:**
> I wanted a cleanup-possibility on a by-user-basis... this is how i did it…
Gosh, I had forgotten about this thread! There is [another thread]("http://ubuntuforums.org/showthread.php?t=1969822") where I have done exactly as you have done (see [post #9 of that thread]("http://ubuntuforums.org/showthread.php?t=1969822&p=12318858&viewfull=1#post12318858")).

However, there still remains a problem ([post #20]("http://ubuntuforums.org/showthread.php?t=1969822&p=12547499&viewfull=1#post12547499")):

The script runs when I log out by restarting the machine, but it does  not run when I merely log out without restarting. So, restarting will run the script, but logging out and then  either logging back in or restarting will not run the script.

I have yet to find a solution to that problem.

---

### Post by GameX2 on 2013-04-29
For some reason, I never got this to work. :(

Here's my lightdm.conf file:

```
[SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter
display-setup-script=/etc/lightdm/lightdmxrandr.sh
allow-guest=false
session-setup-script=/home/Scripts/wallpaper_logon.sh
session-cleanup-script=/home/Scripts/wallpaper_logoff.sh
```

I have an XML file as background, which LightDM does not display (Instead, I can choose a custom background for LightDM!).  However, during login, the wallpaper does not fade, and I would love to.

When I log in, LightDM would be supposed to run this script (Yes, my scripts are executables):

```
#!/bin/sh
sleep 4
gsettings set org.gnome.desktop.background picture-options 'stretched'
gsettings set org.gnome.desktop.background picture-uri file:///usr/share/backgrounds/friendship_v3/background-1.xml
```

Nothing happen.  Running the script manually, or adding it to startup applications work, however...

And at logoff, I want to change it back to LightDM background:

```
#!/bin/sh
gsettings set org.gnome.desktop.background picture-uri file:///usr/share/backgrounds/LoginWallpaper4.jpg
sleep 2
gnome-session-quit --no-prompt
```

gnome-session-quit --no-prompt actually logoff properly, if I run the script manually.

This is really confusing.  Where are my wallpapers supposed to be located?  In my Home, or in /Etc/Lightdm ?  Same question for the login and logoff scripts ?

Thank you!

---

### Post by Paddy Landau on 2013-04-30
GameX2, I'm not entirely sure about your situation. I have two questions:

[LIST=1]
[*]Which version of Ubuntu are you using? 
[*]Why do you have the [FONT=lucida console]sleep[/FONT] commands in your scripts? Try doing this again without the sleep. 
[/LIST]

---

### Post by GameX2 on 2013-04-30
> **Paddy Landau said:**
> GameX2, I'm not entirely sure about your situation. I have two questions:

[LIST=1]
[*]Which version of Ubuntu are you using? 
[*]Why do you have the [FONT=lucida console]sleep[/FONT] commands in your scripts? Try doing this again without the sleep. 
[/LIST]


Thanks for your reply.

I now use Ubuntu 13.04, but I also have Ubuntu 12.04 installed on the same computer.  I can't get it to work on both versions.

I can put my script "LoginWallpaper.sh" in my startup applications, and it's working.  The reason why I have to put the sleep command, is that otherwise, I login, and the background immediately change (Right now, without any delay.  I don't see the background fading).  I want to avoid such a rapid change.  My goal: I have a custom LightDM background - when I login, I still see the LightDM background, then 3-4 seconds later, the background fade to my XML.

If I run the script Wallpaper_Logoff.sh manually, which set my Desktop background identical to the LightDM background and log me out automatically, this work.  But I can't make the script run everytime I logoff/reboot/shutdown.

A workaround would probably be to run this script, only at login:

```

gsettings set org.gnome.desktop.background picture-uri file:///usr/share/backgrounds/LoginWallpaper4.jpg
sleep 4
gsettings set org.gnome.desktop.background picture-options 'stretched'
gsettings set org.gnome.desktop.background picture-uri file:///usr/share/backgrounds/friendship_v3/background-1.xml
```

At login, I assume LightDM would immediately change my desktop background to the current LightDM background (This sentence sound weird..  Well, my current Desktop background would be identical to the LightDM background).  Then 4 seconds later, when the Desktop will appear, the background should fade to the other one.

Can I even run the command " gsettings set org.gnome.desktop.background picture " from LightDM at all ?  I've tried so many times, and never got it working.  Even tried changing ownership of the backgrounds to root or "LightDM", no luck.


Thank you very much.

---

### Post by Paddy Landau on 2013-05-01
> **GameX2 said:**
> Can I even run the command " gsettings set org.gnome.desktop.background picture " from LightDM at all?
That's a good question. Remember that LightDM runs as root, as I recall, so you'd have to run gsettings as yourself:
```
su "${USER}" --command gsettings[FONT=arial]&#8230;[/FONT]
```
Beware if you have other users on the same computer, as the code will affect them. You can put in a condition (replace *gamex2* with your user name):
```
if [[ "${USER}" == '*gamex2*' ]]
then
        su "${USER}" --command gsettings[FONT=arial]&#8230;[/FONT]
fi
```
This is not something that I have tried, particularly XML wallpaper (I didn't realise that it was possible), so I cannot be sure that this will work.

---

