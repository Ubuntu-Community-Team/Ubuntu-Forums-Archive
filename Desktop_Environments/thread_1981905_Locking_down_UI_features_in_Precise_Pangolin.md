---
title: "Locking down UI features in Precise Pangolin"
date: 2012-05-17
forum: Desktop Environments
---

### Post by sgifford on 2012-05-17
Hello,

I'm using the new Precise Pangolin LTS release for workstations to run a dedicated set of applications in an office.  I'd like to lock down some Ubuntu/GNOME features which should not be needed by our users.  We are running a GNOME-style installation (not Unity) since it seems easier to lock down, and the interface is more straightforward for limited-purpose workstations.

In my searches, I see a lot of references to earlier versions of Ubuntu, using tools like Pessulus and Lockdown Editor.  These tools don't seem to be available for Precise Pangolin.

I have had some luck so far with tools like dconf, and I'm hoping my remaining issues can be solved using settings I haven't figured out yet, or maybe some tool I don't know about.

Here are the items I'm trying to remove/hide/disable:
[LIST]
[*]"Places" menu at the top
[*]"Time and Date Settings" below the clock (but keeping the clock itself)
[*]The virtual desktop switcher in the lower-right corner
[*]"System Settings", "Displays", "Startup Applications", and "Software Up To Date" in the gear menu
[*]"Attached Devices" and "Printers" in the gear menu
[*]"Suspend" and "Hibernate" in the gear menu (but leaving log out, shutdown, etc.)
[/LIST]

I have attached some screenshots that may help to clarify.

Thanks for any advice, tips, etc.!

---

### Post by coesunixadm on 2012-05-21
We are working on a similar thing over here.  So far we have used gsettings to modify the schemas stored in /usr/share/glib-2.0/schemas as follows: 

[COLOR=#000000][FONT=Arial]gsettings set com.ubuntu.update-notifier auto-launch false[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]gsettings set com.canonical.indicator.session suppress-restart-menuitem [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]gsettings set com.canonical.indicator.session suppress-shutdown-menuitem true[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]gsettings set com.canonical.indicator.session use-username-in-switch-item false[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]gsettings set com.canonical.unity-greeter play-ready-sound false[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]gsettings set org.gnome.desktop.lockdown disable-print-setup true[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]gsettings set org.gnome.desktop.lockdown disable-lock-screen true[/FONT][/COLOR]

Please let us know of other lockdown methods you have used.

---

### Post by sgifford on 2012-05-24
Thanks!  But, these commands give me errors, for example:
```

$ gsettings set com.ubuntu.update-notifier auto-launch false
No such key 'suppress-suspend-menuitem'
$ sudo gsettings  --schemadir /usr/share/glib-2.0/schemas set com.ubuntu.update-notifier auto-launch false
No such key 'suppress-suspend-menuitem'

```

Was there any trick to this?  Or did it just work for you?  I'm on Precise Pangolin.

As far as the settings we have locked down so far, we have done it through the dconf-editor tool, and by setting these options in the GUI:

[LIST]
[*]apps/indicator-session/user-show-menu: Off
[*]com/canonical/indicator/appmenu/bluetooth/visible: Off
[*]com/canonical/indicator/appmenu/datetime/show-events: Off
[*]com/canonical/indicator/appmenu/power/icon-policy: Never
[*]org/gnome/desktop/lockdown/disable-print-setup: On
[*]org/gnome/desktop/lockdown/disable-printing: On
[*]org/gnome/desktop/lockdown/disable-user-switching: On
[*]org/gnome/desktop/media-handling/automount: Off
[*]org/gnome/desktop/media-handling/automount-open: Off
[*]org/gnome/desktop/media-handling/automount-never: On
[*]org/gnome/desktop/screensaver/user-switch-enabled: Off
[/LIST]

Thanks for your help!

-----Scott.

---

### Post by coesunixadm on 2012-05-24
We ran into those errors after we had previously un-installed the entire update manager via: 

```
sudo apt-get remove update-manager
```Check to make sure it is properly installed on your system.  If it is there it should be in the same folder:

```
/usr/share/glib-2.0/schemas/
```

---

### Post by sgifford on 2012-05-28
Thanks, that did help with some of them!

---

### Post by kposney on 2012-11-03
Hi

I an locking it down for use in a retail stores. Found these tweaks below.

Workspace switcher app on panel removal

Installed MyUnity app allowed me to set workspaces to one which removed the workspace switcher from launcher on it’s own.



Launcher Panel reset of launcher icons to original on login.
gsettings get com.canonical.Unity.Launcher favorites

Take the results and change command to set and put in the script on login. 

gsettings set com.canonical.Unity.Launcher favorites "['gnome-terminal.desktop', 'firefox.desktop', 'chromium-browser.desktop' ]"

---

### Post by grahammechanical on 2012-11-03
Have you considered Ubuntu Business Remix? I might not be exactly what you are trying to do but as the advert says, 

> it&#8217;s just a convenient starting point that includes many common changes made by IT administrators deploying Ubuntu in a corporate setting.

[it&#8217;s just a convenient starting point that includes many common changes made by IT administrators deploying Ubuntu in a corporate setting.]("it&#8217;s just a convenient starting point that includes many common changes made by IT administrators deploying Ubuntu in a corporate setting.")

---

