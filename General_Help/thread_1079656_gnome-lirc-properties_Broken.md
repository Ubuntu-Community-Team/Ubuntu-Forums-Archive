---
title: "gnome-lirc-properties Broken"
date: 2009-02-24
forum: General Help
---

### Post by paul.maddox on 2009-02-24
Hi all,

Just upgraded to Jaunty and tried to use gnome-lirc-properties but anytime the applet tries to update any configuration (via dbus) it crashes.

Running it from the terminal shows lots of AccessDenied errors:


ERROR:dbus.proxies:Introspect error on :1.94:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.92" (uid=0 pid=7815 comm="/usr/bin/python /usr/bin/gnome-lirc-properties ") interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.94" (uid=0 pid=7836 comm="/usr/bin/python -m gnome_lirc_properties.backend "))


Any ideas how I can get around this?

Thanks.

---

### Post by bpowell1978 on 2009-04-26
Same exact problem here. *bump*

---

### Post by Dark_Koala on 2009-06-13
Me too... Still looking for a solution :(

---

### Post by darklord on 2009-06-21
Hi all,

I have found a partial fix - this relates to [https://bugs.launchpad.net/bugs/318769]("https://bugs.launchpad.net/bugs/318769").

see [https://bugs.launchpad.net/ubuntu/+source/gnome-lirc-properties/+bug/350825](https://bugs.launchpad.net/ubuntu/+source/gnome-lirc-properties/+bug/350825).

from the above link you can see that you need to alter this file
/etc/dbus-1/system.d/org.gnome.LircProperties.Mechanism.conf .

from memory change this 

```
 <policy user="root">
    <allow own="org.gnome.LircProperties.Mechanism"/>
  </policy>

``` 

to this 
```

  <policy user="root">
    <allow own="org.gnome.LircProperties.Mechanism"/>
    <allow send_destination="org.gnome.LircProperties.Mechanism"
           send_interface="org.gnome.LircProperties.Mechanism"/>
  </policy>

```

then retart dbus
```

sudo /etc/init.d/dbus reload

```

Now gnome-lirc-properties works better - you should be able to select or detect your remote control and test the controler.

for me i also seem to have to plug in the receiver again. My remote control is an "Aim RC 6" - "rc118"

The fix seems to forget the set properties in gnome-lirc-properties so i have to reset them every time after booting the computer.

---

