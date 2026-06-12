---
title: "desktop always reset to default"
date: 2012-11-15
forum: Desktop Environments
---

### Post by rebornishard on 2012-11-15
[http://ubuntuforums.org/attachment.php?attachmentid=227200&stc=1&d=1352964295](http://ubuntuforums.org/attachment.php?attachmentid=227200&stc=1&d=1352964295)
This launcher on the left side on my desktop always change into default state, any item i put on it will be reset after i restart / shutdown my laptop :(
is there anything i can do to repair it, i reinstall ubuntu desktop but it still reset :(
thank you

this is message i got :
> GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.


---

### Post by stinkeye on 2012-11-15
Your not logged into the guest session are you?
In terminal...
```
echo $DESKTOP_SESSION
```

When do you get the error message?
What Ubuntu release?
Fresh install or upgrade?

I've seen bugs in Natty were it says to install some packages.
In terminal...
```
sudo apt-get install dconf-tools libdconf0 libdconf-dbus-1-0
```

log out and in again

---

### Post by rebornishard on 2012-11-15
> **stinkeye said:**
> Your not logged into the guest session are you?
In terminal...
```
echo $DESKTOP_SESSION
```

When do you get the error message?
What Ubuntu release?
Fresh install or upgrade?

I've seen bugs in Natty were it says to install some packages.
In terminal...
```
sudo apt-get install dconf-tools libdconf0 libdconf-dbus-1-0
```

log out and in again
Thank you stinkeye

```
echo $DESKTOP_SESSION
```
give me blank space

When do you get the error message? compiz ccsm crash, and whatever i did i always set to default, how to view dump for error message ?
What Ubuntu release? 12.04
Fresh install or upgrade? fresh install , try to upgrade to 12.10 but ubuntu ask me to not did it, then i agree and forced to partial upgrade, from there all of this happen :(

```
sudo apt-get install dconf-tools libdconf0 libdconf-dbus-1-0
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdconf-dbus-1-0 is already the newest version.
libdconf0 is already the newest version.
dconf-tools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.

> ~$ unity --reset
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Initializing composite options...done
Initializing opengl options...done
Initializing imgjpeg options...done
Initializing decor options...done
Initializing gnomecompat options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing resize options...done
Initializing wall options...done
Initializing snap options...done
Initializing grid options...done
Initializing move options...done
Initializing mag options...done
Initializing place options...done
Initializing animation options...done
Initializing unitymtgrabhandles options...done
Initializing fade options...done
Initializing workarounds options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing session options...done
Initializing scale options...done
Initializing ezoom options...done
Initializing opacify options...done
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.

(compiz:5370): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.
WARN  2012-11-15 16:43:55 unity.favorites FavoriteStoreGSettings.cpp:139 Unable to load GDesktopAppInfo for 'ubiquity-gtkui.desktop'
WARN  2012-11-15 16:43:55 unity.favorites FavoriteStoreGSettings.cpp:139 Unable to load GDesktopAppInfo for 'ubuntuone-installer.desktop'
ERROR 2012-11-15 16:43:55 unity.launcher.trashlaunchericon TrashLauncherIcon.cpp:62 Could not create file monitor for trash uri: Operation not supported
Initializing unityshell options...done
WARN  2012-11-15 16:43:56 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x1baa380

WARN  2012-11-15 16:43:56 unity <unknown>:0 Failed to fetch path: No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0x1baa380
WARN  2012-11-15 16:43:56 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x1baa380

Setting Update "launcher_hide_mode"
Setting Update "icon_size"
Setting Update "edge_responsiveness"
WARN  2012-11-15 16:43:56 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-11-15 16:43:56 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-11-15 16:43:56 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-impress.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-11-15 16:44:24 unity.iconloader IconLoader.cpp:438 Unable to load icon . GThemedIcon (null) application-x-sharedlib gnome-mime-application-x-sharedlib application-x-generic at size 64
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.

(google-chrome:6119): Gtk-CRITICAL **: IA__gtk_settings_set_long_property: assertion `GTK_SETTINGS (settings)' failed

(google-chrome:6119): Gtk-CRITICAL **: IA__gtk_settings_set_long_property: assertion `GTK_SETTINGS (settings)' failed

(google-chrome:6119): Gtk-CRITICAL **: IA__gtk_settings_set_long_property: assertion `GTK_SETTINGS (settings)' failed

(google-chrome:6119): Gtk-CRITICAL **: IA__gtk_settings_set_long_property: assertion `GTK_SETTINGS (settings)' failed

(google-chrome:6119): Gtk-CRITICAL **: IA__gtk_settings_set_string_property: assertion `GTK_SETTINGS (settings)' failed

(google-chrome:6119): Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(google-chrome:6119): Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(google-chrome:6119): Gtk-CRITICAL **: IA__gtk_icon_theme_prepend_search_path: assertion `GTK_IS_ICON_THEME (icon_theme)' failed

(google-chrome:6119): Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(google-chrome:6119): Gtk-CRITICAL **: IA__gtk_icon_theme_prepend_search_path: assertion `GTK_IS_ICON_THEME (icon_theme)' failed

(google-chrome:6119): Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(google-chrome:6119): Gtk-CRITICAL **: IA__gtk_icon_theme_prepend_search_path: assertion `GTK_IS_ICON_THEME (icon_theme)' failed

(google-chrome:6119): Gtk-CRITICAL **: IA__gtk_settings_set_string_property: assertion `GTK_SETTINGS (settings)' failed

(google-chrome:6119): Gtk-CRITICAL **: IA__gtk_settings_set_string_property: assertion `GTK_SETTINGS (settings)' failed

(google-chrome:6119): Gtk-CRITICAL **: IA__gtk_settings_set_string_property: assertion `GTK_SETTINGS (settings)' failed
WARN  2012-11-15 16:44:30 unity.libindicator <unknown>:0 Desktop file '/usr/local/share/applications/google-chrome.desktop' is using a deprecated format for its actions that will be dropped soon.
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.

(exe:6519): Gtk-CRITICAL **: IA__gtk_settings_set_long_property: assertion `GTK_SETTINGS (settings)' failed

(exe:6519): Gtk-CRITICAL **: IA__gtk_settings_set_long_property: assertion `GTK_SETTINGS (settings)' failed

(exe:6519): Gtk-CRITICAL **: IA__gtk_settings_set_long_property: assertion `GTK_SETTINGS (settings)' failed

(exe:6519): Gtk-CRITICAL **: IA__gtk_settings_set_long_property: assertion `GTK_SETTINGS (settings)' failed

(exe:6519): Gtk-CRITICAL **: IA__gtk_settings_set_string_property: assertion `GTK_SETTINGS (settings)' failed

(exe:6519): Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(exe:6519): Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(exe:6519): Gtk-CRITICAL **: IA__gtk_icon_theme_prepend_search_path: assertion `GTK_IS_ICON_THEME (icon_theme)' failed

(exe:6519): Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(exe:6519): Gtk-CRITICAL **: IA__gtk_icon_theme_prepend_search_path: assertion `GTK_IS_ICON_THEME (icon_theme)' failed

(exe:6519): Gtk-CRITICAL **: IA__gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(exe:6519): Gtk-CRITICAL **: IA__gtk_icon_theme_prepend_search_path: assertion `GTK_IS_ICON_THEME (icon_theme)' failed

(exe:6519): Gtk-CRITICAL **: IA__gtk_settings_set_string_property: assertion `GTK_SETTINGS (settings)' failed

(exe:6519): Gtk-CRITICAL **: IA__gtk_settings_set_string_property: assertion `GTK_SETTINGS (settings)' failed

(exe:6519): Gtk-CRITICAL **: IA__gtk_settings_set_string_property: assertion `GTK_SETTINGS (settings)' failed
WARN  2012-11-15 16:53:12 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application833323233

ERROR 2012-11-15 16:53:13 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:13 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:13 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:13 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:13 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:13 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:53:14 unity.glib-gobject <unknown>:0 g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
WARN  2012-11-15 16:53:57 unity.libindicator <unknown>:0 Desktop file '/home/pau/Desktop/google-chrome.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-11-15 16:57:27 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x1bcf100

ERROR 2012-11-15 16:57:29 unity <unknown>:0 bamf_view_get_children: assertion `BAMF_IS_VIEW (view)' failed
ERROR 2012-11-15 16:57:29 unity.glib-gobject <unknown>:0 g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed


---

### Post by stinkeye on 2012-11-15
Try these commands one at a time to attempt to fix broken packages and update system....
```
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by rebornishard on 2012-11-15
> **stinkeye said:**
> Try these commands one at a time to attempt to fix broken packages and update system....
```
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```


> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

the error still there sir :(

i remember this happens after i try kde on my ubuntu

---

### Post by NikTh on 2012-11-15
Hi , 
please give the results 
```
lsb_release -rcd ; uname -r 
env
```
**Click on "New Reply" and put the results inside [CODE] tags to be easier to read. **[See here how]("http://i.stack.imgur.com/zADbK.png")

Thanks

---

### Post by rebornishard on 2012-11-15
> **NikTh said:**
> Hi , 
please give the results 
```
lsb_release -rcd ; uname -r 
env
```
**Click on "New Reply" and put the results inside ```
 tags to be easier to read. **[See here how]("http://i.stack.imgur.com/zADbK.png")

Thanks
Thank you and sorry NikTh

[CODE]Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise
3.2.0-33-generic

```
```
SSH_AGENT_PID=2571
GPG_AGENT_INFO=/home/pau/.cache/keyring-JB6Vjf/gpg:0:1
TERM=xterm
SHELL=/bin/bash
XDG_SESSION_COOKIE=bfcf543faa3445af4636cfeb00000008-1352977561.931737-594864162
WINDOWID=58720262
GNOME_KEYRING_CONTROL=/home/pau/.cache/keyring-JB6Vjf
USER=pau
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lz=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:
LIBGL_DRIVERS_PATH=/usr/lib/fglrx/dri:/usr/lib32/fglrx/dri:/usr/lib/x86_64-linux-gnu/dri
XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session0
XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
SSH_AUTH_SOCK=/home/pau/.cache/keyring-JB6Vjf/ssh
SESSION_MANAGER=local/malware:@/tmp/.ICE-unix/2529,unix/malware:/tmp/.ICE-unix/2529
DEFAULTS_PATH=/usr/share/gconf/ubuntu.default.path
XDG_CONFIG_DIRS=/etc/xdg/xdg-ubuntu:/etc/xdg
PATH=/usr/lib/jvm/jdk1.7.0_07/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/pau/Play/play-2.0.4
DESKTOP_SESSION=ubuntu
PWD=/home/pau
JAVA_HOME=/usr/lib/jvm/jdk1.7.0_07
GNOME_KEYRING_PID=2518
LANG=en_US.UTF-8
MANDATORY_PATH=/usr/share/gconf/ubuntu.mandatory.path
UBUNTU_MENUPROXY=libappmenu.so
COMPIZ_CONFIG_PROFILE=ubuntu
GDMSESSION=ubuntu
SHLVL=1
HOME=/home/pau
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
LOGNAME=pau
XDG_DATA_DIRS=/usr/share/ubuntu:/usr/share/gnome:/usr/local/share/:/usr/share/
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-CPsYhk4obV,guid=6fc2189ce0f228a7f1e9d39100000022
LESSOPEN=| /usr/bin/lesspipe %s
DISPLAY=:0
XDG_CURRENT_DESKTOP=Unity
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
XAUTHORITY=/home/pau/.Xauthority
_=/usr/bin/env

```

that the result

---

### Post by NikTh on 2012-11-15
> **rebornishard said:**
> Thank you and sorry NikTh
Sorry about what ? :confused:

I cannot see something weird . Try this 

```
sudo apt-get install --reinstall gsettings-desktop-schemas unity libglib2.0-0 dconf-tools
sudo dpkg --configure -a
```Thanks

---

### Post by rebornishard on 2012-11-19
> **NikTh said:**
> Sorry about what ? :confused:

I cannot see something weird . Try this 

```
sudo apt-get install --reinstall gsettings-desktop-schemas unity libglib2.0-0 dconf-tools
sudo dpkg --configure -a
```Thanks
sorry NikTh, i used quote instead of code

i reinstall ubuntu back to 12.04 then upgrade into 12.10

lsb_release -rcd ; uname -r

i got
```
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal
3.5.0-18-generic

```

now i wanted to install fglrx but without broke unity like before
i didn't install gnome or kde desktop like what i did before
now i just wanted to install vga driver
i have intel and ati driver
is there any guide that can help to install ad 12.10
thank you

---

### Post by NikTh on 2012-11-20
> **rebornishard said:**
> now i wanted to install fglrx but without broke unity like before
i didn't install gnome or kde desktop like what i did before
now i just wanted to install vga driver
i have intel and ati driver
is there any guide that can help to install ad 12.10
thank you

Well , ATI graphics in 12.10 are suffer a little , due to ATI's decision to [drop Radeon HD 2000/3000/4000 Catalyst Support](http://www.phoronix.com/scan.php?page=article&item=amd_catalyst_legacy2&num=1)
Now depends on what card you have. 
```
lspci -nnk | grep -iA2 vga
```Thanks

---

### Post by rebornishard on 2012-11-24
> **NikTh said:**
> Well , ATI graphics in 12.10 are suffer a little , due to ATI's decision to [drop Radeon HD 2000/3000/4000 Catalyst Support](http://www.phoronix.com/scan.php?page=article&item=amd_catalyst_legacy2&num=1)
Now depends on what card you have. 
```
lspci -nnk | grep -iA2 vga
```Thanks

i use 6630m
but sadly it's hybrid with intel
i already test to build it with guide from help ubuntu
then i remove ati config
but now sometimes ubuntu tell me i running on low graphic
and ask me to enable low graphic for this session
how to complete clear amd driver?
thank you NikTh

---

