---
title: "Adjusting Mouse Settings"
date: 2013-01-01
forum: Desktop Environments
---

### Post by Gannin on 2013-01-01
Using Ubuntu 12.10.

Back in the day, I could go into gconf and manually adjust the values for the mouse settings.  I don't think the newer versions of Ubuntu use gconf for the mouse settings anymore, so is there somewhere else I can look for manually adjusting the settings?  I don't mean the sliders in the system settings, I mean somewhere where you can input actual values for the mouse settings.  Thanks!

---

### Post by ajgreeny on 2013-01-01
```
synclient -l
```will show you the current values for the variables which you can then play around with using ```
synclient <variable>=#
``` eg **synclient MaxTapTime=0** to turn off tap-to-click.

See [http://ubuntuforums.org/showthread.php?t=1538147&highlight=save+synclient+settings](http://ubuntuforums.org/showthread.php?t=1538147&highlight=save+synclient+settings) for a way to make these settings permanent.

---

### Post by Gannin on 2013-01-01
> **ajgreeny said:**
> ```
synclient -l
```will show you the current values for the variables which you can then play around with using ```
synclient <variable>=#
``` eg **synclient MaxTapTime=0** to turn off tap-to-click.

See [http://ubuntuforums.org/showthread.php?t=1538147&highlight=save+synclient+settings](http://ubuntuforums.org/showthread.php?t=1538147&highlight=save+synclient+settings) for a way to make these settings permanent.

Thanks for the information, but I'm not using a touch pad.  Just a regular mouse on a regular desktop.

---

### Post by ajgreeny on 2013-01-01
Whoops!

Sorry about that; I was answering quicker than I was thinking.

---

### Post by stinkeye on 2013-01-01
dconf-editor

You can also use terminal commands with gsettings.
eg for the setting shown in pic... the get, set and reset commands...

```
[COLOR="SeaGreen"]glen@Quantal:~$[/COLOR] gsettings [COLOR="magenta"]get[/COLOR] org.gnome.settings-daemon.peripherals.mouse double-click
**400**
[COLOR="seagreen"]glen@Quantal:~$[/COLOR] gsettings [COLOR="magenta"]set[/COLOR] org.gnome.settings-daemon.peripherals.mouse double-click 300
[COLOR="seagreen"]glen@Quantal:~$[/COLOR] gsettings [COLOR="magenta"]get[/COLOR] org.gnome.settings-daemon.peripherals.mouse double-click 
**300**
[COLOR="seagreen"]glen@Quantal:~$[/COLOR] gsettings [COLOR="magenta"]reset[/COLOR] org.gnome.settings-daemon.peripherals.mouse double-click 
[COLOR="seagreen"]glen@Quantal:~$[/COLOR] gsettings [COLOR="magenta"]get[/COLOR] org.gnome.settings-daemon.peripherals.mouse double-click 
**400**
```

---

### Post by Gannin on 2013-01-01
Awesome, just what I was looking for.  Thanks!

---

### Post by grahammechanical on 2013-01-02
It is true that 12.10 does not have gconf editor any more but it does have dconf editor. It is in the Dash. What you are looking for might be under org>gnome>desktop>a11y>mouse.

regards.

---

