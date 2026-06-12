---
title: "Error - Nautilus cannot handle network: locations"
date: 2009-03-21
forum: General Help
---

### Post by MountainX on 2009-03-21
I set up an application launcher with this command:
```
gksudo "nautilus --no-desktop"
```
When I use the launcher, the Nautilus instance cannot handle any network locations.

It gives the error:
[COLOR=Red][B]Nautilus cannot handle network: locations.
Couldn't display "network:///"[/B][/COLOR]


I have tried variations on the launcher command, but so far I have not found a solution.

---

### Post by dcstar on 2009-03-21
> **MountainX said:**
> I set up an application launcher with this command:
```
gksudo "nautilus --no-desktop"
```
When I use the launcher, the Nautilus instance cannot handle any network locations.

It gives the error:
[COLOR=Red][B]Nautilus cannot handle network: locations.
Couldn't display "network:///"[/B][/COLOR]


I have tried variations on the launcher command, but so far I have not found a solution.

```
gksudo "dbus-launch nautilus --no-desktop --browser %U"
```

---

### Post by MountainX on 2009-03-21
> **dcstar said:**
> ```
gksudo "dbus-launch nautilus --no-desktop --browser %U"
```

Thank you! I owe you a coffee! :)

here's what worked for me in a launcher
```
gksudo "dbus-launch nautilus --no-desktop --browser"
```

---

### Post by MountainX on 2009-03-22
This is also helpful:
```
$ nautilus --help-all
```Usage:
  nautilus [OPTION...] [URI...] 

Browse the file system with the file manager

Help Options:
  -?, --help                      Show help options
  --help-all                      Show all help options
  --help-gtk                      Show GTK+ Options
  --help-bonobo-activation        Show Bonobo Activation options
  --help-gnome                    Show GNOME options
  --help-gnome-session            Show session management options

GTK+ Options
  --class=CLASS                   Program class as used by the window manager
  --name=NAME                     Program name as used by the window manager
  --screen=SCREEN                 X screen to use
  --sync                          Make X calls synchronous
  --gtk-module=MODULES            Load additional GTK+ modules
  --g-fatal-warnings              Make all warnings fatal

Bonobo Activation options:
  --oaf-ior-fd=FD                 File descriptor to print IOR on
  --oaf-activate-iid=IID          IID to activate
  --oaf-private                   Prevent registering of server with OAF

GNOME Library
  --disable-sound                 Disable sound server usage
  --enable-sound                  Enable sound server usage
  --espeaker=HOSTNAME:PORT        Host:port on which the sound server to use is running
  --version                       

Session management:
  --sm-client-id=ID               Specify session management ID
  --sm-config-prefix=PREFIX       Specify prefix of saved configuration
  --sm-disable                    Disable connection to session manager

Application Options:
  -c, --check                     Perform a quick set of self-check tests.
  -g, --geometry=GEOMETRY         Create the initial window with the given geometry.
  -n, --no-default-window         Only create windows for explicitly specified URIs.
  --no-desktop                    Do not manage the desktop (ignore the preference set in the preferences dialog).
  --browser                       open a browser window.
  -q, --quit                      Quit Nautilus.
  -l, --load-session=FILENAME     Load a saved session from the specified file. Implies "--no-default-window".
  --display=DISPLAY               X display to use

---

### Post by MountainX on 2011-05-10
FYI - using the command "gksudo "dbus-launch nautilus --no-desktop --browser" is [SIZE=3]**dangerous**[/SIZE]!

The gksudo command "gksudo "dbus-launch nautilus --no-desktop --browser" starts a new nautilus process with root privledges. This new nautilus process continues to run (even after the nautilus window is closed) until the process is manually killed or the system is rebooted.

If you run this command once and someone later comes along and inserts any old USB disk into your computer, they will get root access without even having to type in a password! And this is true even if you ran the command days earlier (and haven't rebooted since).

The supported and preferred way to open files as root (via Nautilus) is to use a package named: nautilus-gksu. It is not installed by default, so you need to install it from the repositories with the following command:

sudo apt-get update
sudo apt-get install nautilus-gksu

Once installed, X needs to be restarted to start using the new feature(Restart X, reboot or run sudo killall nautilus).

To perform an action on a file as root, you would then navigate to the file (or directory). Then right click on the file or directory, and you will see a new option named "Open as administrator".

That should allow you to edit files as root, but also prevent any new windows that are opened via a USB mount, from being opened as root.

---

