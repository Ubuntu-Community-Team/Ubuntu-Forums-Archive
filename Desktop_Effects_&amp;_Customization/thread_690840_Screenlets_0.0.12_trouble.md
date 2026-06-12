---
title: "Screenlets 0.0.12 trouble"
date: 2008-02-07
forum: Desktop Effects &amp; Customization
---

### Post by Phristen on 2008-02-07
Downloaded a deb package from here:
[http://www.getdeb.net/app/Screenlets](http://www.getdeb.net/app/Screenlets)

All works great, except for automatic startup... They are included in the sessions manager, but they don't start.

Also, if I kill the screenlets via screenlet manager (i.e, Re-Start all Screenlets button), then they close just fine but they don't restart :( So the only was to start them is to manually click on each of them in that list... I don't like this way.

Any ideas what I'm doing wrong?

---

### Post by SomeGuyDude on 2008-02-07
> **Phristen said:**
> Downloaded a deb package from here:
[http://www.getdeb.net/app/Screenlets](http://www.getdeb.net/app/Screenlets)

All works great, except for automatic startup... They are included in the sessions manager, but they don't start.

Also, if I kill the screenlets via screenlet manager (i.e, Re-Start all Screenlets button), then they close just fine but they don't restart :( So the only was to start them is to manually click on each of them in that list... I don't like this way.

Any ideas what I'm doing wrong?

What do you have in the sessions manager? I just click the little "startup" checkbox in the manager. No idea about the kill all problem.

Which version do you have, by the way? rev 173 just got put on .deb on gnome-look.

---

### Post by Phristen on 2008-02-07
rev 173, but 169 had the same problem. (0.0.10 was working fine though)
As I've said the "startup" checkbox is checked and so they all show up in the session manager, but they dont start.

---

### Post by santiagoward2000 on 2008-02-08
> **Phristen said:**
> Downloaded a deb package from here:
[http://www.getdeb.net/app/Screenlets](http://www.getdeb.net/app/Screenlets)

All works great, except for automatic startup... They are included in the sessions manager, but they don't start.

Also, if I kill the screenlets via screenlet manager (i.e, Re-Start all Screenlets button), then they close just fine but they don't restart :( So the only was to start them is to manually click on each of them in that list... I don't like this way.

Any ideas what I'm doing wrong?

Hi!
I think the **Re-Start** button restarts the Screenlets config, not the Screenlets themselves. So, for example, it will erase your location setting for weather, the position, size and themes of all Screenlets, etc.
About the Autostart, sorry, but I have no idea! :(
Cheers!

---

### Post by SomeGuyDude on 2008-02-08
> **Phristen said:**
> All works great, except for automatic startup... They are included in the sessions manager, but they don't start.


Just noticed this part. What exactly is in the sessions manager?

---

### Post by plun on 2008-02-08
Hi all

There might be a problem for users with earlier versions installed. Discussed during development.

Start the terminal, >  mark, copy and paste commands > Enter

```
sudo apt-get remove --purge screenlets

sudo rm -rf /usr/lib/python2.5/site-packages/screenlets*
```

This is a **rm command** and as you see it removes sitepackages for screenlets.

Reinstall from Getdeb.

-------------------------------------------------------

Start screenlets-manager from terminal for error checking. (look in the terminal window when
you starts an screenlet)

```
screenlets-manager
```

Note **Start/Stop** and **Auto start on login** checkboxes.

When everything seems to be ok everything can easily be done from the screenlets icon and right-clicks.

Please also note that the manager supports drag & drop if a user downloads a new screenlet :)

Have Fun....!

---

### Post by Phristen on 2008-02-08
Ok, when I run screenlets-manager I get this:> It looks like you are running gnome
lo
eth0
0
Error - Please install python image module
/home/crisis/.config/autostart/Screenlets Daemon.desktop
/home/crisis/.config/autostart/screenlets-daemon.desktop
True
Starter already exists.
DAEMON FOUND!
Is this bad?> I think the Re-Start button restarts the Screenlets config, not the Screenlets themselves. So, for example, it will erase your location setting for weather, the position, size and themes of all Screenlets, etc.No. When I launch them manually after restart, all the position and scale config is there intact.


And this is the output of restart button:> /home/crisis/.config/autostart/NetmonitorScreenlet.desktop: 1: [Desktop: not found
/home/crisis/.config/autostart/NetmonitorScreenlet.desktop: 6: X-GNOME-Autostart-enabled=true: not found
/home/crisis/.config/autostart/ManometerScreenlet.desktop: 1: [Desktop: not found
/home/crisis/.config/autostart/ManometerScreenlet.desktop: 6: X-GNOME-Autostart-enabled=true: not found
/home/crisis/.config/autostart/ClockScreenlet.desktop: 1: [Desktop: not found
/home/crisis/.config/autostart/ClockScreenlet.desktop: 6: X-GNOME-Autostart-enabled=true: not found
/home/crisis/.config/autostart/WeatherScreenlet.desktop: 1: [Desktop: not found
/home/crisis/.config/autostart/WeatherScreenlet.desktop: 6: X-GNOME-Autostart-enabled=true: not found
/home/crisis/.config/autostart/ClearCalendarScreenlet.desktop: 1: [Desktop: not found
/home/crisis/.config/autostart/ClearCalendarScreenlet.desktop: 6: X-GNOME-Autostart-enabled=true: not found
/home/crisis/.config/autostart/SidebarScreenlet.desktop: 1: [Desktop: not found
/home/crisis/.config/autostart/SidebarScreenlet.desktop: 6: X-GNOME-Autostart-enabled=true: not found
/home/crisis/.config/autostart/DiskusageScreenlet.desktop: 1: [Desktop: not found
/home/crisis/.config/autostart/DiskusageScreenlet.desktop: 6: X-GNOME-Autostart-enabled=true: not found


---

### Post by santiagoward2000 on 2008-02-08
> **Phristen said:**
> No. When I launch them manually after restart, all the position and scale config is there intact.

Hmm... Then I have no idea what it's supposed to do. Sorry

---

### Post by plun on 2008-02-08
> **Phristen said:**
> Ok, when I run screenlets-manager I get this:Is this bad?No. When I launch them manually after restart, all the position and scale config is there intact.
And this is the output of restart button:

OK, you needs a package called python-imaging

Easiest with the terminal,  mark, copy and paste > Enter the command
```

sudo apt-get install python-imaging
```

You seems to have a little mess with the configuration.

Start screenlets-manager from terminal   > choose screenlet  >  **Reset Screenlet Config**  ( to the right)

Start/Stop again and enable autostart, look for errors

Also check the session manager  Menu System > Preferences>Sessions, maybe you have double automagic starts.

:)

---

### Post by Phristen on 2008-02-08
I installed the package and now it seems to work.
I still get some errors in the terminal though:> Error in screenlets.services.get_service_by_name: org.freedesktop.DBus.Error.ServiceUnknown: The name org.screenlets.Clock was not provided by any .service files
closingClearCalendarScreenlet
Error in screenlets.services.get_service_by_name: org.freedesktop.DBus.Error.ServiceUnknown: The name org.screenlets.ClearCalendar was not provided by any .service files
closingWeatherScreenlet
Error in screenlets.services.get_service_by_name: org.freedesktop.DBus.Error.ServiceUnknown: The name org.screenlets.Weather was not provided by any .service files
closingNetmonitorScreenlet
Error in screenlets.services.get_service_by_name: org.freedesktop.DBus.Error.ServiceUnknown: The name org.screenlets.Netmonitor was not provided by any .service files
closingManometerScreenlet
Error in screenlets.services.get_service_by_name: org.freedesktop.DBus.Error.ServiceUnknown: The name org.screenlets.Manometer was not provided by any .service files
closingDiskusageScreenlet
Error in screenlets.services.get_service_by_name: org.freedesktop.DBus.Error.ServiceUnknown: The name org.screenlets.Diskusage was not provided by any .service files
UNREGISTER screenlet: ClockScreenlet
UNREGISTER screenlet: ClearCalendarScreenlet
UNREGISTER screenlet: WeatherScreenlet
UNREGISTER screenlet: NetmonitorScreenlet
UNREGISTER screenlet: ManometerScreenlet
UNREGISTER screenlet: DiskusageScreenlet


---

### Post by plun on 2008-02-08
> **Phristen said:**
> I installed the package and now it seems to work.
I still get some errors in the terminal though:

Ok, it might be a problem with the same screenlet in both your home and share... never seen your
outputs :confused:

Folders
/usr/local/share/screenlets
~/.screenlets 

This command should give a clean ouput


```
plun@dunder:~$ **python -u /usr/share/screenlets/Clock/ClockScreenlet.py &**
[1] 9162
plun@dunder:~$ CachingBackend: Loading instances from cache
CachingBackend: Loading <Clock1>
Creating new entry for ClockScreenlet in /tmp/screenlets/screenlets.plun.running
Loading instances in: /home/plun/.config/Screenlets/Clock/default/
File: Clock1.ini
Creating new instance: 
UPDATING SHAPE
LOAD NEW THEME: station
FOUND: /usr/share/screenlets/Clock/themes/station
theme.conf found! Loading option-overrides.
theme.conf loaded: 
Name: RYX's railway-station clock
Author: RYX (aka Rico Pfaus)
Version: 1.0
Info: A typical railway-station look-alike
UPDATING SHAPE
Set options in ClockScreenlet
LOAD NEW THEME: station
FOUND: /usr/share/screenlets/Clock/themes/station
theme.conf found! Loading option-overrides.
theme.conf loaded: 
Name: RYX's railway-station clock
Author: RYX (aka Rico Pfaus)
Version: 1.0
Info: A typical railway-station look-alike
UPDATING SHAPE
OK - Clock has been initialized.
Restored instances from session 'default' ...
CachingBackend: Saving <#Clock1> :) ...
OK


```


If you cannot figure it out a complete removal is preferred, "How do I completely uninstall all screenlets?" 

[http://screenlets.org/index.php/FAQ#How_do_I_install_new_Screenlets.3F](http://screenlets.org/index.php/FAQ#How_do_I_install_new_Screenlets.3F)

And a reinstall

I uninstalled my dev Screenlets and installed Getdebs version with no issues.

---

### Post by Phristen on 2008-02-08
The only thing I have in ~/.screenlets is config.ini
Anyway, the screenlets work, so maybe those errors arent serious... I'll be doing a fresh install of Hardy in spring, anyway, so whatever I've messed up in my current installation won't matter ;)

---

