---
title: "I think I have added kubuntu to ubuntu - not sure"
date: 2019-05-02
forum: Desktop Environments
---

### Post by jgw on 2019-05-02
I think I have added kubuntu desktop to ubuntu.  I am not sure.  When I reboot it says its kbuntu.  Settings/details just says ubuntu.  Here is a couple command results:
```
greg@movies:~$ ls /usr/bin/*session
/usr/bin/dbus-run-session  /usr/bin/gnome-session-custom-session
/usr/bin/gnome-session
greg@movies:~$ ls -l /usr/share/xsessions/
total 24
-rw-r--r-- 1 root root 7625 Mar 19  2018 gnome-classic.desktop
-rw-r--r-- 1 root root  138 Nov  4  2012 kodi.desktop
-rw-r--r-- 1 root root 2353 Oct  4  2018 plasma.desktop
-rw-r--r-- 1 root root  323 May  2  2018 ubuntu-communitheme-snap.desktop
-rw-r--r-- 1 root root  247 May  2  2018 ubuntu.desktop
greg@movies:~$ 
```

I am trying to change the fonts in Krusader - menu bar, toolbars, etc.  I have done the kde system settings font changes which changed nothing I could see.  As far as I can tell I am using the plasma.desktop, but not sure.

Thank you.........

-Computer-
```
Processor		: AMD A8-7650K Radeon R7, 10 Compute Cores 4C+6G
Memory			: 15338MB (3888MB used)
Machine Type		: Desktop
Operating System	: Ubuntu 18.04.2 LTS
User Name		: greg (greg)
Date/Time		: Thu 02 May 2019 02:34:08 PM PDT
```

-Display-
```
Resolution		: 3840x2160 pixels
OpenGL Renderer		: AMD KAVERI (DRM 2.50.0, 4.15.0-48-generic, LLVM 7.0.0)
X11 Vendor		: The X.Org Foundation
```

---

### Post by TheFu on 2019-05-02
Before you login, click on the "gear", select the DE you want, then login.
I would do this under a completely new userid to avoid conflicting config files from causing bad things to happen.  Run like that using a different userid for a few days to be certain all is working.  You can access all the gnome apps or kde apps from either DE.

BTW, whenever posting command output, please use 'code tags' so that the output lines up like it does in the terminal.  This is in the AdvReply or Advance edit button.

---

### Post by jgw on 2019-05-03
Thank you for the reply.  I keep forgetting the code tag thing and apologize.  I will try to do better!

All that being said does anybody know how I can get control of the fonts for menu bars, tool bars, etc?

---

### Post by #&amp;thj^% on 2019-05-03
????>>'System Settings'
Click on the 'Appearance' icon, or press Tab to enter the main window, and then use the arrow keys to navigate to 'Appearance' and then press Enter.

In the window that opens, click on the 'Fonts' icon, or press Tab until the pane on the left is highlighted, then use the down arrow key to move to 'Fonts'

---

### Post by jgw on 2019-05-04
Thank you for the responses.

I have uploaded 2 files.  The first is my Krusader screen and the second is the fonts screen from system settings.  I have found that no matter how I set the size it makes no difference.  I suspect I am in the wrong system settings.

Thoughts?

---

### Post by #&amp;thj^% on 2019-05-04
Yep wrong place, you can or "should" be able to call it directly from the terminal:
```
systemsettings5 &
```

---

### Post by jgw on 2019-05-04
Thank for for the reply.

I did as suggested - it took me right back to the wrong one.  I did it in a terminal and got:
```
greg@movies:~$ systemsettings5 &
[1] 8711
greg@movies:~$ WARNING: viewBackgroundColor is deprecated, use backgroundColor with colorSet: Theme.View instead
WARNING: viewBackgroundColor is deprecated, use backgroundColor with colorSet: Theme.View instead
KActivities: Database connection:  "kactivities_db_resources_139778832185344_readonly" 
    query_only:          QVariant(qlonglong, 1) 
    journal_mode:        QVariant(QString, "wal") 
    wal_autocheckpoint:  QVariant(qlonglong, 100) 
    synchronous:         QVariant(qlonglong, 0)
Nothing to load - the client id is empty
Nothing to load - the client id is empty
checking permissions of  "/usr/share/color-schemes/Breeze.colors"
KActivitiesStats( 0x5588f542e160 ) ResultModelPrivate::onResultScoreUpdated  result added: "kcm:colors.desktop" score: 0 last: 1557002313 first: 1557002313
KActivitiesStats( 0x5588f542e160 ) ResultModelPrivate::onResultScoreUpdated  result added: "kcm:fonts.desktop" score: 3.87883 last: 1557002313 first: 1556827215
Service  org.kde.fontinst  not registered, starting "/usr/lib/x86_64-linux-gnu/libexec/kauth/fontinst"
1557002345 Connecting to session bus
1557002345 Failed to register service!
KActivitiesStats( 0x5588f542e160 ) ResultModelPrivate::onResultScoreUpdated  result added: "kcm:fontinst.desktop" score: 1 last: 1557002345 first: 1556827912
Closing SQL connection:  "kactivities_db_resources_139778832185344_readonly"
greg@movies:~$
``` 

I also pressed super f2 for "system settings" and got KDE system settings (the one I was using and got sent to by systemsettings5 and ubuntu system settings

---

### Post by #&amp;thj^% on 2019-05-04
> **jgw said:**
> Thank for for the reply.

I did as suggested - it took me right back to the wrong one.  I did it in a terminal and got:
greg@movies:~$ systemsettings5 &
[1] 8711
greg@movies:~$ WARNING: viewBackgroundColor is deprecated, use backgroundColor with colorSet: Theme.View instead
WARNING: viewBackgroundColor is deprecated, use backgroundColor with colorSet: Theme.View instead
KActivities: Database connection:  "kactivities_db_resources_139778832185344_readonly" 
    query_only:          QVariant(qlonglong, 1) 
    journal_mode:        QVariant(QString, "wal") 
    wal_autocheckpoint:  QVariant(qlonglong, 100) 
    synchronous:         QVariant(qlonglong, 0)
Nothing to load - the client id is empty
Nothing to load - the client id is empty
checking permissions of  "/usr/share/color-schemes/Breeze.colors"
KActivitiesStats( 0x5588f542e160 ) ResultModelPrivate::onResultScoreUpdated  result added: "kcm:colors.desktop" score: 0 last: 1557002313 first: 1557002313
KActivitiesStats( 0x5588f542e160 ) ResultModelPrivate::onResultScoreUpdated  result added: "kcm:fonts.desktop" score: 3.87883 last: 1557002313 first: 1556827215
Service  org.kde.fontinst  not registered, starting "/usr/lib/x86_64-linux-gnu/libexec/kauth/fontinst"
1557002345 Connecting to session bus
1557002345 Failed to register service!
KActivitiesStats( 0x5588f542e160 ) ResultModelPrivate::onResultScoreUpdated  result added: "kcm:fontinst.desktop" score: 1 last: 1557002345 first: 1556827912
Closing SQL connection:  "kactivities_db_resources_139778832185344_readonly"
greg@movies:~$ 

I also pressed super f2 for "system settings" and got KDE system settings (the one I was using and got sent to by systemsettings5 and ubuntu system settings

Ha the old multiple DE syndrome eh? Ya that is sometimes problem-matic,  I always try to warn users of more than one DE environment installed to be prepared to roll-up their sleeves, and prepare to tinker with the settings and configs etc. 
Things just try to grab other stuff related to other DE settings.
I'm not sure how to advise you further, with out knowing how you installed KDE, ie: command used **or **all you installed by hand.:)
And sometimes the changes when made in Gnome will carry to the KDE (Plasma) session. Like Fonts. Give it a try if have not already.

---

### Post by jgw on 2019-05-04
Thank you.....

I keep forgetting the code thing - sorry............

Anyway, to install kbuntu I used [https://vitux.com/how-to-install-the-kde-plasma-desktop-on-ubuntu-18-04-lts/](https://vitux.com/how-to-install-the-kde-plasma-desktop-on-ubuntu-18-04-lts/)

That one also took quite a long time to complete...........

---

### Post by #&amp;thj^% on 2019-05-04
Did you use this:(Gosh I hope not)
```
sudo apt install sddm
```
And if you did, only if you did re-run:
```
sudo dpkg-reconfigure sddm
```
and choose **"gdm3"** it's the less worse of two evils here. LOL
NOTE:
> A display manager is the component of your Operating system responsible for launching your display server and the login session. This is the reason it is sometimes called the login manager. The layout of the screen that you see while entering your username and password(the greeter), your login session and user authorization are some of the tasks that the display manager performs. A few common types of default display managers are gdm, gdm3, lightdm, kdm, and sddm, etc.

---

### Post by jgw on 2019-05-04
Thanks again!

Yep, seems I did that.  To see I did the sudo dpkg-reconfigure sddm thing (and choose gdm).  I have no idea what I might have chosen previously.  Anyway, after i did that nothing happened as far as I can tell.  I re-read the instructions and it said that sddm needed to be pressed to get to kdm, ie. "The sddm display manager is the default one for KDE Plasma desktop. Hit Enter for Ok."

What happens if I press "sddm"?  I remember that I did login to the kde login screen once.  I am not sure what happened but I have only seen that specific login once and I am sure I have rebooted several times since then.

---

### Post by #&amp;thj^% on 2019-05-05
I'm kind of vague on what your saying, was you able to login with gdm3 and plasma?
I actually got rid of both "gdm3" and "sddm" and I just stick with "lightdm"
```
loginctl show-session $XDG_SESSION_ID
Id=2
User=1000
Name=me
Timestamp=Sun 2019-05-05 05:52:32 MDT
TimestampMonotonic=44535400
VTNr=7
Seat=seat0
Display=:0
Remote=no
**Service=lightdm**
**Desktop=plasma**
Scope=session-2.scope
Leader=1593
Audit=2
Type=x11
Class=user
Active=yes
State=active
IdleHint=no
IdleSinceHint=0
IdleSinceHintMonotonic=0
LockedHint=no

```
So i guess maybe you want to keep the KDE Plasma session then?

---

### Post by jgw on 2019-05-05
Sorry took so long - thanks for the reply.......

when I run sudo dpkg-reconfigure sddm I have 2 options; gdm3 & sddm

Then I ran the thing you did and got:

```

greg@movies:~$ loginctl show-session $XDG_SESSION_ID
Id=1
User=1000
Name=greg
Timestamp=Sat 2019-05-04 16:32:55 PDT
TimestampMonotonic=62072343
VTNr=1
Seat=seat0
TTY=tty1
Remote=no
Service=gdm-autologin
Scope=session-1.scope
Leader=1337
Audit=1
Type=x11
Class=user
Active=yes
State=active
IdleHint=no
IdleSinceHint=0
IdleSinceHintMonotonic=0
LockedHint=no

```

I suspect I am going to have to select sddm to get anyplace close as there is, I think, nowhere to get to kde from here.  (that is what the reconfigure sddm says but I you said I shouldn't do that so I am resisting <g>)

---

### Post by #&amp;thj^% on 2019-05-06
Your options are usually not configured per>>DM, but in a common location for "all" DMs
The usual place is /usr/share/xsessions, where .desktop files will be present for each login option. 
```

cd /usr/share/xsessions
ls
cinnamon.desktop    gnome-xorg.desktop  kodi.desktop  plasma.desktop
cinnamon2d.desktop  gnome.desktop       mate.desktop  xfce.desktop
```
I have never figured out if you have reached "A" KDE-Plasma session yet??
I use only 'lightdm' on all my mixed Linux installs ie:Arch Gentoo Debian/Ubuntu and Slack>>> and control the various DE sessions from that. (However that dose not mean you have to)
I don't even have them installed:
```
pacman -Qi sddm
error: package 'sddm' was not found

me on Mon May 06 at 10:22 AM in ~ branch: (HEAD) 
>> pacman -Qi gdm3
error: package 'gdm3' was not found

```

**EDIT:** And as TheFu suggested>>"I would do this under a completely new userid/name to avoid conflicting config files from causing bad things to happen."
just seen this as installed: "ubuntu-communitheme-snap.desktop">>> I had problems with more than one session installed with that package.

---

### Post by jgw on 2019-05-06
```

greg@movies:/usr/share/xsessions$ ls
gnome-classic.desktop  plasma.desktop                    ubuntu.desktop
kodi.desktop           ubuntu-communitheme-snap.desktop

```

I continue to wonder what would happen if I ran sudo dpkg-reconfigure sddm and choose sddm
apparently, if I would do that I would first have to goto /etc/init-d/ and edit the scripts in gdm3 and sddm.  I was going to post those for you to peer at but found that they were actually folders so I gave up on that.  (they were also executable)

I did pacman -Qi sddm which got me a small box with pacman in it.  It was too small to play
I did pacman -Qi sddm which got me the same small box with pacman in it.  It too was too small to play

"have never figured out if you have reached "A" KDE-Plasma session yet??"
I am not sure what that means.  When I installed KDE-Plasma I did log in, once - never saw that screen again.  (I am pretty clueless about this stuff)  All I want to do is try and change some font sizes ,for menu bar and tool bars, in a couple of programs.  One is Krusader (main one) and the other was the system settings although that would make no difference as I have no idea what good that one is (I sent a picture of that one).

---

### Post by again? on 2019-05-07
> Service=gdm-autologin
See if you can turn off auto-login in settings or 
just try logging out to see if that takes you to the login screen.

Don't use kde so can't tell you exactly where it is or if you need to be using sddm.
Don't see any harm in switching to sddm.

Reboot and at the greeter choose your session.
When using gdm3, at the login screen you have to select the user then a cog icon will show to select session.
In sddm you should see a session option somewhere on the panel at the login screen.

[COLOR="#FF0000"]Edit:[/COLOR] I just installed plasma-desktop in my test install of bionic, keeping gdm3.
Logged in to plasma session.
Changing size of titlebar fonts worked.
[ATTACH=CONFIG]283207[/ATTACH]

As others have said though, different desktop environments don't coexist too nicely nowadays and maybe you stumbled into an incomplete plasma desktop install.
If it was me and I was curious about kde I would treat your current install as a test with a mind to reinstalling.
Then in future use the terminal or synaptic to install packages from other DE's to check what else is installed.
Quite often you can use the **--no-install-recommends** option to get a minimal amount of extra packages.
If in doubt, I keep a note of installed packages shown in the terminal under "The following NEW packages will be installed:",  for removal later if necessary.

---

### Post by jgw on 2019-05-07
Thanks for the reply

Now I have to edit /etc/init.d/gdm3 & sddm as per:
 &#9474; Multiple display managers can run simultaneously if they are configured   &#9474; 
 &#9474; to manage different servers; to achieve this, configure the display       &#9474; 
 &#9474; managers accordingly, edit each of their init scripts in /etc/init.d,     &#9474; 
 &#9474; and disable the check for a default display manager.  

Here are snippits for /etc/init.d/gdm3 and sddm:

```

# To start gdm even if it is not the default display manager, change
# HEED_DEFAULT_DISPLAY_MANAGER to "false"
HEED_DEFAULT_DISPLAY_MANAGER=false
DEFAULT_DISPLAY_MANAGER_FILE=/etc/X11/default-display-manager


# To start sddm even if it is not the default display manager, change
#HEED_DEFAULT_DISPLAY_MANAGER to "false"
HEED_DEFAULT_DISPLAY_MANAGER=false
# Also overridable from command line like:
# HEED_DEFAULT_DISPLAY_MANAGER=false /etc/init.d/lightdm start
[ -z "$HEED_DEFAULT_DISPLAY_MANAGER" ] && HEED_DEFAULT_DISPLAY_MANAGER=false

DEFAULT_DISPLAY_MANAGER_FILE=/etc/X11/default-display-manager

DESC="Init script for Simple Desktop Display Manager"
DAEMON=/usr/bin/sddm
START_ARGS='--background --make-pidfile'

#
# Function that starts the daemon/service
#
do_start_override()
{
	if grep -wqs text /proc/cmdline; then
		log_warning_msg "Not starting Simple Desktop Display Manager ($NAME); found 'text' in kernel commandline."
	elif [ "$HEED_DEFAULT_DISPLAY_MANAGER" = "true" ] &&
	     [ -e $DEFAULT_DISPLAY_MANAGER_FILE ] &&
	     [ "$(cat $DEFAULT_DISPLAY_MANAGER_FILE)" != "$DAEMON" ]; then
		log_action_msg "Not starting Simple Desktop Display Manager ($NAME); it is not the default display manager."
	else
		[ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME"
		# Wait for plymouth if running
		[ -x /bin/plymouth ] && /bin/plymouth quit
		call do_start_cmd
		case "$?" in
		  0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		  2)   [ "$VERBOSE" != no ] && log_end_msg 1 ;;
		esac
	fi
}

:

```

I included the rest of the sddm script for the heck of it.


Now, in theory I can run sudo dpkg-reconfigure sddm and see what happens.   Did it, choose sddm.  Now greg@movies:~$ loginctl show-session $XDG_SESSION_ID

```

Id=1
User=1000
Name=greg
Timestamp=Sun 2019-05-05 15:11:39 PDT
TimestampMonotonic=52513919
VTNr=1
Seat=seat0
TTY=tty1
Remote=no
Service=gdm-autologin
Scope=session-1.scope
Leader=1367
Audit=1
Type=x11
Class=user
Active=yes
State=active
IdleHint=no
IdleSinceHint=0
IdleSinceHintMonotonic=0
LockedHint=no
greg@movies:~$ 

```

Now I will reboot.

---

### Post by jgw on 2019-05-07
I have now rebooted.  When booting it seemed to be very slow.  I hit the shift key a couple of times.  The  the sddm login appeared.  I logged in and did:

```

greg@movies:~$ loginctl show-session $XDG_SESSION_ID
Id=3
User=1000
Name=greg
Timestamp=Tue 2019-05-07 09:11:33 PDT
TimestampMonotonic=100980537
VTNr=1
Seat=seat0
Display=:0
Remote=no
Service=sddm
Desktop=GNOME-Classic:GNOME:
Scope=session-3.scope
Leader=2551
Audit=3
Type=x11
Class=user
Active=yes
State=active
IdleHint=no
IdleSinceHint=0
IdleSinceHintMonotonic=0
LockedHint=no


```

I then opened KDE system settings.   I was unable to change the menu bar or any other bars  (they all remained teeny)  Oh, I did press apply <g>

I think I have to figure out how to change my desktop from gnome to something else (sddm?)  I have no idea.  

Thoughts?

---

### Post by again? on 2019-05-08
> Service=sddm
Desktop=GNOME-Classic:GNOME:
The reason you can't change the titlebar fonts with kde settings is your not even running plasmashell.
You are using the gnome-classic desktop.

Two options:
[LIST=1]
[*]Change title bar fonts with gnome-tweaks or
[*]logout and choose the "Plasma" session whereby you can use the kde settings.
Not knowing exactly what you installed you may not have a plasma session.
[/LIST]
[ATTACH=CONFIG]283219[/ATTACH]

Also now that you have switched to the sddm display manager you can turn off autologin in kde settings.
No need to recklessly edit config files.
[ATTACH=CONFIG]283218[/ATTACH]

FYI: from** [https://www.ghacks.net/2008/12/09/get-to-know-linux-desktop-environment-vs-window-manager/](https://www.ghacks.net/2008/12/09/get-to-know-linux-desktop-environment-vs-window-manager/)**
> 
[LIST]
[*]X Windows - This is the foundation that allows for graphic elements to be drawn on the display. 
X Windows builds the primitive framework that allows moving of windows, interactions with keyboard and mouse, and draws windows. 
This is required for any graphical desktop.

[*]Window Manager: The Window Manager is the piece of the puzzle that controls the placement and appearance of windows. 
Window Managers include: Enlightenment, Afterstep, FVWM, Fluxbox, IceWM, etc. 
Requires X Windows but not a desktop environment.

[*]Desktop Environment: This is where it begins to get a little fuzzy for some. A Desktop Environment includes a Window Manager but builds upon it. 
The Desktop Environment typically is a far more fully integrated system than a Window Manager. 
Requires both X Windows and a Window Manager.
[/LIST]

Basically the the title bar fonts are controlled by the window manager.
The desktop session you are logging into determines what window manager is being used, so you have to use the appropriate settings application.

---

### Post by jgw on 2019-05-08
Thank you for the reply.  

Strangely enough I did log in with the plasma screen as depicted in your picture.  None of this really makes any sense to me.  I am not on that machine right now but I will be later and I will do as suggested, log out, and then log in again.  I also can't figure out how to stop the auto login.  What I did, when I logged in with plasma was hit the shift key a couple of times and that login screen popped up!  I have yet to logout and login so I will make a run  at that.  I also have no idea how to get to that user manager - system settings but I will give it a try.

Thanks again - I have never messed with this stuff before so I continue to struggle, hopefully I will figure it out.

---

### Post by jgw on 2019-05-08
I have now logged out and logged back in (also got rid of the auto login).  In BOTH cases I got:
```

greg@movies:~$ loginctl show-session $XDG_SESSION_ID
Id=3
User=1000
Name=greg
Timestamp=Wed 2019-05-08 16:08:41 PDT
TimestampMonotonic=170068745
VTNr=1
Seat=seat0
Display=:0
Remote=no
Service=sddm
Desktop=GNOME-Classic:GNOME:
Scope=session-3.scope
Leader=2512
Audit=3
Type=x11
Class=user
Active=yes
State=active
IdleHint=no
IdleSinceHint=0
IdleSinceHintMonotonic=0
LockedHint=no
greg@movies:~$ 

```

Then I did:
```

greg@movies:/usr/share/xsessions$ ls
gnome-classic.desktop  plasma.desktop                    ubuntu.desktop
kodi.desktop           ubuntu-communitheme-snap.desktop

```

Since I logged in with the plasma screen (I think) and , when rebooting it said "Kubuntu" instead of "ubuntu" It thinks its not loading gnome desktop?  The simple fact is that it is.  This even gets better!  Tweaks, for instance, no longer does anything.  I really need to get to the plasma shell but have no idea how to get there as I thought I would be there by logging in with that screen.

I should add that I think I used to have a 'dock' option in my system settings but not now.  I do, however, have a bar on the bottom of the screen which holds currently open programs.  I also have dash to dock (gnome) also running.  

I should also add that my top bar is now running with high contrast icons and I can no longer control them.

Mysteries do, obviously, abound............

---

### Post by again? on 2019-05-09
Did you try creating a new user account as TheFu suggested and logging into the plasma session?
Does your normal Ubuntu session work where you should be able to change title bar fonts with gnome-tweaks? (Gnome classic isn't the default Ubuntu session)

What is the goal here?
Do you want the plasma desktop or do you just want to use krusader in the default Ubuntu desktop environment?

---

### Post by jgw on 2019-05-09
Thank you for the reply..............

I thought I had replied but that went up in smoke so I will try again.

I did not try creating a new user account as I could never figure out how to do that.
I don't thing I have a nor al ubuntu session anymore and gnome tweaks no longer works.

I am running with a 4k system with a resolution of 3840 x 2160 on a 65" tv.  I use this system for watching downloaded movies.
My problem began when nautilus get strange.  I would not, for instance, change the mouse icon when I hovered over column boundaries but I could guess where that was to move columns around.  Then I thought I would look at other file managers and those, like Krusader, had problems with the program fonts.  I could control the data display fonts but not menu or other bars intrinsic to the program.   When running with a 4k desktop fonts get very strange very quick.  I was then told to try the plasma screen and the system configurator for that.  So I added kde with [https://vitux.com/how-to-install-the-kde-plasma-desktop-on-ubuntu-18-04-lts/](https://vitux.com/how-to-install-the-kde-plasma-desktop-on-ubuntu-18-04-lts/).   Then I tried the kde configurator also had font problems but that made no difference anyway.  

I could go on and on but the simple fact is that this adventure has led to a genuine mess.  Right now I am told that I have a gnome desktop with a SDDM service.  what I have been trying to do is install a plasma desktop.  Its kinda interesting.  If I reboot, for instance, the "Ubuntu" name is now "Kubuntu".  I stopped the auto login and now get to login to a box that is so small I can't even really read it.  I have been told that this is the KDE login screen.  

Since I have spent more than a week on this I am now to a point where I think my best solution is to re-install the operating system (probably kubuntu this time).  The question becomes should I install it completely wiping everything out or try to install saving the existing programs.  Given my mess I should probably go with a complete install.  I have my data on another drive so that is safe.  I will, however, have to reinstall kodi, couchpotato and sonarr (and probably a bunch of other stuff).  I have done this a number of times, over the years, but resist because of the time it will take.  On the other hand I suspect I have spent twice as much time not doing that as I would have spent doing it.

Anyway, I appreciate everybody's help but my suspicion is that its time to stop bothering everybody and just get on with it. 

Thoughts?

---

### Post by #&amp;thj^% on 2019-05-10
Honestly you are no bother, but this is just something "I" just can't figure out. :(
I can't even re-produce it..

---

