---
title: "Dell Inspiration Screen timeout"
date: 2017-12-29
forum: Desktop Environments
---

### Post by Jonners59 on 2017-12-29
My wife has bought herself a Dell Inspiration 15 5000 Series laptop.  I have installed the latest xfce Ubuntu
```
Linux chiara-Inspiron-5567 4.13.0-21-generic #24-Ubuntu SMP Mon Dec 18 17:29:16 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

The problem is that the screen times out, and that is not the worst, it happens within minutes.

I have changed the settings in battery management and other locations...  all to no avail.

I have searched and tried a number of "fixes", but none of them work either.

Caffeine gives me this, in a terminal:
```
/usr/bin/caffeine:25: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.  from gi.repository import GObject, Gtk, GLib



```

I have another that is a script, but that does not work either:
```
#!/bin/bashexport DISPLAY=:0.0


if [ $# -eq 0 ]; then
  echo usage: $(basename $0) "on|off|status"
  exit 1
fi


if [ $1 = "off" ]; then
  echo -en "Turning monitor off..."
  xset dpms force off
  echo -en "done.\nCheck:"
  xset -q|grep "Monitor is"
elif [ $1 = "on" ]; then
  echo -en "Turning monitor on..."
  xset dpms force on
  echo -en "done.\nCheck:"
  xset -q|grep "Monitor is"
elif [ $1 = "status" ]; then
  xset -q|sed -ne 's/^[ ]*Monitor is //p'
else
  echo usage: $(basename $0) "on|off|status"
fi
```

Any help, PLEASE?

---

### Post by him610 on 2017-12-31
You might consider investigating the settings in XFCE Power Manager.
Settings>Power Manager>tab Display

---

### Post by Jonners59 on 2018-01-01
> **him610 said:**
> You might consider investigating the settings in XFCE Power Manager.
Settings>Power Manager>tab Display

Yes, did that beforeI started looking at more complex solutions.  seems there was a bug.... thank you anyway.  &#128512;

---

### Post by Jonners59 on 2018-01-05
Bump

---

### Post by flocculant on 2018-01-05
I assume that xfce4-power-manager is version 1.4.4-4ubuntu2.

You could, if you wanted to, try updating that to the version at the Xubuntu Team's Daily ppa. [https://launchpad.net/~xubuntu-dev/+archive/ubuntu/ppa](https://launchpad.net/~xubuntu-dev/+archive/ubuntu/ppa)

If you do - install ppa-purge as well, then once you've done you can ppa-purge ppa:xubuntu-dev/ppa to revert package back and disable the ppa.

Further - _just upgrade xfce4-power-manager_, the ppa has more than that in it.

You'll likely want to disable the ppa asap after testing.

Also you might want to think about xfce forum.

(The PyGIWarning: is just that - nothing to worry about)

---

### Post by Jonners59 on 2018-01-05
> **flocculant said:**
> I assume that xfce4-power-manager is version 1.4.4-4ubuntu2.

You could, if you wanted to, try updating that to the version at the Xubuntu Team's Daily ppa. [https://launchpad.net/~xubuntu-dev/+archive/ubuntu/ppa](https://launchpad.net/~xubuntu-dev/+archive/ubuntu/ppa)

If you do - install ppa-purge as well, then once you've done you can ppa-purge ppa:xubuntu-dev/ppa to revert package back and disable the ppa.

Further - _just upgrade xfce4-power-manager_, the ppa has more than that in it.

You'll likely want to disable the ppa asap after testing.

Also you might want to think about xfce forum.

(The PyGIWarning: is just that - nothing to worry about)
Thank you will look into these and feed back.... :-)

---

### Post by Jonners59 on 2018-02-03
> **flocculant said:**
> I assume that xfce4-power-manager is version 1.4.4-4ubuntu2.

You could, if you wanted to, try updating that to the version at the Xubuntu Team's Daily ppa. [https://launchpad.net/~xubuntu-dev/+archive/ubuntu/ppa](https://launchpad.net/~xubuntu-dev/+archive/ubuntu/ppa)

If you do - install ppa-purge as well, then once you've done you can ppa-purge ppa:xubuntu-dev/ppa to revert package back and disable the ppa.

Further - _just upgrade xfce4-power-manager_, the ppa has more than that in it.

You'll likely want to disable the ppa asap after testing.

Also you might want to think about xfce forum.

(The PyGIWarning: is just that - nothing to worry about)
Sorry for the delay in getting back.  I rarely get my hands on the wife's laptop to do any work on it so completely forgot.

So installed the ppa and the ppa purge app.  Could NOT install xfce4-power-manager as it said I had un resolvable dependencies.

[HTML]xfce4-power-manager:
 Depends: libxfconf-0-3 (>=4.6.0) but it is not installable[/HTML]


 I don't know how to fix that.  Any help, please?

---

