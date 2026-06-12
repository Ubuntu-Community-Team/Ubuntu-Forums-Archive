---
title: "Disabling services"
date: 2009-03-04
forum: General Help
---

### Post by Taxi on 2009-03-04
If I disable a service in the "Services Settings" dialog, what does that do?  Does it just stop the service from loading as a convenience at startup or does it prevent it from ever loading even if there's a device that needs it?  If at some point I need that service, will I need to manually re-enable it in the settings and reboot?

For example, I don't tend to use any Bluetooth devices with my system.  For me, enabling Bluetooth at startup is not worth any slowdown in boot time or ongoing memory usage if all it's doing is waiting around so that it's ready the moment I plug in a Bluetooth device, as opposed to two seconds later.  But I guess I *would* like for Bluetooth devices to be plug-and-play with my system in the event that I eventually need to use a friend's Bluetooth device or something, without having to change settings and reboot.

Basically, does disabling a service in "Services Settings" totally prevent it from running or does it just mean I'd have to wait a bit for it to load when I need it?

Thanks!

---

### Post by Chandler258 on 2009-03-04
I'm not sure about all of this but disabling them in the "Services Settings" dialog disables them and they don't load at startup anymore. 

About bluetooth

```
Usage: /etc/init.d/bluetooth {start|stop|restart|force-reload|status}
```

So if you run in the shell

```
/etc/init.d/bluetooth stop
``` 

it will stop bluetooth service. You can play with it and create launchers for enabling and disablig some services, but if you don't know what you're disabling ... don't disable it ;)

---

### Post by Taxi on 2009-03-04
Right.  So if I stop it from running at startup, does that mean it will never run, or will it just wait to load until it's explicitly needed?

---

### Post by Vince4Amy on 2009-03-04
Give BootUpManager a try it's a graphical way of editing startup services on Ubuntu/Debian.

```
sudo apt-get install bum
``` You'll find it in the System menu.

Or my favourite which is the same but ran in a command line and offers more options, sysv-rc-conf:

```
sudo apt-get install sysv-rc-conf
``` You can run that one by typing ```
sudo sysv-rc-conf
```

---

### Post by Taxi on 2009-03-04
Right. I'm not actually having trouble disabling the services (System -> Administration -> Services in GNOME should work just fine for my purposes).  My question is what disabling it actually means.

If I stop it from running at startup, does that mean it will never run, or will it just wait to load until it's explicitly needed?

---

### Post by oldos2er on 2009-03-04
I believe it means it will never run.

---

### Post by Taxi on 2009-03-05
Ok, thanks.  Maybe I'll just leave them alone if I think there's even an outside chance I'll want to use them eventually.  (acpid & powernowd can go, since my mobo doesn't even support them, but maybe bluetooth will hang around)

---

