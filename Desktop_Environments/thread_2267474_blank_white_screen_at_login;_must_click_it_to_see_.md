---
title: "blank white screen at login; must click it to see login box"
date: 2015-03-01
forum: Desktop Environments
---

### Post by watchpocket on 2015-03-01
I am running Ubuntu-MATE 14.04.2 with dual monitors.  Lately when I boot up I see **a blank white screen** (on  both monitors).  

Not long after this started to appear I discovered I could simply click my mouse anywhere on the screen (either screen), and the **Username/Password login box would appear **in the middle of  the screen (both screens).  

The login box appears sometimes overlaid on the white screen, and sometimes overlaid on the blue-green "Ubuntu-Mate-Cold-lightdm.jpg" image (the latter is what's supposed to happen).

*My question is: **How can I get rid of this white screen and make the background image and the login box appear immediately upon login?***

This is my /etc/lightdm directory:
```

 --> **ls -la /etc/lightdm** 
total 28
 4 drwxr-xr-x   2 root root  4096 Feb 28 01:57 ./
12 drwxr-xr-x 139 root root 12288 Mar  1 16:59 ../
 4 -rw-r--r--   1 root root  1606 Feb 23 09:09 lightdm-gtk-greeter-ubuntu-mate.conf
 4 -rw-r--r--   1 root root  2790 Feb 28 01:27 lightdm-gtk-greeter-ubuntu.conf
 0 lrwxrwxrwx   1 root root    55 Jan 19 00:25 lightdm-gtk-greeter.conf -> /etc/alternatives/lightdm-gtk-greeter-config-derivative
 4 -rw-r--r--   1 root root   452 Oct 30 14:55 users.conf

```

The contents of the four files in this directory are pasted below.

This is the ***[COLOR=#0000ff]lightdm-gtk-greeter-ubuntu-mate.conf[/COLOR]*** file:
```

  1 #
  2 # background = Background file to use, either an image path or a color (e.g. #772953)
  3 # theme-name = GTK+ theme to use
  4 # icon-theme-name = Icon theme to use
  5 # font-name = Font to use
  6 # xft-antialias = Whether to antialias Xft fonts (true or false)
  7 # xft-dpi = Resolution for Xft in dots per inch (e.g. 96)
  8 # xft-hintstyle = What degree of hinting to use (none, slight, medium, or hintfull)
  9 # xft-rgba = Type of subpixel antialiasing (none, rgb, bgr, vrgb or vbgr)
 10 # indicators = semi-colon ";" separated list of allowed indicator modules. Built-in indicators include "~a11y", "~language", "~session", "~power". Unity indicators can be repre    ____sented by short name (e.g. "sound", "power"), service file name, or absolute path
 11 # show-clock (true or false)
 12 # clock-format = strftime-format string, e.g. %H:%M
 13 # keyboard = command to launch on-screen keyboard
 14 # position = main window position: x y
 15 # default-user-image = Image used as default user icon, path or #icon-name
 16 # screensaver-timeout = Timeout (in seconds) until the screen blanks when the greeter is called as lockscreen
 17 #-
 18 [greeter]
 19 background=/usr/share/backgrounds/ubuntu-mate-utopic/Ubuntu-Mate-Cold-lightdm.jpg
 20 theme-name=Ambiant-MATE
 21 icon-theme-name=LoginIcons
 22 font-name=Ubuntu 11
 23 xft-antialias=true
 24 xft-dpi=96
 25 xft-hintstyle=hintslight
 26 xft-rgba=rgb
 27 indicators=~host;~spacer;~clock;~spacer;~session;~a11y;~language;~power
 28 keyboard=onboard
 29 reader=orca
 30 position = 50%,center 50%,center
 31 default-user-image = #avatar-default
 32 screensaver-timeout = 60
 33 a11y-states=contrast;font;keyboard;reader
 34 user-background = false
 35 clock-format = %a %d %b, %H:%M

```

And this is the ***[COLOR=#0000ff]lightdm-gtk-greeter-ubuntu.conf[/COLOR]*** file:
```

  1 # LightDM GTK+ Configuration
  2 # Available configuration options listed below.
  3 #
  4 # Appearance:
  5 #  theme-name = GTK+ theme to use
  6 #  icon-theme-name = Icon theme to use
  7 #  background = Background file to use, either an image path or a color (e.g. #772953)
  8 #  user-background = false|true ("true" by default")  Display user background (if available)
  9 #  transition-duration = Length of time (in milliseconds) to transition between background images ("500" by default)
 10 #  transition-type = ease-in-out|linear|none  ("ease-in-out" by default)
 11 #
 12 # Fonts:
 13 #  font-name = Font to use
 14 #  xft-antialias = false|true  Whether to antialias Xft fonts
 15 #  xft-dpi = Resolution for Xft in dots per inch (e.g. 96)
 16 #  xft-hintstyle = none|slight|medium|hintfull  What degree of hinting to use
 17 #  xft-rgba = none|rgb|bgr|vrgb|vbgr  Type of subpixel antialiasing
 18 #
 19 # Login window:
 20 #  active-monitor = Monitor to display greeter window (name or number). Use #cursor value to display greeter at monitor with cursor.
 21 #  position = x y ("50% 50%" by default)  Login window position
 22 #  default-user-image = Image used as default user icon, path or #icon-name
 23 #  hide-user-image = false|true ("false" by default)
 24 #
 25 # Panel:
 26 #  panel-position = top|bottom ("top" by default)
 27 #  show-clock = false|true ("false" by default)
 28 #  clock-format = strftime-format string, e.g. %H:%M
 29 #  show-indicators = semi-colon ";" separated list of allowed indicator modules. Built-in indicators include "~a11y", "~language", "~session", "~power". Unity indicators can be    ____ represented by short name (e.g. "sound", "power"), service file name, or absolute path
 30 #
 31 # Accessibility:
 32 #  a11y-states = states of accessibility features: "name" - save state on exit, "-name" - disabled at start (default value for unlisted), "+name" - enabled at start. Allowed na    ____mes: contrast, font, keyboard, reader.
 33 #  keyboard = command to launch on-screen keyboard (e.g. "onboard")
 34 #  keyboard-position = x y[;width height] ("50%,center -0;50% 25%" by default)
 35 #  reader = command to launch screen reader (e.g. "orca")
 36 #
 37 # Security:
 38 #  allow-debugging = false|true ("false" by default)
 39 #  screensaver-timeout = Timeout (in seconds) until the screen blanks when the greeter is called as lockscreen
 40 #
 41 # Template for per-monitor configuration:
 42 #  [monitor: name]
 43 #  background = overrides default value
 44 #  user-background = overrides default value
 45 #  laptop = false|true ("false" by default) Marks monitor as laptop display
 46 #-
 47 [greeter]
 48 background=/usr/share/backgrounds/ubuntu-mate-utopic/Ubuntu-Mate-Cold-lightdm.jpg
 49 theme-name=Ambiance
 50 icon-theme-name=LoginIcons
 51 font-name=Ubuntu 11
 52 xft-antialias=true
 53 xft-dpi=96
 54 xft-hintstyle=slight
 55 xft-rgba=rgb
 56 show-indicators=~host;~spacer;~session;~language;~a11y;~clock;~power;
 57 show-clock=true
 58 clock-format=%d %b, %H:%M

```

Here is the ***[COLOR=#0000ff]/etc/alternatives/lightdm-gtk-greeter-config-derivative[/COLOR]*** file
```

  1 #
  2 # background = Background file to use, either an image path or a color (e.g. #772953)
  3 # theme-name = GTK+ theme to use
  4 # icon-theme-name = Icon theme to use
  5 # font-name = Font to use
  6 # xft-antialias = Whether to antialias Xft fonts (true or false)
  7 # xft-dpi = Resolution for Xft in dots per inch (e.g. 96)
  8 # xft-hintstyle = What degree of hinting to use (none, slight, medium, or hintfull)
  9 # xft-rgba = Type of subpixel antialiasing (none, rgb, bgr, vrgb or vbgr)
 10 # indicators = semi-colon ";" separated list of allowed indicator modules. Built-in indicators include "~a11y", "~language", "~session", "~power". Unity indicators can be repre    ____sented by short name (e.g. "sound", "power"), service file name, or absolute path
 11 # show-clock (true or false)
 12 # clock-format = strftime-format string, e.g. %H:%M
 13 # keyboard = command to launch on-screen keyboard
 14 # position = main window position: x y
 15 # default-user-image = Image used as default user icon, path or #icon-name
 16 # screensaver-timeout = Timeout (in seconds) until the screen blanks when the greeter is called as lockscreen
 17 #-
 18 [greeter]
 19 background=/usr/share/backgrounds/ubuntu-mate-utopic/Ubuntu-Mate-Cold-lightdm.jpg
 20 theme-name=Ambiant-MATE
 21 icon-theme-name=LoginIcons
 22 font-name=Ubuntu 11
 23 xft-antialias=true
 24 xft-dpi=96
 25 xft-hintstyle=hintslight
 26 xft-rgba=rgb
 27 indicators=~host;~spacer;~clock;~spacer;~session;~a11y;~language;~power
 28 keyboard=onboard
 29 reader=orca
 30 position = 50%,center 50%,center
 31 default-user-image = #avatar-default
 32 screensaver-timeout = 60
 33 a11y-states=contrast;font;keyboard;reader
 34 user-background = false
 35 clock-format = %a %d %b, %H:%M

```

And, finally, here's the [COLOR=#0000ff]***users.conf***[/COLOR] file:
```
 
  1 #
  2 # User accounts configuration
  3 #
  4 # NOTE: If you have AccountsService installed on your system, then LightDM will
  5 # use this instead and these settings will be ignored
  6 #
  7 # minimum-uid = Minimum UID required to be shown in greeter
  8 # hidden-users = Users that are not shown to the user
  9 # hidden-shells = Shells that indicate a user cannot login
 10 #
 11 [UserList]
 12 minimum-uid=500
 13 hidden-users=nobody nobody4 noaccess
 14 hidden-shells=/bin/false /usr/sbin/nologin

```

Thank you to anyone who chooses to respond.

---

### Post by Portaro on 2015-03-01
Take a look on the line

49 theme-name=Ambiance

I think that you need the convergence with the ubuntu mate config - 
20 theme-name=Ambiant-MATE

Maybe is the theme with mistake apply on login theme.

You can use LightDM GTK+ Greeter Settings to set lightdm properties (appearance) - [http://www.lffl.org/2014/10/lightdm-greeter-settings-personalizzare-display-manager-xubuntu-lubuntu.html](http://www.lffl.org/2014/10/lightdm-greeter-settings-personalizzare-display-manager-xubuntu-lubuntu.html)

---

### Post by watchpocket on 2015-03-01
Thanks for your response.  That did not fix the problem, but thank you for making me aware of the ***LightDM GTK+ Greeter Settings*** program.

---

### Post by ihoe3fze on 2015-03-02
Try to update greeter from this ppa:
[https://code.launchpad.net/~kalgasnik/+archive/ubuntu/lightdm-gtk-greeter-post-2.0.0](https://code.launchpad.net/~kalgasnik/+archive/ubuntu/lightdm-gtk-greeter-post-2.0.0)
or use this link to get .deb file:
[https://code.launchpad.net/~kalgasnik/+archive/ubuntu/lightdm-gtk-greeter-post-2.0.0/+sourcepub/4809554/+listing-archive-extra](https://code.launchpad.net/~kalgasnik/+archive/ubuntu/lightdm-gtk-greeter-post-2.0.0/+sourcepub/4809554/+listing-archive-extra)

Are you using monitors in mirrored mode (by default)?

---

### Post by watchpocket on 2015-03-02
***YES !!!***  Upgrading the greeter totally fixed the problem.  

Also the greeter no longer mirrors in both monitors (and, no, I am not in mirrored-mode).  And the greeter is way better than the old one, very nice the way it comes on.  Thanks for your advice, I hadn't known there was an updated version of the greeter.  (Of course it's only dated yesterday.)  Issue solved!

---

### Post by ihoe3fze on 2015-03-02
Ok, good to hear it. I don't know when official version will be updated.

Can you provide more info?
1. Add this option to /etc/lightdm/lightdm-gtk-greeter.conf:
allow-debugging=true
(or use settings application - "misc." tab)
2. Go to login screen
3. Post /var/log/lightdm/x-*-greeter.log (the newest one) here

---

### Post by watchpocket on 2015-03-02
Yes but that more info will have to wait til late tonight or tomorrow, have to leave the house right now, thanks again.

---

### Post by watchpocket on 2015-03-02
> **ihoe3fze said:**
> 
2. Go to login screen


So: Just to be clear, I take it I should go to the login screen and *actually log in*, of course, yes?  And then post the newest log.

---

### Post by ihoe3fze on 2015-03-02
It doesn't matter, really. All I want to see - section where greeter detects displays configuration.

---

### Post by watchpocket on 2015-03-03
I will post log info late Thursday night / early Friday morning.

---

### Post by watchpocket on 2015-03-06
> **ihoe3fze said:**
> 
(or use settings application - "misc." tab)


"Debugging Mode" is checked in the misc tab (I enabled it in the config file), but there's a  small white exclamation mark inside a red circle beside "Debugging Mode" that, when you mouse over it, says:

"GtkInspector is not available on your system
Gtk version: (3, 10, 8) < (3, 14, 0)"

In any event:

> 
3. Post /var/log/lightdm/x-*-greeter.log (the newest one) here

This is the output of /var/log/lightdm/x-0-greeter.log:
```

Activating service name='org.a11y.atspi.Registry'
Successfully activated service 'org.a11y.atspi.Registry'
[+0.00s] DEBUG: unity-greeter.vala:496: Starting unity-greeter 14.04.11 UID=113 LANG=en_US.UTF-8
[+0.00s] DEBUG: unity-greeter.vala:499: Setting cursor
[+0.03s] DEBUG: unity-greeter.vala:513: Loading command line options
[+0.03s] DEBUG: unity-greeter.vala:541: Setting GTK+ settings
[+0.11s] DEBUG: unity-greeter.vala:564: Creating Unity Greeter
[+0.11s] DEBUG: unity-greeter.vala:57: Creating background surface
[+0.13s] DEBUG: Connecting to display manager...
[+0.13s] DEBUG: Wrote 18 bytes to daemon
[+0.13s] DEBUG: Read 8 bytes from daemon
[+0.13s] DEBUG: Read 150 bytes from daemon
[+0.13s] DEBUG: Connected version=1.10.4 default-session=ubuntu show-manual-login=false hide-users=false has-guest-account=true show-remote-login=true
[+0.45s] DEBUG: menubar.vala:336: LANG=en_US.UTF-8 LANGUAGE=(null)
[+1.17s] DEBUG: menubar.vala:368: LANG=en_US.UTF-8 LANGUAGE=(null)
[+1.17s] DEBUG: Loading users from org.freedesktop.Accounts
[+1.17s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+1.18s] DEBUG: user-list.vala:1030: Adding/updating user rj (rj)
[+1.18s] DEBUG: Loading sessions from org.freedesktop.DisplayManager
[+1.19s] DEBUG: user-list.vala:1012: Adding guest account entry
[+1.23s] DEBUG: Loaded session /usr/share/xsessions/mate.desktop (MATE, This session logs you into MATE)
[+1.23s] DEBUG: Loaded session /usr/share/xsessions/ubuntu.desktop (Ubuntu, This session logs you into Ubuntu)
[+1.23s] DEBUG: Starting authentication for user rj...
[+1.23s] DEBUG: Wrote 18 bytes to daemon
[+1.23s] DEBUG: main-window.vala:185: Screen is 1920x1200 pixels
[+1.23s] DEBUG: main-window.vala:193: Monitor 0 is 1920x1200 pixels at 0,0
[+1.23s] DEBUG: main-window.vala:193: Monitor 1 is 1920x1200 pixels at 0,0
[+1.23s] DEBUG: unity-greeter.vala:567: Showing greeter
[+1.23s] DEBUG: unity-greeter.vala:252: Showing main window
[+1.24s] DEBUG: background.vala:483: Regenerating backgrounds
[+1.24s] DEBUG: background.vala:68: Making background /usr/share/backgrounds/warty-final-ubuntu.png at 1920x1200
[+1.24s] DEBUG: unity-greeter.vala:610: Starting main loop
[+1.24s] DEBUG: Read 8 bytes from daemon
[+1.24s] DEBUG: Read 32 bytes from daemon
[+1.24s] DEBUG: Prompt user with 1 message(s)
[+1.25s] DEBUG: background.vala:159: Error loading background: Failed to open file '/usr/share/backgrounds/warty-final-ubuntu.png': No such file or directory
[+1.48s] DEBUG: background.vala:68: Making background /home/rj/Pictures/Dark-brown-fine-wood-texture.jpg at 1920x1200
[+1.48s] DEBUG: settings-daemon.vala:75: Acquired org.gnome.SessionManager
[+1.48s] DEBUG: settings-daemon.vala:102: Acquired org.gnome.ScreenSaver
[+1.48s] DEBUG: settings-daemon.vala:159: All bus names acquired, starting unity-settings-daemon
[+1.69s] DEBUG: unity-greeter.vala:235: starting system-ready sound
nm-applet-Message: using fallback from indicator to GtkStatusIcon
[+2.98s] DEBUG: background.vala:121: Render of background /usr/share/backgrounds/warty-final-ubuntu.png complete
[+2.98s] DEBUG: background.vala:138: images[0] was null for /usr/share/backgrounds/warty-final-ubuntu.png
[+3.00s] DEBUG: Connected to Application Indicator Service.
[+3.06s] DEBUG: main-window.vala:185: Screen is 3840x1200 pixels
[+3.06s] DEBUG: main-window.vala:193: Monitor 0 is 1920x1200 pixels at 0,0
[+3.06s] DEBUG: main-window.vala:193: Monitor 1 is 1920x1200 pixels at 1920,0
nm-applet-Message: moving back from GtkStatusIcon to indicator
[+3.06s] DEBUG: menubar.vala:538: Adding indicator object 0x22f7940 at position 0

** (unity-settings-daemon:1421): WARNING **: Unable to register client: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such method 'RegisterClient'
[+3.15s] DEBUG: menubar.vala:538: Adding indicator object 0x22f7680 at position 0
[+3.24s] DEBUG: menubar.vala:538: Adding indicator object 0x22f73c0 at position 2
[+3.33s] DEBUG: menubar.vala:538: Adding indicator object 0x22f7ec0 at position 2
[+3.39s] DEBUG: Request current apps
[+3.40s] DEBUG: Building new application entry: :1.6  with icon: nm-no-connection at position 0
[+3.47s] DEBUG: menubar.vala:538: Adding indicator object 0x2465b00 at position 4
[+3.50s] DEBUG: background.vala:121: Render of background /home/rj/Pictures/Dark-brown-fine-wood-texture.jpg complete
[+3.52s] DEBUG: background.vala:483: Regenerating backgrounds
[+3.52s] DEBUG: background.vala:68: Making background /usr/share/backgrounds/warty-final-ubuntu.png at 1920x1200
[+3.52s] DEBUG: background.vala:68: Making background /home/rj/Pictures/Dark-brown-fine-wood-texture.jpg at 1920x1200
[+3.52s] DEBUG: background.vala:159: Error loading background: Failed to open file '/usr/share/backgrounds/warty-final-ubuntu.png': No such file or directory
[+3.53s] DEBUG: background.vala:121: Render of background /usr/share/backgrounds/warty-final-ubuntu.png complete
[+3.53s] DEBUG: background.vala:138: images[0] was null for /usr/share/backgrounds/warty-final-ubuntu.png
[+3.64s] DEBUG: background.vala:121: Render of background /home/rj/Pictures/Dark-brown-fine-wood-texture.jpg complete
[+21.81s] DEBUG: Providing response to display manager
[+21.81s] DEBUG: Wrote 25 bytes to daemon
[+24.09s] DEBUG: Read 8 bytes from daemon
[+24.09s] DEBUG: Read 14 bytes from daemon
[+24.09s] DEBUG: Authentication complete for user rj with return code 7
[+24.09s] DEBUG: Starting authentication for user rj...
[+24.09s] DEBUG: Wrote 18 bytes to daemon
[+24.09s] DEBUG: Read 8 bytes from daemon
[+24.09s] DEBUG: Read 32 bytes from daemon
[+24.09s] DEBUG: Prompt user with 1 message(s)
[+27.58s] DEBUG: Providing response to display manager
[+27.58s] DEBUG: Wrote 26 bytes to daemon
[+27.60s] DEBUG: Read 8 bytes from daemon
[+27.60s] DEBUG: Read 14 bytes from daemon
[+27.60s] DEBUG: Authentication complete for user rj with return code 0
[+27.60s] DEBUG: Starting session mate
[+27.60s] DEBUG: Wrote 16 bytes to daemon
[+27.60s] DEBUG: Read 8 bytes from daemon
[+27.60s] DEBUG: Read 4 bytes from daemon
[+27.60s] DEBUG: unity-greeter.vala:605: Got a SIGTERM
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.

** (unity-settings-daemon:1421): WARNING **: Name taken or bus went away - shutting down
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
[+27.62s] DEBUG: unity-greeter.vala:613: Cleaning up
[+27.62s] DEBUG: unity-greeter.vala:621: Upstart exited with return value 0
[+27.62s] DEBUG: unity-greeter.vala:633: AT-SPI exited with return value 0
[+27.62s] DEBUG: unity-greeter.vala:639: Exiting

(unity-settings-daemon:1421): dconf-WARNING **: failed to commit changes to dconf: The connection is closed
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
init: indicator-bluetooth main process (1441) killed by TERM signal
init: indicator-power main process (1442) killed by TERM signal
init: indicator-datetime main process (1444) killed by TERM signal
init: indicator-session main process (1460) killed by TERM signal
init: indicator-application main process (1528) terminated with status 1

```

Many thanks.

---

### Post by ihoe3fze on 2015-03-06
[QUOTE=watchpocket]
This is the output of /var/log/lightdm/x-0-greeter.log
```

[+0.11s] DEBUG: unity-greeter.vala:564: Creating **Unity Greeter**

```[/QUOTE]
It's not a gtk greeter log :).
Anyway, everything works as expected so log file is not really needed.

---

### Post by watchpocket on 2015-03-07
> **ihoe3fze said:**
> It's not a gtk greeter log :).
Anyway, everything works as expected so log file is not really needed.

I'd prefer to have the gtk greeter active, since, being on Ubuntu-MATE, I don't use unity at all.  I'll be looking for how to make that happen.

Also, ***should*** GtkInspector be on my system?  I couldn't find it in Synaptic. 

I'm a bit curious as to why I've got that warning in the Greeter-settings Misc tab.

---

### Post by ihoe3fze on 2015-03-08
> **watchpocket said:**
> I'd prefer to have the gtk greter active, since, being on Ubuntu-MATE, I don't use unity at all.  I'll be looking for how to make that happen.
Also, ***should*** GtkInspector be on my system?  I couldn't find it in Synaptic. 
I'm a bit curious as to why I've got that warning in the Greeter-settings Misc tab.
GtkInspector is the **built-in** debugging tool for gtk applications - [it's a part of gtk toolkit since 3.14]("https://wiki.gnome.org/Projects/GTK%2B/Inspector"). Version of gtk in 14.04 - 3.10. So, it's ok for your system.
This warning is confusing a bit, maybe it will be removed in next version.

---

### Post by zika on 2015-03-08
> **ihoe3fze said:**
> Try to update greeter from this ppa:
[https://code.launchpad.net/~kalgasnik/+archive/ubuntu/lightdm-gtk-greeter-post-2.0.0](https://code.launchpad.net/~kalgasnik/+archive/ubuntu/lightdm-gtk-greeter-post-2.0.0)
or use this link to get .deb file:
[https://code.launchpad.net/~kalgasnik/+archive/ubuntu/lightdm-gtk-greeter-post-2.0.0/+sourcepub/4809554/+listing-archive-extra](https://code.launchpad.net/~kalgasnik/+archive/ubuntu/lightdm-gtk-greeter-post-2.0.0/+sourcepub/4809554/+listing-archive-extra)

Are you using monitors in mirrored mode (by default)?Can You elaborate where does automatic build of LightDM available from that PPA come from?

---

### Post by ihoe3fze on 2015-03-09
> **zika said:**
> Can You elaborate where does automatic build of LightDM available from that PPA come from?

Please, rephrase the  question. Probably, my english is not so well to correctly understand the question.

---

### Post by watchpocket on 2015-03-09
> **zika said:**
> Can You elaborate where does automatic build of LightDM available from that PPA come from?

You should ask the person who created the PPA ("Andrew P.").  It apparently was uploaded to the PPA by Andrew P. on 2015-03-01.

Sign into launchpad and then go to [URL="https://launchpad.net/~kalgasnik"]https://launchpad.net/~kalgasnik 
[/URL]
Then get the e-mail address there of the maintainer of that PPA, and ask him.

---

### Post by divirtual on 2015-03-12
Thanks for reporting and solving this problem.  I had the same white screen on a laptop plus second monitor with Ubuntu 14.04, plus the Mate Desktop installed.  I am installing the updated LightDM greeter.

---

### Post by watchpocket on 2015-03-12
Do you get the same warning in the Greeter-settings Misc tab?

---

