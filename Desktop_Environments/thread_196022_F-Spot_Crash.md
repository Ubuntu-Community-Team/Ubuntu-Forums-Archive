---
title: "F-Spot Crash"
date: 2006-06-13
forum: Desktop Environments
---

### Post by vvlist on 2006-06-13
This is the output:
> An unhandled exception was thrown: No reply within specified time

in <0x0011c> DBus.Message:SendWithReplyAndBlock ()
in <0x00062> FSpot.Core.Proxy:Organize ()
in <0x00530> FSpot.Driver:Main (System.String[] args)
.NET Version: 1.1.4322.2032

Assembly Version Information:

Mono.CompilerServices.SymbolWriter (1.0.5000.0)
DBusProxy (0.0.0.0)
System.Data (1.0.5000.0)
Mono.Data.SqliteClient (1.0.5000.0)
gdk-sharp (2.8.0.0)
Mono.Posix (1.0.5000.0)
gnome-vfs-sharp (2.8.0.0)
dbus-sharp (0.60.0.0)
System (1.0.5000.0)
atk-sharp (2.8.0.0)
gtk-sharp (2.8.0.0)
glib-sharp (2.8.0.0)
gnome-sharp (2.8.0.0)
f-spot (0.0.0.0)
mscorlib (1.0.5000.0)

Platform Information: Linux 2.6.15-23-686 i686 unknown GNU/Linux

Disribution Information:

[/etc/debian_version]
testing/unstable

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06 LTS"



Has this happened to anybody else?
EDIT: This has been fixed.

---

