---
title: "Trusty (14.04) System-Config-Printer-KDE Missing, Can't Configure Printers"
date: 2015-03-16
forum: Desktop Environments
---

### Post by Illydth on 2015-03-16
Not sure what the heck's going on, several web searches have not turned up anything for me.

Ubuntu/Kubuntu 14.04 Trusty Tahr.  Installed from CD (no upgrade - Upgrade from 12.04 -> 14.10 failed and I had to re-install the system).

In 12.04 I had a printer icon in the System Settings and could configure printers that way.  In 14.04 I have no icon to configure printers.

Most docs tell me to install or reinstall system-config-printer-kde, which, according to apg-get no longer exists as a package.

[I]user@system:/etc$ sudo apt-get install system-config-printer-kde
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package system-config-printer-kde is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'system-config-printer-kde' has no installation candidate
[/I]

Another search sent me to kcmshell4 to try to run it:

[I]dwagneradm@wstldwagner3:/etc$ kcmshell4 system-config-printer-kde
kcmshell(12317)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "system-config-printer-kde.desktop" not found
kcmshell(12317)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "kcm_system-config-printer-kde.desktop" not found
kcmshell(12317)/kdecore (services) KServiceFactory::findServiceByDesktopPath: "kcmsystem-config-printer-kde.desktop" not found
Could not find module 'system-config-printer-kde'. See kcmshell4 --list for the full list of modules.
[/I]

Trying to run system-config-printer from the command line throws a Python Traceback:

[I]dwagneradm@wstldwagner3:~/Documents$ system-config-printer
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 29, in <module>
    import dbus
  File "/usr/lib/python2.7/dist-packages/dbus/__init__.py", line 103, in <module>
    from dbus._dbus import Bus, SystemBus, SessionBus, StarterBus
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 39, in <module>
    from dbus.bus import BusConnection
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 39, in <module>
    from dbus.connection import Connection
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 37, in <module>
    from dbus.proxies import ProxyObject
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 34, in <module>
    from dbus._expat_introspect_parser import process_introspection_data
  File "/usr/lib/python2.7/dist-packages/dbus/_expat_introspect_parser.py", line 26, in <module>
    from xml.parsers.expat import ParserCreate
  File "/usr/lib/python2.7/xml/parsers/expat.py", line 4, in <module>
    from pyexpat import *
ImportError: /usr/lib/python2.7/lib-dynload/pyexpat.x86_64-linux-gnu.so: undefined symbol: XML_SetHashSalt
[/I]

NO Idea what I should be looking at next, printing in its entirety looks to either be missing or borked on this system.

Help?

(SEE POST 4 FOR SOLUTION)

---

### Post by SeijiSensei on 2015-03-16
I just avoide the distro's printer configuration utilities and use the CUPS web interface instead.  Point your browser to [http://localhost:631/](http://localhost:631/), then follow the links to add the printer.  You'll be prompted to enter your username and your password along the way just as you would if you were using sudo.

---

### Post by Illydth on 2015-03-18
Thanks for that, yes, the cups interface does work.

That said, that might be considered a workaround, and for those less savy that's not exactly the best option...cups interface leaves a LOT to be desired.

What broke in 14.04 to remove the printer setup capability from System Settings?  This is an LTS Release, I'd hate to see "Use CUPS" as the official answer.  As I said I don't even SEE a "system-config-printer-kde" package available any more...that means there's got to be something more to it.

---

### Post by Illydth on 2015-03-18
Partially Fixed.

*** Oracle's Client Installation Breaks Python *** - Expat Library comes from a different place once the oracle 11G Client is installed...and doesn't include the right functions.

[http://ubuntuforums.org/showthread.php?t=2142948](http://ubuntuforums.org/showthread.php?t=2142948)

The important part on my system: 

```

user@system:/etc$ ldd /usr/lib/python2.7/lib-dynload/pyexpat.x86_64-linux-gnu.so
        linux-vdso.so.1 =>  (0x00007fff5ddfe000)
        libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007ff43a83a000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007ff43a475000)
        **libexpat.so.1 => /opt/oracle/product/11.2.0/client_1/lib/libexpat.so.1 (0x00007ff43a343000)**
        /lib64/ld-linux-x86-64.so.2 (0x00007ff43ac8e000)

```

Note that Oracle's 11G Client seems to install it's own libexpat package...and while:

```

user@system:/etc$ strings /lib/x86_64-linux-gnu/libexpat.so.1 | grep XML_SetHashSalt
XML_SetHashSalt

```
Returns the proper function:

```

user@system:/etc$ strings /opt/oracle/product/11.2.0/client_1/lib/libexpat.so.1 | grep XML_SetHashSalt

```
Does not.

I ended up:

```

mv /opt/oracle/product/11.2.0/client_1/lib/libexpat.so.1 /opt/oracle/product/11.2.0/client_1/lib/libexpat.so.1.oracle
ln -s /lib/x86_64-linux-gnu/libexpat.so.1 /opt/oracle/product/11.2.0/client_1/lib/libexpat.so.1

```

This has "system-config-printer" working again when running from the command line.

Now, I'm still missing the config item from System Settings, and system-config-printer-kde is still not a package anymore in 14.04...so not everything is back to normal, but at least there's an option.

Not fixed, better.

---

### Post by Illydth on 2015-03-18
And there it is.  Once I had that fixed, I started checking KDE issues instead of kubuntu issues and came across:

[https://lists.debian.org/debian-qt-kde/2014/07/msg00256.html](https://lists.debian.org/debian-qt-kde/2014/07/msg00256.html)

Which seems to indicate a package called "print-manager" which wasn't installed.  

```

sudo apt-get install print-manager

```

And restart KDE and I get both "Manage Print Jobs" icon on my dock (hidden by the up arrow), a "Printers" Icon in System Settings and an Icon in the KDE Menu (Search "print").

**TO FIX THIS ISSUE:**

1) Verify python works by trying to run "system-config-printer" from the command line.
2) Install "print-manager"
3) Restart KDE.

**TO FIX SYSTEM-CONFIG-PRINTER PYTHON ERROR**

1) First check to see that you have the right packages installed:
dpkg -l | grep libexpat
ii  libexpat1:amd64
dpkg -l | grep libpython2.7-stdlib
ii  libpython2.7-stdlib:amd64

2) If you are getting an error about a missing library or a function not existing do the following:
strings <library> | grep XML_SetHashSalt
XML_SetHashSalt
ldd /usr/lib/python2.7/lib-dynload/pyexpat.x86_64-linux-gnu.so
        linux-vdso.so.1 =>  (0x00007fff5ddfe000)
        libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007ff43a83a000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007ff43a475000)
        libexpat.so.1 => /opt/oracle/product/11.2.0/client_1/lib/libexpat.so.1 (0x00007ff43a343000)
        /lib64/ld-linux-x86-64.so.2 (0x00007ff43ac8e000)

Make sure you are linked against the operating system version of the library in question and NOT a non-standard location's version.

---

### Post by erchamion2 on 2015-09-22
thanks! worked for me!

---

