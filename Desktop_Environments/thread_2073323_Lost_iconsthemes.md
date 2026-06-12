---
title: "Lost icons/themes"
date: 2012-10-19
forum: Desktop Environments
---

### Post by Davsharyan on 2012-10-19
Hi all,
I just upgraded from 12.04 (Ubuntu) to 12.10 and moved to Xubuntu desktop.
After login into Xubuntu session all icons and theme missing from menu bar, right-click menu .... I tried to purge all xubuntu packages also remove ~/.config/xfce folder and reinstall, but didn't help that. Any suggestion ?
Find attached.

Thnx

---

### Post by 2F4U on 2012-10-19
Looks like an issue with the upgrade. I did a fresh install and everything looks perfect. Do you get any error messages in .xsession-errors in your home folder? Am I right in assuming that the upgrade went without errors?

---

### Post by critin on 2012-10-19
Did you try All Settings?   Desktop?

If you only installed the  Xubuntu desktop,  you could Log Out, then Log In choosing ubuntu at the login screen--keeping both.

But of course, if you've already purged...

---

### Post by Davsharyan on 2012-10-19
Yes, I see some 'no such file' lines, will try fix them and update here.
And upgrade was fine w/o errors.
Thnx

> **2F4U said:**
> Looks like an issue with the upgrade. I did a fresh install and everything looks perfect. Do you get any error messages in .xsession-errors in your home folder? Am I right in assuming that the upgrade went without errors?

---

### Post by Davsharyan on 2012-10-21
Hey,
Fixed few missing file lines by installing packages, but still can't see full icons/themes.
One note, even when I try to apply another style from the Appearance, nothing changes exept sizes.
I guess something from the icons or themese packages missing. How I can force to re-install FULL xubuntu-package, once I did that but seems still sometihng missing.

p.s. Ubuntu session doesn't work too, I killed there something and now it just can't start.

Here is .xsession-errors
> openConnection: connect: No such file or directory
cannot connect to brltty at :0

(xfwm4:15081): GLib-CRITICAL **: g_str_has_prefix: assertion `prefix != NULL' failed

** (zeitgeist-datahub:15224): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/user/index.php" was not found, exec: kate, mime_type: application/x-php

** (zeitgeist-datahub:15224): WARNING **: recent-manager-provider.vala:133: Desktop file for "file:///home/user/Music/Oliver%20Koletzki%20&%20Fran/Oliver%20Koletzki%20&%20Fran%20-%20Lovestoned%20(2010)/Oliver%20Koletzki%20&%20Fran%20-%20Lovestoned.m3u" was not found, exec: amarok, mime_type: audio/x-mpegurl
log4j:ERROR [100M] is not in proper int form.
log4j:ERROR [100M] not in expected format.
java.lang.NumberFormatException: For input string: "100M"
	at java.lang.NumberFormatException.forInputString(NumberFormatException.java:65)
	at java.lang.Long.parseLong(Long.java:441)
	at java.lang.Long.valueOf(Long.java:540)
	at org.apache.log4j.helpers.OptionConverter.toFileSize(OptionConverter.java:279)
	at org.apache.log4j.RollingFileAppender.setMaxFileSize(RollingFileAppender.java:260)
	at davmail.Settings.updateLoggingConfig(Settings.java:265)
	at davmail.Settings.load(Settings.java:90)
	at davmail.Settings.load(Settings.java:106)
	at davmail.DavGateway.main(DavGateway.java:66)

(xfsettingsd:15305): GLib-CRITICAL **: g_str_has_prefix: assertion `prefix != NULL' failed

(dropbox:15197): Gtk-WARNING **: /var/lib/dropbox/.dropbox-dist/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/engines/liboxygen-gtk.so)
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon

(xfce4-indicator-plugin:15383): libindicator-WARNING **: Unable to load icon from file 'audio-volume-muted' because: Failed to open file 'audio-volume-muted': No such file or directory

(xfce4-indicator-plugin:15383): libindicator-WARNING **: Unable to load icon from file 'audio-volume-muted-blocking' because: Failed to open file 'audio-volume-muted-blocking': No such file or directory

(xfce4-indicator-plugin:15383): libindicator-WARNING **: Unable to load icon from file 'audio-output-none' because: Failed to open file 'audio-output-none': No such file or directory

(xfce4-indicator-plugin:15383): libindicator-WARNING **: IndicatorObject class does not have an accessible description.
** Message: moving back from GtkStatusIcon to indicator
The program 'wrapper' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 459 error_code 3 request_code 138 minor_code 1)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

(xfce4-indicator-plugin:15383): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(xfce4-indicator-plugin:15383): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(xfce4-indicator-plugin:15383): libindicator-WARNING **: Unable to load icon from file 'audio-volume-high' because: Failed to open file 'audio-volume-high': No such file or directory

(xfce4-indicator-plugin:15383): libindicator-WARNING **: Unable to load icon from file 'audio-volume-muted' because: Failed to open file 'audio-volume-muted': No such file or directory

(xfce4-indicator-plugin:15383): libindicator-WARNING **: Unable to load icon from file 'audio-volume-muted-blocking' because: Failed to open file 'audio-volume-muted-blocking': No such file or directory

(xfce4-indicator-plugin:15383): libindicator-WARNING **: Unable to load icon from file 'audio-volume-high' because: Failed to open file 'audio-volume-high': No such file or directory
xfce4-panel-Message: Plugin systray-4 has been automatically restarted after crash.
Error creating proxy: Error calling StartServiceByName for org.gtk.vfs.Daemon: Timeout was reached (g-io-error-quark, 24)

(xfsettingsd:15305): GVFS-CRITICAL **: fill_mountable_info: assertion `proxy != NULL' failed


---

### Post by Toz on 2012-10-23
Have you tried changing the icon theme (Settings Manager -> Appearance -> Icons)?

---

### Post by p1977p on 2012-11-02
Having the same problem with Xubuntu 12.10 with the latest updates. All the icons are gone from the file manager view. Settings -> Appearance -> Icons shows the various themes available, but nothing changes when I click any of them. All the theme files are there though.  :(

---

### Post by duphenix on 2012-11-02
I have two machines, one with this problem and one without.  

The machine that has the problem is stuck on the GNOME Icons.  I go into Appearance and change it to another set. Then restart. The selection in the Appearance menu stays elementary Xfce dark, but the Icons showing on the desktop do not change.  They stay the same as the GNOME Icons. In other words, changing the setting to another Icon set doesn't actually change the icons on the desktop.


I've tried reinstalling all the xfce and xubuntu theme and icon packages, with no help.


On my other machine, selecting a different Icons set in the Appearance menu immediately updates the icons seen on the Desktop.

Any idea why the icon set is stuck on GNOME on one machine and not the other?

---

### Post by duphenix on 2012-11-02
Ok, I've found a fix.  It's not elegant, but it works. Maybe someone else can shed some more light on the situation and provide a less drastic approach.

I went into my home folder, and deleted the ~/.config folder.  Then I logged out and logged back in.  After that I could change the icon sets in the Appearence menu.

---

### Post by Toz on 2012-11-02
Interesting. 

Is xfdesktop managing the desktop?
```
ps -ef | grep xfdesktop | grep -v grep
```

Do you maybe have nautilus managing the desktop?
```
ps -ef | grep nautilus | grep -v grep
```

Is xfsettingsd running?
```
ps -ef | grep xfsettingsd | grep -v grep
```

---

### Post by Toz on 2012-11-02
> **duphenix said:**
> Ok, I've found a fix.  It's not elegant, but it works. Maybe someone else can shed some more light on the situation and provide a less drastic approach.

I went into my home folder, and deleted the ~/.config folder.  Then I logged out and logged back in.  After that I could change the icon sets in the Appearence menu.

Perhaps something was wrong with the session. Maybe next time you could try just deleting the ~/.cache/sessions folder to see if that solves the problem. This way you won't lose all of your configuration settings.

---

### Post by Antixity on 2013-01-30
> **Toz said:**
> Have you tried changing the icon theme (Settings Manager -> Appearance -> Icons)?

Hi. I lost my menu icons in Xubuntu 12.04 and thankfully was able to get them back by going into Settings Manager -> Appearance -> Settings, and then making sure that "Show images in menus" was checked. This was the only way I could get my menu icons back. 

Hope this helps someone with the same problem.

Cheers! 
Antixity

---

### Post by Toz on 2013-01-30
> **Antixity said:**
> Hi. I lost my menu icons in Xubuntu 12.04 and thankfully was able to get them back by going into Settings Manager -> Appearance -> Settings, and then making sure that "Show images in menus" was checked. This was the only way I could get my menu icons back. 

Hope this helps someone with the same problem.

Cheers! 
Antixity

Different problem. Have a look at the first post of this thread.

---

### Post by Antixity on 2013-01-30
> **Toz said:**
> Different problem. Have a look at the first post of this thread.

Yes, I should have been more careful. Thanks for the prompt.

---

### Post by thw24 on 2013-02-10
> **Toz said:**
> Perhaps something was wrong with the session. Maybe next time you could try just deleting the ~/.cache/sessions folder to see if that solves the problem. This way you won't lose all of your configuration settings.

Had the same problem. Deleting the cache didn't solve it. I had to remove the config folders (not only the xfce!) as mentioned above and redo my configuration.  :(

Nevertheless: Thanks for the help!

---

### Post by Toz on 2013-02-10
> **thw24 said:**
> Had the same problem. Deleting the cache didn't solve it. I had to remove the config folders (not only the xfce!) as mentioned above and redo my configuration.  :(

Nevertheless: Thanks for the help!

Hello thw24 and welcome to the forums.

It is probably best to log out, go to the first tty (Ctrl+Alt+F1), log in to the text console there then:
```
cd .cache
rm -rf .sessions
exit

```
....then return to the GUI login (Ctrl+Alt+F7) and log in again.

If you delete the sessions cache while still logged in, the existing corruption may again be saved as you log out.

In Xfce 4.10, a "Clear Saved Sessions" option has been added to Settings Manager->Session and Startup->Session tab.

---

