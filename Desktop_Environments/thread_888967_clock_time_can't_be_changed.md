---
title: "clock time can't be changed"
date: 2008-08-13
forum: Desktop Environments
---

### Post by ATSC on 2008-08-13
Hello,


for some reason, my gnome clock is two hours ahead. The config-panel shows the time correctly though (see below). Neither manual changes nor the configuration via internet-synchronization helps (I've selected/tried several time-servers). The location matches the timezone.

/edit: I also noticed that the login screen shows the correct time.



Sorry in advance, if this has already been posted. I've had a look but couldn't find something helpful yet.

---

### Post by phidia on 2008-08-13
It looks like the time/day applet you posted is set for "manually".
Try setting it to "Auto" or "Automatically" and see if that picks it up.
Well that's my best guess at this-there are ways to set the time from CLI but see if that slight change helps.

---

### Post by ATSC on 2008-08-14
^^been there, done that. No changes. :(

---

### Post by sayakb on 2008-08-14
Open a terminal (Applications->Accessories->Terminal) and type in:
```
sudo date -s "8/20/2008 12:48:00"
```
Correct date and time as per your's

---

### Post by ATSC on 2008-08-14
Done that, still the same. :(

---

### Post by sayakb on 2008-08-14
Try changing your timezone to -2hrs of your existing one (which would be GMT in your case)

---

### Post by ATSC on 2008-08-14
Still no changes. The config-panel shows the new time that I entered while the clock still shows the old, wrong one. I also tried to change the bios-clock, without success.

(Btw, I made a mistake in my first post: the clock is two hours **behind** the correct time)

---

### Post by Mister.Vash on 2008-08-14
Can you post the output of:
```
cat /etc/timezone
```

and the output of:
```
gconftool-2 --recursive-list /apps/panel/applets/clock_screen0
```

and the output of:
```
date -R
```

---

### Post by timkoop on 2008-08-14
Well, maybe it has something to do with Ubuntu thinking your hardware clock is set to GMT (UTC) or not.  On Linux systems, you generally set your hardware clock to UTC, then each user says which timezone they are in.

Try running this:
sudo gedit /etc/default/rcS

and change the line to
UTC=no
or
UTC=yes

--
Tim

---

### Post by ATSC on 2008-08-15
> **Mister.Vash said:**
> Can you post the output of...

Here it is, I changed the bios clock and the settings in the config panel to the supposed to be correct ones.

```
cat /etc/timezone
```

= Europe/Berlin

 ```
gconftool-2 --recursive-list /apps/panel/applets/clock_screen0
```
=
```
toplevel_id = top_panel_screen0
 bonobo_iid = OAFIID:GNOME_ClockApplet
 attached_toplevel_id = 
 use_custom_icon = false
 action_type = lock
 tooltip = 
 custom_icon = 
 launcher_location = 
 use_menu_path = false
 panel_right_stick = true
 object_type = bonobo-applet
 position = 1
 locked = true
 menu_path = applications:/
 /apps/panel/applets/clock_screen0/prefs:
  expand_weather = false
  show_weather = false
  temperature_unit = Default
  show_seconds = false
  show_tooltip = true
  config_tool = 
  gmt_time = true
  **[color=red]format = 12-hour**[/color]
  expand_tasks = false
  unix_time = false
  speed_unit = Default
  show_timezones = (kein Wert zugewiesen)
  **[color=red]hour_format = 12**[/color]
  show_week_numbers = true
  custom_format = 
  internet_time = false
  expand_locations = false
  cities = [<location name="Berlin\, Deutschland" timezone="Europe/Berlin" latitude="52\,500000" longitude="13\,366667" code="EDNY" current="true"/>]
  show_date = true
  expand_birthdays = false
  expand_appointments = false
  show_temperature = false
  /apps/panel/applets/clock_screen0/prefs/timezones:
   tz_id_list = (kein Wert zugewiesen)
```


```
date -R
```
=
```
Fri, 15 Aug 2008 18:27:46 +0200
```


@timkoop: I already had a look. It's already set to UTC=No

I noticed in the "clock_screen0" that "format" and "time_format" is not correct either. I've selected the 24-hour format in the config-panel, instead of the 12-hour format as indicated above.

Many thanks for your support. :)

---

### Post by ATSC on 2008-08-20
[img]http://img373.imageshack.us/img373/2152/tumbleweeds01fq4.jpg[/img]

no ideas? :(

---

### Post by snowShoveler on 2008-12-07
> **ATSC said:**
> 
 ```
gconftool-2 --recursive-list /apps/panel/applets/clock_screen0
```
=
```
toplevel_id = top_panel_screen0
 bonobo_iid = OAFIID:GNOME_ClockApplet
 attached_toplevel_id = 
 use_custom_icon = false
 action_type = lock
 tooltip = 
 custom_icon = 
 launcher_location = 
 use_menu_path = false
 panel_right_stick = true
 object_type = bonobo-applet
 position = 1
 locked = true
 menu_path = applications:/
 /apps/panel/applets/clock_screen0/prefs:
  expand_weather = false
  show_weather = false
  temperature_unit = Default
  show_seconds = false
  show_tooltip = true
  config_tool = 
  gmt_time = true
  **[color=red]format = 12-hour**[/color]
  expand_tasks = false
  unix_time = false
  speed_unit = Default
  show_timezones = (kein Wert zugewiesen)
  **[color=red]hour_format = 12**[/color]
  show_week_numbers = true
  custom_format = 
  internet_time = false
  expand_locations = false
  cities = [<location name="Berlin\, Deutschland" timezone="Europe/Berlin" latitude="52\,500000" longitude="13\,366667" code="EDNY" current="true"/>]
  show_date = true
  expand_birthdays = false
  expand_appointments = false
  show_temperature = false
  /apps/panel/applets/clock_screen0/prefs/timezones:
   tz_id_list = (kein Wert zugewiesen)
```

I noticed in the "clock_screen0" that "format" and "time_format" is not correct either. I've selected the 24-hour format in the config-panel, instead of the 12-hour format as indicated above.

Many thanks for your support. :)

I had the same problem time displayed was actual + utc offset.  If you look above, the flag gmt_time = true!  If you change to false, it displays right, at least for me.  I dual boot XP and 8.04 so the hw clock is local time.  This wasn't an issue until I upgraded 7.10 to 8.04, although the time showed up in evolution wrong if I remember right.  Anyways, I opened a terminal and ran ```
 gconf-editor
```

Youll have to navigate the folder tree to find it.  apps->panel->applets->clock_screen0->prefs and some options show up on the right. Scroll and find the gmt_time key. Uncheck it and the gnome clock will display correctly! 
It leaves the hardware clock alone, and shows the right time with the ```
date -R
``` command.  
I have not rebooted yet to see if it will stick, but found your post while trying to figure out my own problem.  
Good luck!

---

### Post by ATSC on 2008-12-18
^^ P-E-R-F-E-C-T! Many thanks! :D

---

