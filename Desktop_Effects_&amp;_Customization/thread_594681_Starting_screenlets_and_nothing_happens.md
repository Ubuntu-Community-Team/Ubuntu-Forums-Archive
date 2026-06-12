---
title: "Starting screenlets and nothing happens"
date: 2007-10-28
forum: Desktop Effects &amp; Customization
---

### Post by johndoeedgyeft on 2007-10-28
i installed screenlets but when i click screenlets using menu->system->preferences it just says starting screenlets  but nothing happens.

when i wrote screenlets-manager it just says

"Traceback(most recent call last):
 File "/usr/local/share/screenlets-manager/screenets-manager.py" line 23 in
?
        import screenlets
ImportError: No module named screenlets"

(by the way, another question, is there any way of copying text from terminal???)



i searched forums but i couldnt find a solution yet. i am using edgy eft and beryl.


is there anyone who knows the solution to this problem ?

---

### Post by asiersar on 2007-10-28
> **johndoeedgyeft said:**
> 
(by the way, another question, is there any way of copying text from terminal???)


Ctrl+Shift+C

To paste: Ctrl+Shift+V

---

### Post by johndoeedgyeft on 2007-10-28
thx asiersar.

and now the new problem. again it doesnt work but the error code it gives to me has changed (i am still working on it)

LISTED PATH NOT EXISTS: /usr/local/share/screenlets/screenlets-0.0.10
Unable to load 'CopyStack' from /usr/local/share/screenlets/CopyStack: invalid syntax (CopyStackScreenlet.py, line 365) 
Traceback (most recent call last):
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 589, in ?
    app = ScreenletsManager()
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 133, in __init__
    self.load_screenlets()
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 259, in load_screenlets
    info = ScreenletInfo(s, meta['name'], meta['info'], meta['author'], 
TypeError: unsubscriptable object



any help?

---

### Post by chenxing on 2007-10-31
Goto the line 365 of 
/usr/local/share/screenlets/CopyStack/CopyStackScreenlet.py

delete the "()" and it will be ok.

class Tooltip ():
->
class Tooltip:

---

### Post by johndoeedgyeft on 2007-10-31
now it gives this error :(
hlp plzzz


LISTED PATH NOT EXISTS: /usr/local/share/screenlets/screenlets-0.0.10
DAEMON FOUND!
Traceback (most recent call last):
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 589, in ?
    app = ScreenletsManager()
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 135, in __init__
    self.connect_daemon()
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 166, in connect_daemon
    self.handle_screenlet_registered)
  File "/var/lib/python-support/python2.4/dbus/_dbus.py", line 291, in connect_to_signal
    self._obj.connect_to_signal(signal_name, handler_function, dbus_interface, **keywords)
  File "/var/lib/python-support/python2.4/dbus/proxies.py", line 151, in connect_to_signal
    path=self._object_path,
  File "/var/lib/python-support/python2.4/dbus/_dbus.py", line 179, in add_signal_receiver
    named_service = bus_object.GetNameOwner(named_service, dbus_interface='org.freedesktop.DBus')
  File "/var/lib/python-support/python2.4/dbus/proxies.py", line 25, in __call__
    ret = self._proxy_method (*args, **keywords)
  File "/var/lib/python-support/python2.4/dbus/proxies.py", line 102, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)
  File "dbus_bindings.pyx", line 455, in dbus_bindings.Connection.send_with_reply_and_block
dbus_bindings.DBusException: Could not get owner of name 'org.screenlets.ScreenletsDaemon': no such name

---

### Post by chenxing on 2007-11-01
Try to run this first
screenletsd

---

### Post by johndoeedgyeft on 2007-11-01
Screenletsd isn't used for starting screenlets anymore. Please use the new 'screenlets-manager' or start each Screenlet individually from now on.
:(


and when i write screenlets-manager



LISTED PATH NOT EXISTS: /usr/local/share/screenlets/screenlets-0.0.10
DAEMON FOUND!
Traceback (most recent call last):
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 589, in ?
    app = ScreenletsManager()
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 135, in __init__
    self.connect_daemon()
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 166, in connect_daemon
    self.handle_screenlet_registered)
  File "/var/lib/python-support/python2.4/dbus/_dbus.py", line 291, in connect_to_signal
    self._obj.connect_to_signal(signal_name, handler_function, dbus_interface, **keywords)
  File "/var/lib/python-support/python2.4/dbus/proxies.py", line 151, in connect_to_signal
    path=self._object_path,
  File "/var/lib/python-support/python2.4/dbus/_dbus.py", line 179, in add_signal_receiver
    named_service = bus_object.GetNameOwner(named_service, dbus_interface='org.freedesktop.DBus')
  File "/var/lib/python-support/python2.4/dbus/proxies.py", line 25, in __call__
    ret = self._proxy_method (*args, **keywords)
  File "/var/lib/python-support/python2.4/dbus/proxies.py", line 102, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)
  File "dbus_bindings.pyx", line 455, in dbus_bindings.Connection.send_with_reply_and_block
dbus_bindings.DBusException: Could not get owner of name 'org.screenlets.ScreenletsDaemon': no such name

---

### Post by asiersar on 2007-11-02
I'm not an expert on this, but you could try to start the screenlest directly executing the Python scripts.

For example, go to 

```
/usr/local/share/screenlets/Notes
```

double click on it and see if it works.

---

### Post by asiersar on 2007-11-02
Sorry:

double click on "NotesScreenlet.py"...:rolleyes:

---

