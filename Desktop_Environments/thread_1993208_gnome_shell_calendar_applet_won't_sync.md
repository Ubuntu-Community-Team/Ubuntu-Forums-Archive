---
title: "gnome shell calendar applet won't sync"
date: 2012-06-01
forum: Desktop Environments
---

### Post by theigmo87 on 2012-06-01
I have ubuntu 12.04 with gnome shell 3.4.1 installed. I have tried everything I can find online but I cannot get the gnome shell calendar applet to display any events.  I have my Google account set up in the online accounts settings. I installed Evolution, and my google calendar syncs perfectly on there. Evolution is the default calendar application. I've tried changing the time zones as that was a bug I found, but that didn't help.  It just says that no events are scheduled even though I created an event for tomorrow.

Any ideas? I don't know which logs to put on here, so let me know what is needed. I'm not new to linux, but I'm not an expert by any means, so any help would be appreciated. Thanks.

---

### Post by lovalloj on 2012-06-01
This worked for me, without Evolution!!!
Requires a google account to sync though.

[http://www.webupd8.org/2011/09/google-calendar-gnome-shell-integration.html](http://www.webupd8.org/2011/09/google-calendar-gnome-shell-integration.html)

---

### Post by theigmo87 on 2012-06-01
i've tried that. for some reason some of the programs in my startup applications won't automatically start, such as this and my guake terminal. so because of that this won't work, and i'd really just prefer to sort out this bug instead of using a workaround. thanks for your suggestion though. anyone else?

---

### Post by hictio on 2012-06-01
That's pretty weird, mine syncs Ok with Google Calendar, from day one... Without even setting up the Online Account thingy with my Google data; everything done thru Evolution's configuration.

---

### Post by theigmo87 on 2012-06-02
I'll try deleting my online account stuff then just setting it up in evolution. I had it working in 11.10 and since I upgraded to 12.04 it hasn't worked, but I'll give it a shot. If not, I may just make my own shell extension

---

### Post by theigmo87 on 2012-06-02
Yeah I deleted my gnome online account settings, then set everything up in Evolution and still nothing showed up for calendar events.  It just says "Nothing Scheduled."  Can someone tell me where that calendar/clock applet would be located? and also where the log files are so I can look to see what errors there are. Thanks.

---

### Post by theigmo87 on 2012-06-02
Actually I have a new question for those with the calendar working. if someone could please download "dconf Editor" from the software center and navigate to org -> gnome -> evolution -> calendar and tell me what value you have for both "selected-calendars" and "selected-tasks" it would be great. Mine is empty, but I'm not sure what to put there that may make it work.

or just type this into terminal if you have gsettings (which idk if it comes installed as default):
> gsettings get org.gnome.shell.evolution.calendar selected-calendars

and let me know what it returns please. Thanks.

---

### Post by theigmo87 on 2012-06-02
bump

---

### Post by hictio on 2012-06-03
There you go:

```

stilgar > gsettings get org.gnome.shell.evolution.calendar selected-calendars 
No such schema 'org.gnome.shell.evolution.calendar'

```

This is a plain vanilla Precise Pangolin (32 bits) with all the updates installed.
I've installed Gnome Shell thru Gnome's PPA, like this: [Installing Gnome 3 on Ubuntu 12.04 (Precise Pangolin)](http://www.filiwiese.com/installing-gnome-on-ubuntu-12-04-precise-pangolin/).

---

### Post by theigmo87 on 2012-06-03
yeah I have no idea what created that key then... I mean its obviously something with evolution but i don't know what. I even installed ubuntu 12.04, then gnome-shell, then set up my online accounts, then evolution, and I didn't have the key and my calendar applet worked. I have no idea what's going on, but any ideas would be appreciated.

---

### Post by hictio on 2012-06-03
> **theigmo87 said:**
> yeah I have no idea what created that key then... I mean its obviously something with evolution but i don't know what. I even installed ubuntu 12.04, then gnome-shell, then set up my online accounts, then evolution, and I didn't have the key and my calendar applet worked. I have no idea what's going on, but any ideas would be appreciated.

I have followed exactly those same steps, and mine it is working... Except that I don't setup Online Accounts, and my Evolution setup it is actually a restore from the Evolution I had on Lucid Lynx.
(I love Evolution, BTW, it is heavy weight, but I'm migrating basically the same setup since 7.04 or so)

---

### Post by theigmo87 on 2012-06-03
whoops, I meant I installed ubuntu 12.04 on a virtual machine earlier this morning and tried the same setup I did on this one. And it worked on the virtual machine, and like you said that one key didn't exist on that setup either. So I'm not sure what to do. Does anyone know where to look for the log files for that applet or gnome-shell in general?

---

### Post by theigmo87 on 2012-06-03
well after looking around, i decided to look at ~/.xsession-errors. and after disabling all of my extensions as well as many startup applications, this is my current error log:

```
/etc/mdm/Xsession: Beginning session setup...
localuser:theigmo87 being added to access control list
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/home/theigmo87/.cache/keyring-eaxbLU
SSH_AUTH_SOCK=/home/theigmo87/.cache/keyring-eaxbLU/ssh
GNOME_KEYRING_CONTROL=/home/theigmo87/.cache/keyring-eaxbLU
SSH_AUTH_SOCK=/home/theigmo87/.cache/keyring-eaxbLU/ssh
GPG_AGENT_INFO=/home/theigmo87/.cache/keyring-eaxbLU/gpg:0:1
GNOME_KEYRING_CONTROL=/home/theigmo87/.cache/keyring-eaxbLU
SSH_AUTH_SOCK=/home/theigmo87/.cache/keyring-eaxbLU/ssh
GPG_AGENT_INFO=/home/theigmo87/.cache/keyring-eaxbLU/gpg:0:1
GNOME_KEYRING_CONTROL=/home/theigmo87/.cache/keyring-eaxbLU
SSH_AUTH_SOCK=/home/theigmo87/.cache/keyring-eaxbLU/ssh
GPG_AGENT_INFO=/home/theigmo87/.cache/keyring-eaxbLU/gpg:0:1
=== xinerama setup Configuration ===
  Clone: false
  Output: Laptop attached to default
     status: on
     width: 1280
     height: 800
     rate: 50
     primary: true
     position: 0 0
=== auto-configure - xinerama mode Configuration ===
  Clone: false
  Output: Laptop attached to default
     status: on
     width: 1280
     height: 800
     rate: 50
     primary: true
     position: 0 0
=== Applying Configuration Configuration ===
  Clone: false
  Output: Laptop attached to default
     status: on
     width: 1280
     height: 800
     rate: 50
     primary: true
     position: 0 0
gnome-session[2241]: WARNING: Failed to start app: Unable to start application: Failed to execute child process "/usr/lib/tracker/tracker-miner-fs" (No such file or directory)
gnome-session[2241]: WARNING: Failed to start app: Unable to start application: Failed to execute child process "/usr/lib/tracker/tracker-store" (No such file or directory)
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Initializing nautilus-image-converter extension
Initializing nautilus-dropbox 1.4.0
** Message: applet now removed from the notification area

(nm-applet:2541): Gtk-WARNING **: Theme directory apps/24 of theme fs-icons-gnome-style has no size field


(nm-applet:2541): Gtk-WARNING **: Theme directory status/24 of theme fs-icons-gnome-style has no size field


(nautilus:2548): Gtk-WARNING **: Theme directory apps/24 of theme fs-icons-gnome-style has no size field


(nautilus:2548): Gtk-WARNING **: Theme directory status/24 of theme fs-icons-gnome-style has no size field


(nautilus:2548): Gtk-WARNING **: Theme directory apps/24 of theme fs-icons has no size field


(nm-applet:2541): Gtk-WARNING **: Theme directory apps/24 of theme fs-icons has no size field


(nm-applet:2541): Gtk-WARNING **: Theme directory status/24 of theme fs-icons has no size field


(nautilus:2548): Gtk-WARNING **: Theme directory status/24 of theme fs-icons has no size field

** Message: using fallback from indicator to GtkStatusIcon

(nautilus:2548): Gdk-WARNING **: gdk_window_set_icon_list: icons too large

** (nautilus:2548): WARNING **: Can not get _NET_WORKAREA

** (nautilus:2548): WARNING **: Can not determine workarea, guessing at layout
Window manager warning: Log level 16: Theme directory apps/24 of theme fs-icons-gnome-style has no size field

Window manager warning: Log level 16: Theme directory status/24 of theme fs-icons-gnome-style has no size field

Window manager warning: Log level 16: Theme directory apps/24 of theme fs-icons has no size field

Window manager warning: Log level 16: Theme directory status/24 of theme fs-icons has no size field

      JS LOG: Warning: Missing "url" property in [email]removeaccesibility@lomegor/metadata.json[/email]
      JS LOG: Warning: Missing "url" property in [email]calint@theigmo87.gmail.com/metadata.json[/email]
      JS LOG: Warning: Missing "url" property in [email]quicklists@damianbasic.gmail.com/metadata.json[/email]
      JS LOG: Warning: Missing "url" property in [email]battery-remaining-time@dadexix86.github.com/metadata.json[/email]
      JS LOG: Warning: Missing "url" property in [email]remove-activities-button@missoft.fr/metadata.json[/email]
      JS LOG: Extension "user-theme@gnome-shell-extensions.gcampax.github.com" is already loaded
      JS LOG: Extension "alternative-status-menu@gnome-shell-extensions.gcampax.github.com" is already loaded
      JS LOG: Extension "alternate-tab@gnome-shell-extensions.gcampax.github.com" is already loaded
      JS LOG: GNOME Shell started at Sun Jun 03 2012 18:09:35 GMT-0400 (EDT)
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(gnome-settings-daemon:2323): color-plugin-WARNING **: failed to get edid: unable to get EDID for output

(gnome-settings-daemon:2323): color-plugin-WARNING **: unable to get EDID for xrandr-default: unable to get EDID for output

(gnome-settings-daemon:2323): color-plugin-WARNING **: failed to reset xrandr-default gamma tables: gamma size is zero
** Message: applet now embedded in the notification area
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1800004 (Desktop) with a timestamp of 0.  This shouldn't happen!

(gnome-shell:2496): eds-WARNING **: edsf-persona-store.vala:2078: Error in address book view query: GDBus.Error:org.gnome.evolution.dataserver.AddressBook.OtherError: Cannot connect to the service's server.

(gnome-shell:2496): eds-WARNING **: edsf-persona-store.vala:2078: Error in address book view query: GDBus.Error:org.gnome.evolution.dataserver.AddressBook.OtherError: Cannot connect to the service's server.

(gnome-shell:2496): eds-WARNING **: edsf-persona-store.vala:2078: Error in address book view query: GDBus.Error:org.gnome.evolution.dataserver.AddressBook.OtherError: Cannot connect to the service's server.

(gnome-shell:2496): eds-WARNING **: edsf-persona-store.vala:2078: Error in address book view query: GDBus.Error:org.gnome.evolution.dataserver.AddressBook.OtherError: Cannot connect to the service's server.
    JS ERROR: !!!   Call to GetConnectionUnixProcessID failed
    JS ERROR: !!!     message = '"Expected type utf8 for Argument 'wmclass' but got type 'undefined' (nil)"'
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = '"gjs_throw"'
    JS ERROR: !!!     stack = '"("Expected type utf8 for Argument 'wmclass' but got type 'undefined' (nil)")@gjs_throw:0
()@/usr/share/gnome-shell/js/ui/notificationDaemon.js:589
wrapper()@/usr/share/gjs-1.0/lang.js:204
()@/usr/share/gnome-shell/js/ui/notificationDaemon.js:601
wrapper()@/usr/share/gjs-1.0/lang.js:204
([object Object],null)@/usr/share/gnome-shell/js/ui/notificationDaemon.js:539
wrapper([object Object],null)@/usr/share/gjs-1.0/lang.js:204
([object Object],[object Object])@/usr/share/gnome-shell/js/ui/notificationDaemon.js:425
wrapper([object Object],[object Object])@/usr/share/gjs-1.0/lang.js:204
([object Array],null)@/usr/share/gnome-shell/js/ui/notificationDaemon.js:333
([object _private_Gio_DBusProxy],[object _private_Gio_SimpleAsyncResult])@/usr/share/gjs-1.0/overrides/Gio.js:85
"'
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x200013e (Guake!) with a timestamp of 0.  This shouldn't happen!

** (nautilus:2548): WARNING **: Error calling current_status: Method "current_status" with signature "" on interface "com.ubuntuone.SyncDaemon.Status" doesn't exist


** (nautilus:2548): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1800004 (Desktop) with a timestamp of 0.  This shouldn't happen!

(evolution:3650): Gtk-WARNING **: Theme directory apps/24 of theme fs-icons-gnome-style has no size field


(evolution:3650): Gtk-WARNING **: Theme directory status/24 of theme fs-icons-gnome-style has no size field


(evolution:3650): Gtk-WARNING **: Theme directory apps/24 of theme fs-icons has no size field


(evolution:3650): Gtk-WARNING **: Theme directory status/24 of theme fs-icons has no size field

Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x1800004 (Desktop) with a timestamp of 0.  This shouldn't happen!
[9326:9326:451376841:ERROR:browser_main_loop.cc(147)] GTK theme error: Theme directory apps/24 of theme fs-icons-gnome-style has no size field

[9326:9326:451376942:ERROR:browser_main_loop.cc(147)] GTK theme error: Theme directory status/24 of theme fs-icons-gnome-style has no size field

[9326:9326:451380864:ERROR:browser_main_loop.cc(147)] GTK theme error: Theme directory apps/24 of theme fs-icons has no size field

[9326:9326:451380945:ERROR:browser_main_loop.cc(147)] GTK theme error: Theme directory status/24 of theme fs-icons has no size field
```


the only thing in there i think is related to my problem is an error about the evolution data server, even though that error is related to the address book.  I would think that the gnome shell calendar applet must pull information from this same data server. can anyone else see anything or provide some other useful info?

---

### Post by cblxub on 2012-10-04
I had the same problem, with  a bizarre fix.
I have the Activities configurator extension.
find the extension- preferences
(you can also goto this  page [https://extensions.gnome.org/local/](https://extensions.gnome.org/local/)  and click the preferences icon)
I went to the activites-configurator-extension preference and changed the tranparency to "0".
!!!this froze the shell
when I rebooted  The calendar applet and all notifications worked. (the notifications were missing text as well)

I have no idea why this work. (I tried everything to fix this previously)

hope this helps.

---

### Post by cblxub on 2012-10-06
if the above is not enough to go on~

the full scope of my bug was not only the events in the calendar applet were not updating, but there was no text in any notification, coming from the tray icon.

disabling or removing shell extensions were not enough.

I am using the gnome-shell team ppa with  ubuntu12.04  for gnome 3.41...
I purged the entire ppa and reinstalled it, reinstalled gnome-shell.

It wasn't until I change the preference on activities-configurator-extention (changed the transparency to o%) did ithe shell crash. When I rebooted everything was fixed.

Is there a directory one could delete, that gnome rebuilds on reboot?
Also... since then my  google calender will only update in evolution when I either reboot, login, or restart the session.
This maybe normal, and it doesn't bother me... but I thought it might be worth mentioning. for the sake of this bug and fix.

---

