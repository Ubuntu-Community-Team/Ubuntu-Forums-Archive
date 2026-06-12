---
title: "notify-send not work as CGI script?"
date: 2010-05-27
forum: Desktop Environments
---

### Post by djstava on 2010-05-27
I write a cgi script in python just send a notification command,but that can not work for me.


```
#!/usr/bin/env python
#-*-coding=utf-8-*-

import cgi
import os

print 'Content-Type:text/html\n\n'

os.system("notify-send 'hello'")
```


And 

```

djstava@Gateway:~/test$ notify-send 'hello'

```
is OK.

---

### Post by iponeverything on 2010-05-27
redirect stderr to a file so that you can see if it's trying to tell you something. 

```
os.system("notify-send 'hello' 2>/tmp/notify-error")
```

---

### Post by djstava on 2010-05-27
```

djstava@Gateway:/tmp$ cat notify-error 
libnotify-Message: Unable to get session bus: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.


** (notify-send:4642): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (notify-send:4642): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (notify-send:4642): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed
libnotify-Message: Unable to get session bus: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.


** (notify-send:4642): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (notify-send:4642): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

(notify-send:4642): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

That means notify-send cannot connect current X session?

---

### Post by iponeverything on 2010-05-27
yes.

```
os.system("DISPLAY=:0.0; notify-send 'hello' 2>/tmp/notify-error")
```

---

### Post by djstava on 2010-05-27
```

djstava@Gateway:/tmp$ cat notify-error 
libnotify-Message: Unable to get session bus: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.


** (notify-send:6820): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (notify-send:6820): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (notify-send:6820): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed
libnotify-Message: Unable to get session bus: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.


** (notify-send:6820): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (notify-send:6820): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

(notify-send:6820): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed


```Error remains.

The apache2 default user www-data and my system username is not the same one.Maybe this is the problem.

---

### Post by iponeverything on 2010-05-27
perhaps you can try to setup a sudoer for uid that cgi process is running as that does not require a password to run your notify command as root. Though, I don't know that will work either.. you might also need to duplicate your .Xauthority in /root in addition.

you have to do some experimenting / debugging pin it down.

---

### Post by djstava on 2010-05-27
> **iponeverything said:**
> perhaps you can try to setup a sudoer for uid that cgi process is running as that does not require a password to run your notify command as root. Though, I don't know that will work either.. you might also need to duplicate your .Xauthority in /root in addition.

you have to do some experimenting / debugging pin it down.

I add the line to the /etc/sudoers
```
djstava ALL=(ALL) ALL
```
but that's not take effect,I can't midify the /etc/rc.local when the user djstava login the system.

Add there is no .Xauthority file in the system.
Thanks.

---

### Post by tgalati4 on 2010-05-27
You could try the same in PHP but I think you will run into the same problem.  Apache2 is running as user www-data and notify-send is trying to send to the user's X session.  You don't want to give www-data root privileges that would be bad for security.  

Doing a quick search:

tgalati4@tpad-Gloria7 ~ $ apt-cache search python notify
python-notify - Python bindings for libnotify
bluemindo - really simple but powerful audio player
python-kaa-base - Base Kaa Framework for all Kaa Modules
python-pyinotify - Simple Linux inotify Python bindings
python-pyinotify-doc - Simple Linux inotify Python bindings

So perhaps you can use the older libnotify framework with python.  I'm not sure if there is a notify-osd binding in Python.

You realize that coding specifically using notify-send makes your webpage specific to Linux/Ubuntu?

Windows users would be left in the dark.

---

### Post by djstava on 2010-05-28
> **tgalati4 said:**
> You could try the same in PHP but I think you will run into the same problem.  Apache2 is running as user www-data and notify-send is trying to send to the user's X session.  You don't want to give www-data root privileges that would be bad for security.  

Doing a quick search:

tgalati4@tpad-Gloria7 ~ $ apt-cache search python notify
python-notify - Python bindings for libnotify
bluemindo - really simple but powerful audio player
python-kaa-base - Base Kaa Framework for all Kaa Modules
python-pyinotify - Simple Linux inotify Python bindings
python-pyinotify-doc - Simple Linux inotify Python bindings

So perhaps you can use the older libnotify framework with python.  I'm not sure if there is a notify-osd binding in Python.

You realize that coding specifically using notify-send makes your webpage specific to Linux/Ubuntu?

Windows users would be left in the dark.

Thanks for your reply.
I tried python-notify from [http://www.galago-project.org/downloads.php](http://www.galago-project.org/downloads.php)
```
djstava@Gateway:~/test$ cat /var/www/cgi-bin/test.py 
#!/usr/bin/env python
#-*-coding=utf-8-*-

import cgi
import os

print 'Content-Type:text/html\n\n'

#os.system("DISPLAY=:0.0, notify-send 'hello' 2>/tmp/notify-error")
try:
    import pynotify
    if pynotify.init("cgi script"):
        n = pynotify.Notification("Title", "message")
        n.show()
    else:
        print "There was a problem initializing the pynotify module"
except:
    print "Have not pynotify installed"
```I check the apache2 error.log,same as before.

---

### Post by djstava on 2010-05-31
> **iponeverything said:**
> yes.

```
os.system("DISPLAY=:0.0; notify-send 'hello' 2>/tmp/notify-error")
```

:P,I change the apache2's default user *www-data *to my system user *djstava*,and it works,ONLY need the $DISPLAY.

---

