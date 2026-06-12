---
title: "X-Chat plugin for Muine doesn't work"
date: 2005-09-15
forum: Desktop Environments
---

### Post by Imek on 2005-09-15
I've been trying to get the now playing script for Muine in X-Chat working, but with no luck so far. I installed the one from [here](http://scripts.xchat.org/cgi-bin/disp), but when I try to run it it gives me this error:

Traceback (most recent call last):
   File "/home/imek/.xchat2/m_announce.py", line 38, in m_announce
     song = player.GetCurrentSong().split('\n')
   File "/usr/lib/python2.4/site-packages/dbus.py", line 219, in __call__
     reply_message = self._connection.send_with_reply_and_block(message, 5000)
   File "dbus_bindings.pyx", line 578, in dbus_bindings.Connection.send_with_reply_and_block
 dbus_bindings.DBusException: Service "org.gnome.Muine" does not exist

There is a file called org.gnome.Muine.service in /usr/lib/dbus-1.0/services, and I have all of the latest Muine installed (I have the backports in my repositories). And yes, Muine is definitely running. Anyone know why this could be happening?

---

