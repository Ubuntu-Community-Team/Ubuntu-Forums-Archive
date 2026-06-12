---
title: "enable a single gnome shell extension breaks the system"
date: 2012-03-02
forum: Desktop Environments
---

### Post by unixsurfer on 2012-03-02
Hi,
     
     I will try to describe the situation I am in as simple as possible.
     
     On 29th of February the following packages were upgraded on my 11.10     system
     upgrade libxml2 2.7.8.dfsg-4ubuntu0.1 2.7.8.dfsg-4ubuntu0.2
     upgrade file-roller 3.2.1-0ubuntu1 3.2.1-0ubuntu2
     triggers-pending gconf2 3.2.3-0ubuntu0.1
     libglib2.0-0:i386 2.30.0-0ubuntu4
     triggers-pending man-db 2.6.0.2-2
     triggers-pending desktop-file-utils 0.18-0ubuntu9
     triggers-pending gnome-menus 3.2.0-0ubuntu2
     hicolor-icon-theme 0.12-1ubuntu1
     upgrade gnome-shell 3.2.1-0ubuntu1.1 3.2.2.1-0ubuntu0.1
     install gnome-shell-common <none> 3.2.2.1-0ubuntu0.1
     upgrade python-httplib2 0.7.1-1ubuntu1 0.7.2-1ubuntu2~0.11.10.1
     upgrade python-libxml2 2.7.8.dfsg-4ubuntu0.1 2.7.8.dfsg-4ubuntu0.2
     
     After the 1st restart I noticed that CoverflowAltTab extensions was     not working and was not even listed in the gnome-tweek tool. I tried     to re-installed but didn´t help. I found out that that this     extension is not compatible with gnome-shell 3.2.2.
     
     Because I real like this extension I decided to roll back the     upgrade by installing the previous version of gnome-shell. On the     first login gnome-shell crashed and I was left with no usable     desktop.
     
     I said let's clean .config and .local/share/gnome-shell/extensions.     After that I was able to login without issues.
     But every time I was enabling  few of the following extensions I was     having the same problem
     dpkg -l|grep gnome-shell-ext|awk '{print $2}'
     gnome-shell-extensions-alternate-tab
     gnome-shell-extensions-alternative-status-menu
     gnome-shell-extensions-apps-menu
     gnome-shell-extensions-auto-move-windows
     gnome-shell-extensions-common
     gnome-shell-extensions-dock
     gnome-shell-extensions-drive-menu
     gnome-shell-extensions-gajim
     gnome-shell-extensions-native-window-placement
     gnome-shell-extensions-places-menu
     gnome-shell-extensions-system-monitor
     gnome-shell-extensions-user-theme
     gnome-shell-extensions-windows-navigator
     gnome-shell-extensions-workspace-indicator
     gnome-shell-extensions-xrandr-indicator
     
     the problem doesn't occur with a specific extension.
     
     I created another user in order to see if it is my config the same behaviour occurred.
     
     I found out that I can recover from that situation my removing     ./.config/dconf/user. But with this I lose all my desktop     configuration.
     
     Since it was a not a user conf I reinstalled all gnome-shell     packages but again the same issue.
     So even with latest gnome-shell and clean conf my gnome-shell breaks     after randomly enabling few extensions. That it was not happening before 29th Feb.
     
     What could be possible causing this? What is outside of my home     directory which can lead to this situation?
     
The errors i see on .xsession-errors after enabling a extension and restarting shell by alt-f2 and r are the following
** Message: applet now removed from the notification area
gnome-shell-calendar-server[1911]: Got HUP on stdin - exiting
gnome-session[1732]: WARNING: Application 'gnome-shell.desktop' killed by signal
      JS LOG: GNOME Shell started at Fri Mar 02 2012 08:44:25 GMT+0100 (CET)
** Message: applet now embedded in the notification area

(gnome-shell:3662): folks-WARNING **: Error preparing persona store  'eds:1330250713.18759.0@pparissis-MacBookPro': Couldn't open address  book ‘1330250713.18759.0@pparissis-MacBookPro’: Cannot open book: Cannot  process, book backend is opening

(gnome-shell:3662): Clutter-CRITICAL **: clutter_text_get_editable: assertion `CLUTTER_IS_TEXT (self)' failed

(gnome-shell:3662): Clutter-CRITICAL **: clutter_text_get_text: assertion `CLUTTER_IS_TEXT (self)' failed

(gnome-shell:3662): Clutter-CRITICAL **: clutter_text_set_text: assertion `CLUTTER_IS_TEXT (self)' failed

St-ERROR **: st_widget_get_theme_node called on the widget [0x35979d0  StButton.status-chooser-user-icon] which is not in the stage.
** Message: applet now removed from the notification area
gnome-shell-calendar-server[3671]: Got HUP on stdin - exiting
gnome-session[1732]: WARNING: Application 'gnome-shell.desktop' killed by signal
gnome-session[1732]: WARNING: App 'gnome-shell.desktop' respawning too quickly
gnome-session[1732]: CRITICAL: We failed, but the fail whale is dead. Sorry....
[Notify 08:44:27.978] Docky - Docky requires compositing to work  properly. Certain options are disabled and themes/animations will look  incorrect.

---

### Post by unixsurfer on 2012-03-04
Problem solved my removing auto-move-window extension package and installed it form extensions.gnome.org site.:)
For the full story read [here]("http://mail.gnome.org/archives/gnome-shell-list/2012-March/msg00020.html")

---

