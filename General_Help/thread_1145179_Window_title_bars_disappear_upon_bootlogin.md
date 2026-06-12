---
title: "Window title bars disappear upon boot/login"
date: 2009-05-01
forum: General Help
---

### Post by jacksonpollack on 2009-05-01
When I started up my computer today (running Jaunty) the title bars of all my windows were missing, and my workspace switcher just showed a single workspace. I looked at the Compiz settings, and windows decoration and place windows were checked. Unchecking and rechecking them had no effect.
I then went to Preferences>Appearance and saw that for some reason my visual effects were turned off. Of course, I should still have title bars even when they are turned off... Changing the setting makes the title bars reappear, so that's good.
But when I restart or log out, the same thing happens: all visual effects are set back to “none” and all my title bars are gone. I don't want to enable having title bars every time I log in!

I've read that when this happens some people are having graphics card problems, but everything was working fine before, and I didn't change any settings. Any help would be much appreciated.

---

### Post by KhurramM on 2009-05-01
Goto

gconf-editor

Goto Desktop > Gnome> applications > window_manager

Change /usr/bin/compiz to /usr/bin/metacity in the first two enteries on the right.

Restart X

Hope this solves your issues.

---

### Post by jbrown96 on 2009-05-01
> **jacksonpollack said:**
> When I started up my computer today (running Jaunty) the title bars of all my windows were missing, and my workspace switcher just showed a single workspace. I looked at the Compiz settings, and windows decoration and place windows were checked. Unchecking and rechecking them had no effect.
I then went to Preferences>Appearance and saw that for some reason my visual effects were turned off. Of course, I should still have title bars even when they are turned off... Changing the setting makes the title bars reappear, so that's good.
But when I restart or log out, the same thing happens: all visual effects are set back to “none” and all my title bars are gone. I don't want to enable having title bars every time I log in!

I've read that when this happens some people are having graphics card problems, but everything was working fine before, and I didn't change any settings. Any help would be much appreciated.

When you login try pressing Alt+F2 and then enter ```
emerald --replace
``` If that fixes the problem, then we can just auotmatically run the command when you login. 

System--->Preferences--->Sessions. Create a new entry and insert the same command. You can name and descibe it as you see fit.

---

### Post by jacksonpollack on 2009-05-01
Thanks for your quick responses, but neither solution seems to work.

Changing the setting in gconf-editor to metacity did nothing at all when I rebooted, and when I try the "emerald --replace" idea, I just get this error: Could not open location 'file://~/emerald%20--replace' Error stating file '~/emerald --replace': No such file or directory.

---

### Post by evermooingcow on 2009-05-01
See if this works
```
gtk-window-decorator
```

If it does open compiz preferences and paste the command into the window decorator optional startup commands field.

---

### Post by jacksonpollack on 2009-05-01
No, gtk-window-decorator seemed to do nothing.

The problem really goes beyond the window decoration/title bar though. Like I said, my extra workspaces disappear, but there's a ton of other options turned off. Unless I go to appearances and turn on the visual effects, I can't even hit Atl+F2 to get the run application box to pop up! Somehow no changes to any setting are being saved.

---

### Post by jacksonpollack on 2009-05-02
I uninstalled and reinstalled compiz as that was just about the only thing I could think of to do – even with it uninstalled I had the same problem. The visual effects in Preferences>Appearances are reset to “none” each time I log in (and the title bars still disappear, etc.). Is there any way to control this manually? Force it remember my settings?

I'm not sure what I should do at this point!

---

### Post by Brandon Williams on 2009-05-02
Do you see any errors in ~/.xsession-errors that could be related to this? And what theme are you using? Does the problem persist if you change your theme?

As for forcing it to remember your settings, I have a problem with the system applying some of my key bindings. To get around it, I figured out gconf setting that is associated with the key binding, and I added a script to my startup applications that using gconftool-2 to unset and reapply the desired gconf setting when I log in. You might be able to do something similar. I'm not sure what gconf key you would need to use, though. You might be able to find it by just browsing the keys with gconf-editor.

---

### Post by jacksonpollack on 2009-05-02
I use clearlooks (though customized from there), but changing the theme to something else does nothing.

Here's the contents of the .xsession-errors file. I really don't know enough to interpret this kind of thing, sorry, though some of those nautilus warnings seem suspicious to me...

```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Unable to create /home/aibara/.dbus/session-bus
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
GNOME_KEYRING_SOCKET=/tmp/keyring-k5to8d/socket
SSH_AUTH_SOCK=/tmp/keyring-k5to8d/socket.ssh
Failure: Module initalization failed

** (gsynaptics-init:3287): WARNING **: Using synclient
** (gnome-panel:3282): DEBUG: Adding applet 0.
** (gnome-panel:3282): DEBUG: Initialized Panel Applet Signaler.
** (nm-applet:3285): DEBUG: applet_common_device_state_changed
** (nm-applet:3285): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:3285): DEBUG: applet_common_device_state_changed
** (nm-applet:3285): DEBUG: applet_common_device_state_changed
** (nm-applet:3285): DEBUG: applet_common_device_state_changed
** (nm-applet:3285): DEBUG: foo_client_state_changed_cb
** (nm-applet:3285): DEBUG: applet_common_device_state_changed
** (gnome-panel:3282): DEBUG: Adding applet 1.

(gnome-panel:3282): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:3282): DEBUG: Adding applet 2.
** (gnome-panel:3282): DEBUG: Adding applet 3.
** (gnome-panel:3282): DEBUG: Adding applet 4.
** (gnome-panel:3282): DEBUG: Adding applet 5.

** (nautilus:3283): WARNING **: Unable to add monitor: Not supported

** (nautilus:3283): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:3283): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:3283): WARNING **: Can not get _NET_WORKAREA

** (nautilus:3283): WARNING **: Can not determine workarea, guessing at layout
** (nm-applet:3285): DEBUG: applet_common_device_state_changed
** (nm-applet:3285): DEBUG: foo_client_state_changed_cb
** (gnome-panel:3282): DEBUG: Adding applet 6.
** (gnome-panel:3282): DEBUG: Adding applet 7.

(gnome-panel:3282): GLib-CRITICAL **: g_bookmark_file_load_from_data: assertion `length != 0' failed
There is no available graphics driver for your system which supports the composite extension, or the current one already supports it.
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

(gnome-appearance-properties:3523): GLib-CRITICAL **: g_array_free: assertion `array' failed
Starting gtk-window-decorator
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:3283): GLib-CRITICAL **: g_bookmark_file_load_from_data: assertion `length != 0' failed

(nautilus:3283): Gtk-WARNING **: Attempting to store changes into `/home/aibara/.recently-used.xbel', but failed: Failed to rename file '/home/aibara/.recently-used.xbel.WJA8SU' to '/home/aibara/.recently-used.xbel': g_rename() failed: Operation not permitted

(nautilus:3283): Gtk-WARNING **: Attempting to set the permissions of `/home/aibara/.recently-used.xbel', but failed: Operation not permitted

(gedit:3688): GLib-CRITICAL **: g_bookmark_file_load_from_data: assertion `length != 0' failed

(gedit:3688): Gtk-WARNING **: Attempting to store changes into `/home/aibara/.recently-used.xbel', but failed: Failed to rename file '/home/aibara/.recently-used.xbel.O8NBTU' to '/home/aibara/.recently-used.xbel': g_rename() failed: Operation not permitted

(gedit:3688): Gtk-WARNING **: Attempting to set the permissions of `/home/aibara/.recently-used.xbel', but failed: Operation not permitted

```

---

### Post by vishy1618 on 2009-05-02
Ok, I had this same problem...maybe ur in luck
goto System>Preferences>Startup Applications(Jaunty) or
goto System>Preferences>Sessions(Intrepid and below)
There search for an entry called devilspie and untick it or remove it.
Also, uninstall the package called devilspie from synaptic.
Log out and log in or do a restart... I think that should fix the problem...

---

### Post by jacksonpollack on 2009-05-02
No, devilspie isn't in the startup applications menu, and not even installed in synaptic. I was hoping it would be!

---

### Post by vishy1618 on 2009-05-02
Hmm..strange..in startup applications, under gnome-wm, what command is there?

---

### Post by tee4cute on 2009-05-02
I've the same issue like u T^T (here is my thread [http://ubuntuforums.org/showthread.php?t=1146086&highlight=desktop+visual+effects]("http://ubuntuforums.org/showthread.php?t=1146086&highlight=desktop+visual+effects"))

I do something to make it easier every time I reboot the system. Due to this problem, some effect settings in "COMPIZ MANAGER" are set to default and number of rows of "Desktop Switcher" is set to 1 every time I reboot. So, I make shell script to set some "COMPIZ" effects I preferred and number of rows of "Desktop Switcher" to 2 (<-- I prefer 2 ^^) with "gconftool-2" command. Then, add this script to startup programs. This help me easier every time I reboot the system. ^^

Hope to see the real resolution soonly!!!!!

---

### Post by jacksonpollack on 2009-05-02
Vishy, I don't see gnome-vm there at all. There's a gnome keyring daemon, login sound, settings deamon, setting deamon helper and splash screen. There's also a volume manager, is that what you mean?

Hmm, I have an Intel mobile 945GM like you, tee4cute. I wonder if it not being recognized properly at login might have something to do with the problem? Do all your menu bars disappear each time too?

---

### Post by tee4cute on 2009-05-02
My all themes and menu bar icons/settings are persisted. I only have the problem about "Desktop Effects". As you say, because of "Desktop Effects" issue, this make everything goes wrong. I think I agree with you that this makes the "Windows Title Bar" disappear and "Desktop Switcher" has 1 viewport. Because every time I set the "Desktop Effects" back to "Normal", everything will gonna be OK.

Have you the display driver problem like me? I've googled around and found some interesting issues about this ([http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html]("http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html")).

From the above link, there are 2 methods to solve the display driver problem. First is to revert the driver back and another one is using default GNOME driver but changing memory config instead. According to these methods, I think the second method is better because of using 9.04 driver. But I tried the second method and it didn't work. So I have to follow the first method.

"I guess that this problem occurs because using the driver which is not provided by ubuntu official release."

I'm really not sure about this. So, I want to know about your display driver issue to judge my thought.

^^ Thanks.

---

### Post by jacksonpollack on 2009-05-02
Hmm. Yeah, my problem goes beyond the "desktop effects" being set to "none". My theme stays the same, by the title bars are gone. 

I haven't had any video display driver problems... unless this is somehow related? Once I manually reset the settings all the effects I want work, and stuff like video playback works just fine. What I don't understand is that I upgraded to Jaunty from Intrepid a week ago, and everything was ok for those few days. Then, all of a sudden, this problem occurs.

---

### Post by tee4cute on 2009-05-02
I think the driver issue may relate to this problem because a lot of cases that are about "Desktop Effects" are rely display driver problem. So I guess that this may relate to our facing problem.

(I upgraded from intrepid too. And before I do upgrade, everything is fine >.<)

---

### Post by Brandon Williams on 2009-05-02
I see a lot of permissions related errors/warnings in your .xsession-errors file. This makes me think that you quite likely have a permissions error for the .gconf directories, too, which would prevent gconf from being able to save your configuration changes.

Open a terminal and run this command:
```
find . -not -writable -ls
```

This will give you a listing of all directories and files that you do not have write permission for. From your .xsession-errors file, it looks like some directories and/or file that should not show up in this list will, such as: ./.dbus/session-bus and ./.recently-used.xbel. I'm wondering whether ./.gconf and/or ./.gconfd shows up in the list.

---

### Post by jacksonpollack on 2009-05-02
Here's the output I get from "find . -not -writable -ls", though I see nothing involving gconf:

489820    0 lrwxrwxrwx   1 aibara   aibara         41 Apr 28 10:47 ./.screen-profiles/profile -> /usr/share/screen-profiles/profiles/plain
440875    0 lrwxrwxrwx   1 aibara   aibara         13 Apr  6 14:50 ./.wine/dosdevices/g: -> /media/disk-1
443355    0 lrwxrwxrwx   1 aibara   aibara          1 Jun 26  2008 ./.wine/dosdevices/z: -> /
440806    0 lrwxrwxrwx   1 aibara   aibara         17 Feb 15 20:48 ./.wine/dosdevices/f: -> /media/MAI-ZIP\ #3
440800    0 lrwxrwxrwx   1 aibara   aibara          9 Apr  6 14:50 ./.wine/dosdevices/g:: -> /dev/sdb1
440901    0 lrwxrwxrwx   1 aibara   aibara          8 Aug 21  2008 ./.wine/dosdevices/e:: -> /dev/sdb
440712    0 lrwxrwxrwx   1 aibara   aibara          9 Feb 15 20:48 ./.wine/dosdevices/f:: -> /dev/sdb4
408996    4 -rw-r--r--   1 root     root           31 Feb  1 18:48 ./.usb-creator.log
411304    0 lrwxrwxrwx   1 aibara   aibara         34 Jun 27  2008 ./.themes/aud-Default -> /usr/share/audacious/Skins/Default
408349    0 -rw-r--r--   1 aibara   aibara          0 Jun 25  2008 ./.recently-used.xbel
416208    0 lrwxrwxrwx   1 aibara   aibara         15 May  2 17:43 ./.mozilla/firefox/tah64t23.default/lock -> 127.0.1.1:+3861
416593  620 -r--------   1 aibara   aibara     627978 Jun  3  2008 ./.mozilla/firefox/tah64t23.default/extensions/{1018e4d6-728f-4b20-ad56-37578a4de76b}/db.dat
416596    4 -r--------   1 aibara   aibara       1582 Jun  3  2008 ./.mozilla/firefox/tah64t23.default/extensions/{1018e4d6-728f-4b20-ad56-37578a4de76b}/chrome.manifest
416595    4 -r--------   1 aibara   aibara        560 Nov  7  2007 ./.mozilla/firefox/tah64t23.default/extensions/{1018e4d6-728f-4b20-ad56-37578a4de76b}/defaults/preferences/prefs.js
416594  440 -r--------   1 aibara   aibara     443531 Jun  3  2008 ./.mozilla/firefox/tah64t23.default/extensions/{1018e4d6-728f-4b20-ad56-37578a4de76b}/chrome/flagfox.jar
416586    4 -r--------   1 aibara   aibara       1241 Jun  3  2008 ./.mozilla/firefox/tah64t23.default/extensions/{1018e4d6-728f-4b20-ad56-37578a4de76b}/install.rdf
416322    4 -r--------   1 aibara   aibara       2782 Jul 28  2008 ./.mozilla/firefox/tah64t23.default/extensions/{d40f5e7b-d2cf-4856-b441-cc613eeffbe3}/locale/de-DE/bp.dtd
416321    4 -r--------   1 aibara   aibara       2652 Jul 28  2008 ./.mozilla/firefox/tah64t23.default/extensions/{d40f5e7b-d2cf-4856-b441-cc613eeffbe3}/locale/en-US/bp.dtd
416325    4 -r--------   1 aibara   aibara        188 Aug  5  2008 ./.mozilla/firefox/tah64t23.default/extensions/{d40f5e7b-d2cf-4856-b441-cc613eeffbe3}/chrome.manifest
416320    4 -r--------   1 aibara   aibara        836 Jul 26  2008 ./.mozilla/firefox/tah64t23.default/extensions/{d40f5e7b-d2cf-4856-b441-cc613eeffbe3}/defaults/preferences/bpprefs.js
416324   12 -r--------   1 aibara   aibara       9459 Aug  5  2008 ./.mozilla/firefox/tah64t23.default/extensions/{d40f5e7b-d2cf-4856-b441-cc613eeffbe3}/content/bp.xul
416311   32 -r--------   1 aibara   aibara      29022 Aug  5  2008 ./.mozilla/firefox/tah64t23.default/extensions/{d40f5e7b-d2cf-4856-b441-cc613eeffbe3}/content/bp.js
416313    4 -r--------   1 aibara   aibara        699 Aug  5  2008 ./.mozilla/firefox/tah64t23.default/extensions/{d40f5e7b-d2cf-4856-b441-cc613eeffbe3}/content/menu.xul
416319    4 -r--------   1 aibara   aibara        171 Aug  5  2008 ./.mozilla/firefox/tah64t23.default/extensions/{d40f5e7b-d2cf-4856-b441-cc613eeffbe3}/content/menu.js
416314    4 -r--------   1 aibara   aibara       1280 Aug  5  2008 ./.mozilla/firefox/tah64t23.default/extensions/{d40f5e7b-d2cf-4856-b441-cc613eeffbe3}/install.rdf
416520    4 drwx------   3 root     root         4096 Jun 24  2008 ./.dbus
find: `./.dbus': Permission denied

---

### Post by Brandon Williams on 2009-05-02
Is your user name aibara? If it is, I don't understand why you can't write to .recently-used.xbel.

That isn't your problem, though. It could be that the issue is the .dbus directory. It should be owned and writable by you, not root. This will likely cause trouble for many parts of the system. Try this:
```
$ sudo chown -R aibara:aibara ~/.dbus
```

I don't know whether the will have an impact on gconf, but it should make the dbus error from your .xsession-errors file go away. It's possible that dbus is a necessary part of getting your config changes written to disk. I'm not sure. It's worth a try, though, and should be fixed anyway.

---

### Post by jacksonpollack on 2009-05-02
Yes, the user name is aibara. I changed the permissions just fine and that dbus error is now gone from .xsession-errors, but unfortunately it made no difference.

---

### Post by Brandon Williams on 2009-05-02
You probably did this already, but just to double check ...

Did you change the permissions, log out, log in, change the setting, log out, and log back in again? The first log out and log in would have been necessary to get dbus working again, and the second to see if the configuration change sticks.

---

### Post by jacksonpollack on 2009-05-02
Yeah, I did so a few times just to make sure.

---

### Post by jacksonpollack on 2009-05-03
I found this bug, which seems to be similar to what I'm going through to some extent:
[https://bugzilla.redhat.com/show_bug.cgi?id=212725#c6](https://bugzilla.redhat.com/show_bug.cgi?id=212725#c6)
It's not encouraging they never found a solution. It seems like the basic window manager just doesn't run on start up (but manually using gtk-window-decorator does nothing either, so I dunno), for whatever reason.

And now, ironically, Tomboy notes insists on doing the opposite: it starts when I don't want it to! It appears in the notification area, killing the panel applet I've been using. It doesn't appear in Preferences>Startup applications though... There seems to be some new error when I login? 

Here's my .xsession-errors again:
```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
GNOME_KEYRING_SOCKET=/tmp/keyring-0hIufJ/socket
SSH_AUTH_SOCK=/tmp/keyring-0hIufJ/socket.ssh
** (gnome-panel:6885): DEBUG: Adding applet 0.
** (gnome-panel:6885): DEBUG: Initialized Panel Applet Signaler.
x-session-manager[6781]: WARNING: Could not launch application '1038e5f9cdb0688595124132680281377500000046650036.desktop': Unable to start application: Failed to execute child process "glipper" (No such file or directory)
x-session-manager[6781]: WARNING: Could not launch application '1038e5f9cdb0688595124132680280805000000046650035.desktop': Unable to start application: Failed to execute child process "glipper" (No such file or directory)
Failure: Module initalization failed
** (gnome-panel:6885): DEBUG: Adding applet 1.
** (gnome-panel:6885): DEBUG: Adding applet 2.
** (gnome-panel:6885): DEBUG: Adding applet 3.

(gnome-panel:6885): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.

** (gsynaptics-init:6907): WARNING **: Using synclient
** (gnome-panel:6885): DEBUG: Adding applet 4.
** (gnome-panel:6885): DEBUG: Adding applet 5.
[DEBUG]: NoteManager created with note path "/home/aibara/.tomboy".
[INFO]: Initializing Mono.Addins
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.Tomboy
[DEBUG]: 	       Name: Tomboy.Tomboy,0.10
[DEBUG]: 	Description: 
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/Tomboy.exe

** (nautilus:6886): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:6886): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:6886): WARNING **: Can not get _NET_WORKAREA

** (nautilus:6886): WARNING **: Can not determine workarea, guessing at layout
** (nm-applet:6903): DEBUG: applet_common_device_state_changed
** (nm-applet:6903): DEBUG: old state indicates that this was not a disconnect 0
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** (nm-applet:6903): DEBUG: applet_common_device_state_changed
** (nm-applet:6903): DEBUG: foo_client_state_changed_cb

** (nautilus:6886): WARNING **: Unable to add monitor: Not supported

** (gnome-panel:6885): WARNING **: panel-applet-frame.c:1273: failed to load applet OAFIID:TomboyApplet:
System exception: IDL:Bonobo/GeneralError:1.0 : Child process did not give an error message, unknown failure occurred
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.PrintNotesAddin
[DEBUG]: 	       Name: Printing Support
[DEBUG]: 	Description: Allows you to print a note.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/PrintNotes.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.BacklinksAddin
[DEBUG]: 	       Name: Backlinks
[DEBUG]: 	Description: See which notes link to the one you're currently viewing.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/Backlinks.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.FixedWidthAddin
[DEBUG]: 	       Name: Fixed Width
[DEBUG]: 	Description: Adds fixed-width font style.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/FixedWidth.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.ExportToHtmlAddin
[DEBUG]: 	       Name: Export to HTML
[DEBUG]: 	Description: Exports individual notes to HTML.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/ExportToHtml.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.StickyNoteImportAddin
[DEBUG]: 	       Name: Sticky Notes Importer
[DEBUG]: 	Description: Import your notes from the Sticky Notes applet.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/StickyNoteImport.dll
[DEBUG]: StickyNoteImporter: Sticky Notes XML file does not exist or is invalid!
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.WebDavSyncServiceAddin
[DEBUG]: 	       Name: WebDav Sync Service Add-in
[DEBUG]: 	Description: Synchronize Tomboy Notes to a WebDav URL
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/WebDavSyncService.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.FileSystemSyncServiceAddin
[DEBUG]: 	       Name: Local Directory Sync Service Add-in
[DEBUG]: 	Description: Synchronize Tomboy Notes to a local file system path
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/FileSystemSyncService.dll
[DEBUG]: Unable to locate 'gnomesu' in your PATH
[DEBUG]: Using '/usr/bin/gksu' as GUI 'su' tool
[DEBUG]: Successfully found all system tools
[DEBUG]: Unable to locate 'wdfs' in your PATH
[DEBUG]: Tomboy remote control active.
[DEBUG]: EnableDisable Called: enabling... True
[DEBUG]: Binding key '<Alt>F12' for '/apps/tomboy/global_keybindings/show_note_menu'
[DEBUG]: Binding key '<Alt>F11' for '/apps/tomboy/global_keybindings/open_start_here'
** (nm-applet:6903): DEBUG: applet_common_device_state_changed
** (gnome-panel:6885): DEBUG: Adding applet 6.
** (gnome-panel:6885): DEBUG: Adding applet 7.
** (nm-applet:6903): DEBUG: applet_common_device_state_changed
** (nm-applet:6903): DEBUG: foo_client_state_changed_cb
** (gnome-panel:6885): DEBUG: Removing applet 7.
** (gnome-panel:6885): DEBUG: Removing applet 6.
** (gnome-panel:6885): DEBUG: Adding applet 6.

(gnome-panel:6885): GLib-CRITICAL **: g_bookmark_file_load_from_data: assertion `length != 0' failed
There is no available graphics driver for your system which supports the composite extension, or the current one already supports it.
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator

(gnome-appearance-properties:7206): GLib-CRITICAL **: g_array_free: assertion `array' failed

(nautilus:6886): GLib-CRITICAL **: g_bookmark_file_load_from_data: assertion `length != 0' failed

(nautilus:6886): Gtk-WARNING **: Attempting to store changes into `/home/aibara/.recently-used.xbel', but failed: Failed to rename file '/home/aibara/.recently-used.xbel.X1Q9SU' to '/home/aibara/.recently-used.xbel': g_rename() failed: Operation not permitted

(nautilus:6886): Gtk-WARNING **: Attempting to set the permissions of `/home/aibara/.recently-used.xbel', but failed: Operation not permitted

(gedit:7476): GLib-CRITICAL **: g_bookmark_file_load_from_data: assertion `length != 0' failed

```

I have no clue if all this stuff is related. I'm starting to think that I need to just start over and reinstall Ubuntu... If this was a desktop that I could leave on I wouldn't care much, but it's my laptop, and I'm constantly moving around from place to place during the day. 
Any other ideas to fix this stuff? I do appreciate everyone's help so far!

---

### Post by Brandon Williams on 2009-05-03
Before going the route of reinstallation, try to figure out whether or not it's a problem in the user config (vs. the system config).

Create a new user. Log in as that user, and test to see whether the new user has the same problem. If the new user account is functioning as expected, then you know there's a problem with your existing user account. If that's the case, just copy all important files over to the new user account, delete the old, rename the new one, and you're back to usability.

---

### Post by Brandon Williams on 2009-05-03
I just noticed [this post](http://ubuntuforums.org/showthread.php?t=1140152) about the same problem. One of the comments suggests that it is indeed user config related and that a newly created user does not exhibit the problem.

---

### Post by jacksonpollack on 2009-05-03
It was indeed something user config related. I made a new user name, transfered my files over, and everything is perfect now. I wonder what could have messed up...

In any case, thanks a ton for your help Brandon. I don't know how much time you just saved me with that last suggestion!

---

### Post by tee4cute on 2009-05-05
jackson :

I've found new solution that's easier to create new user. The problem is on .gconf. The only one thing to do is renaming the folder "~/.gconf/desktop" to "~/.gconf/desktop_old" (or delete it if you prefer). Let the system regenerate it and you will get a new clean one like creating a new user.

Thanks Brandon to enlighten me for this solution ^^.

(I think all of old users that were created in the old version of ubuntu (8.10) may be in trouble. Because I've tried to log on as guest user before to recheck that it's not user related problem. And the guest user has this problem too. This leads me to misunderstand to the problem)

Thanks everyone on this topic to find the solution !!! ^^

---

