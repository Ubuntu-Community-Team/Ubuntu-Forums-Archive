---
title: "M64Py epic fail."
date: 2018-10-22
forum: Emulators
---

### Post by nerv-agent on 2018-10-22
I managed to install the latest Mupen64Plus, and am trying to get the front-end M64Py to work. Instead, I get this:

```
Frontend: INFO: No OpenGL_accelerate module loaded: No module named 'OpenGL_accelerate'
Frontend: INFO: Unable to load registered array format handler numeric:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/OpenGL/arrays/numeric.py", line 13, in <module>
    import Numeric
ImportError: No module named 'Numeric'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/OpenGL/arrays/formathandler.py", line 35, in loadPlugin
    plugin_class = entrypoint.load()
  File "/usr/lib/python3/dist-packages/OpenGL/plugins.py", line 14, in load
    return importByName( self.import_path )
  File "/usr/lib/python3/dist-packages/OpenGL/plugins.py", line 28, in importByName
    module = __import__( ".".join(moduleName), {}, {}, moduleName)
  File "/usr/lib/python3/dist-packages/OpenGL/arrays/numeric.py", line 15, in <module>
    raise ImportError( """No Numeric module present: %s"""%(err))
ImportError: No Numeric module present: No module named 'Numeric'

process 3118: arguments to dbus_connection_unref() were incorrect, assertion "connection->generation == _dbus_current_generation" failed in file ../../dbus/dbus-connection.c line 2822.
This is normally a bug in some application using the D-Bus library.
process 3118: arguments to dbus_connection_unref() were incorrect, assertion "connection->generation == _dbus_current_generation" failed in file ../../dbus/dbus-connection.c line 2822.
This is normally a bug in some application using the D-Bus library.
process 3118: arguments to dbus_connection_unref() were incorrect, assertion "connection->generation == _dbus_current_generation" failed in file ../../dbus/dbus-connection.c line 2822.
This is normally a bug in some application using the D-Bus library.
process 3118: arguments to dbus_connection_unref() were incorrect, assertion "connection->generation == _dbus_current_generation" failed in file ../../dbus/dbus-connection.c line 2822.
This is normally a bug in some application using the D-Bus library.
process 3118: arguments to dbus_connection_unref() were incorrect, assertion "connection->generation == _dbus_current_generation" failed in file ../../dbus/dbus-connection.c line 2822.
This is normally a bug in some application using the D-Bus library.
process 3118: arguments to dbus_connection_unref() were incorrect, assertion "connection->generation == _dbus_current_generation" failed in file ../../dbus/dbus-connection.c line 2822.
This is normally a bug in some application using the D-Bus library.
process 3118: arguments to dbus_connection_unref() were incorrect, assertion "connection->generation == _dbus_current_generation" failed in file ../../dbus/dbus-connection.c line 2822.
This is normally a bug in some application using the D-Bus library.
process 3118: arguments to dbus_connection_unref() were incorrect, assertion "connection->generation == _dbus_current_generation" failed in file ../../dbus/dbus-connection.c line 2822.
This is normally a bug in some application using the D-Bus library.
Frontend: INFO: attached to library 'Mupen64Plus Core' version 2.5.0
Frontend: INFO: includes support for Dynamic Recompiler.
Frontend: INFO: video extension enabled
Frontend: DEBUG: plugin_load_try()
Traceback (most recent call last):
  File "/usr/share/m64py/m64py/core/core.py", line 214, in plugin_load_try
    plugin_handle = C.cdll.LoadLibrary(plugin_path)
  File "/usr/lib/python3.5/ctypes/__init__.py", line 425, in LoadLibrary
    return self._dlltype(name)
  File "/usr/lib/python3.5/ctypes/__init__.py", line 347, in __init__
    self._handle = _dlopen(self._name, mode)
OSError: libboost_filesystem.so.1.46.1: cannot open shared object file: No such file or directory

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/games/m64py", line 58, in <module>
    window = MainWindow((opts, args))
  File "/usr/share/m64py/m64py/frontend/mainwindow.py", line 90, in __init__
    self.worker.init()
  File "/usr/share/m64py/m64py/frontend/worker.py", line 55, in init
    self.plugins_load()
  File "/usr/share/m64py/m64py/frontend/worker.py", line 138, in plugins_load
    self.core.plugin_load_try(plugin_path)
  File "/usr/share/m64py/m64py/core/core.py", line 223, in plugin_load_try
    plugin_path = plugin_path.decode('ascii', 'ignore')
AttributeError: 'str' object has no attribute 'decode'
process 3118: arguments to dbus_connection_close() were incorrect, assertion "connection->generation == _dbus_current_generation" failed in file ../../dbus/dbus-connection.c line 2935.
This is normally a bug in some application using the D-Bus library.
process 3118: arguments to dbus_message_ref() were incorrect, assertion "message->generation == _dbus_current_generation" failed in file ../../dbus/dbus-message.c line 1672.
This is normally a bug in some application using the D-Bus library.
process 3118: arguments to dbus_message_ref() were incorrect, assertion "message->generation == _dbus_current_generation" failed in file ../../dbus/dbus-message.c line 1672.
This is normally a bug in some application using the D-Bus library.
process 3118: arguments to dbus_message_ref() were incorrect, assertion "message->generation == _dbus_current_generation" failed in file ../../dbus/dbus-message.c line 1672.
This is normally a bug in some application using the D-Bus library.
process 3118: arguments to dbus_message_iter_init() were incorrect, assertion "message != NULL" failed in file ../../dbus/dbus-message.c line 2071.
This is normally a bug in some application using the D-Bus library.
process 3118: arguments to dbus_message_unref() were incorrect, assertion "message->generation == _dbus_current_generation" failed in file ../../dbus/dbus-message.c line 1695.
This is normally a bug in some application using the D-Bus library.
process 3118: arguments to dbus_message_unref() were incorrect, assertion "message->generation == _dbus_current_generation" failed in file ../../dbus/dbus-message.c line 1695.
This is normally a bug in some application using the D-Bus library.
process 3118: arguments to dbus_connection_unref() were incorrect, assertion "connection->generation == _dbus_current_generation" failed in file ../../dbus/dbus-connection.c line 2822.
This is normally a bug in some application using the D-Bus library.
process 3118: arguments to dbus_message_unref() were incorrect, assertion "message->generation == _dbus_current_generation" failed in file ../../dbus/dbus-message.c line 1695.
This is normally a bug in some application using the D-Bus library.
process 3118: arguments to dbus_connection_unref() were incorrect, assertion "connection->generation == _dbus_current_generation" failed in file ../../dbus/dbus-connection.c line 2822.
This is normally a bug in some application using the D-Bus library.
process 3118: arguments to dbus_connection_unref() were incorrect, assertion "connection->generation == _dbus_current_generation" failed in file ../../dbus/dbus-connection.c line 2822.
This is normally a bug in some application using the D-Bus library.

```

And yes, I already know about the front-end Mupen64Plus-QT which is also epic fail and a waste of time because they didn't include controller settings.

---

### Post by deadflowr on 2018-10-22
*Thread moved to **Emulators** *

Which version of Ubuntu?

---

### Post by nerv-agent on 2018-10-24
Ubuntu 16.04 LTS

---

### Post by deadflowr on 2018-10-24
running on 16.04 I'm not seeing the libboost-filesystem OSError
So what libboost package is installed
in a terminal run
```
dpkg -l | grep libboost
```
I have 1.58.0 which is the latest on 16.04.

Not sure if that's the issue at hand.
I do get the dbus spam, so it shouldn't be related to that at least.

---

### Post by nerv-agent on 2018-10-28
This is what it outputs:

```
dpkg -l | grep libboost
ii  libboost-date-time1.58.0:amd64                 1.58.0+dfsg-5ubuntu3.1                                     amd64        set of date-time libraries based on generic programming concepts
ii  libboost-filesystem1.58.0:amd64                1.58.0+dfsg-5ubuntu3.1                                     amd64        filesystem operations (portable paths, iteration over directories, etc) in C++
ii  libboost-filesystem1.58.0:i386                 1.58.0+dfsg-5ubuntu3.1                                     i386         filesystem operations (portable paths, iteration over directories, etc) in C++
ii  libboost-iostreams1.58.0:amd64                 1.58.0+dfsg-5ubuntu3.1                                     amd64        Boost.Iostreams Library
ii  libboost-log1.58.0                             1.58.0+dfsg-5ubuntu3.1                                     amd64        C++ logging library
ii  libboost-regex1.58.0:amd64                     1.58.0+dfsg-5ubuntu3.1                                     amd64        regular expression library for C++
ii  libboost-system1.58.0:amd64                    1.58.0+dfsg-5ubuntu3.1                                     amd64        Operating system (e.g. diagnostics support) library
ii  libboost-system1.58.0:i386                     1.58.0+dfsg-5ubuntu3.1                                     i386         Operating system (e.g. diagnostics support) library
ii  libboost-thread1.58.0:amd64                    1.58.0+dfsg-5ubuntu3.1                                     amd64        portable C++ multi-threading


```

---

### Post by deadflowr on 2018-10-29
I think the next step is how was it installed? (I mean m64py, to be clear)
(As well as how did you installed the latest mupen64plus)

---

### Post by nerv-agent on 2018-10-30
I installed the latest mupen64plus version 2.5.  As for M64Py, I ran the debian that was posted at this url:  [https://sourceforge.net/projects/m64py/files/m64py-0.2.4/m64py_0.2.4-0_all.deb/download](https://sourceforge.net/projects/m64py/files/m64py-0.2.4/m64py_0.2.4-0_all.deb/download)

---

