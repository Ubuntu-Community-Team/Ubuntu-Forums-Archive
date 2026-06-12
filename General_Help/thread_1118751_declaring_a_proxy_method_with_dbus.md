---
title: "declaring a proxy method with dbus"
date: 2009-04-07
forum: General Help
---

### Post by peter c. on 2009-04-07
I'm trying to test the glib bindings of dbus by getting a C program to call a simple method from another C program. 

I've been following online tutorials for this, and (I think) I've understood the general principle and how to write the code to call the method on the 'client' side, but I can't find a clear explanation of how to set up a method on the 'server' side that can be called across the bus daemon. 

If anyone can help point me in the right direction I would be really grateful!


Here are some of the sites I've looked at so far:
[http://dbus.freedesktop.org/doc/dbus-tutorial.html](http://dbus.freedesktop.org/doc/dbus-tutorial.html)
[http://dbus.freedesktop.org/doc/dbus-glib/index.html](http://dbus.freedesktop.org/doc/dbus-glib/index.html)
[http://www.ibm.com/developerworks/linux/library/l-dbus.html](http://www.ibm.com/developerworks/linux/library/l-dbus.html)

---

### Post by Brucevdk on 2009-04-17
As I'm too lazy to actually figure out how to do this in C maybe an example in Python will help you:

Service:
```

import gobject
import dbus
import dbus.service
import dbus.mainloop.glib

INTERFACE = "org.ubuntuforums.peter.Service"
OBJECT_PATH = "/org/ubuntuforums/peter/Service"
SERVICE = "org.ubuntuforums.peter.Service"

class Service(dbus.service.Object):
    
    def __init__(self, connection):
        dbus.service.Object.__init__(self, connection, OBJECT_PATH)
        
    @dbus.service.method(INTERFACE)
    def SomeMethod(self):
        # TODO: Might want to do something here...
        pass
    
dbus.mainloop.glib.DBusGMainLoop(set_as_default=True)
session_bus = dbus.SessionBus()
name = dbus.service.BusName(SERVICE, session_bus) 
service = Service(session_bus)
mainloop = gobject.MainLoop()
mainloop.run()

```

Client:
```

import dbus

INTERFACE = "org.ubuntuforums.peter.Service"
OBJECT_PATH = "/org/ubuntuforums/peter/Service"
SERVICE = "org.ubuntuforums.peter.Service"

session_bus = dbus.SessionBus()
dbus_service = session_bus.get_object(SERVICE, OBJECT_PATH)
dbus_service.SomeMethod()


```

---

### Post by peter c. on 2009-05-06
Hey, I have realised that part of the problem was that I wasn't familiar with g-object, so have had to spend some time getting my head around that. 
Many thanks for this example code though, will see what I can make of translating it across to C.

---

