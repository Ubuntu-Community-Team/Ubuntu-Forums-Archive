---
title: "Clock, weather etc on desktop?"
date: 2013-11-10
forum: Desktop Environments
---

### Post by Niemil on 2013-11-10
Well, I seen those themes where they've a transparent clock on their desktop, maybe some specs on their computer (like how hot the computer is etc), and also weather.

I googled and found this tutorial: [http://www.ashokgelal.com/2008/09/gmail-weather-beauty-right-on-your-ubuntu-desktop/](http://www.ashokgelal.com/2008/09/gmail-weather-beauty-right-on-your-ubuntu-desktop/)

I been going through it, but nothing happends really at the end when I write conky in the ALT+F2 box that popup.

I am not sure, but is a directory a folder? because I made a folder named scripts and got the files in there.
And I also followed the tutorial exactly how it's written, and no idea why it doesn't work.

Anybody who can help me with this?

---

### Post by ardchoille422 on 2013-11-10
Does Conky not provide a menu entry so you can run it from the standard menu?

---

### Post by Niemil on 2013-11-10
> **ardchoille422 said:**
> Does Conky not provide a menu entry so you can run it from the standard menu?
Not what I know.
I went to the "dash" window and searched for conky, but nothing shows up.

Also on that link, I now tested the one in the "Update 2", but still nothing really appears :/

Also using Ubuntu 12.04 with Gnome, no idea if that can make sense for this to work.

---

### Post by deadflowr on 2013-11-10
conky uses a command to launch.
There is no application icon, unless you make one for it yourself.

The best practice, is to open a terminal and simply type conky. (or conky &)
Do this to see if any errors come up.
ctrl + C will kill it.
If ctrl + C doesn't kill it, try opening another terminal window or tab and run killall conky.

The run command (alt+F2) does the same thing, but if errors happen you won't know it.

---

### Post by Niemil on 2013-11-10
> **deadflowr said:**
> conky uses a command to launch.
There is no application icon, unless you make one for it yourself.

The best practice, is to open a terminal and simply type conky. (or conky &)
Do this to see if any errors come up.
ctrl + C will kill it.
If ctrl + C doesn't kill it, try opening another terminal window or tab and run killall conky.

The run command (alt+F2) does the same thing, but if errors happen you won't know it.

Well, I wrote conky in terminal, and this came up:
```
Conky: desktop window (e00023) is subwindow of root window (2b7)Conky: window type - override
Conky: drawing to created window (0x2c00001)
Conky: drawing to double buffer
/bin/sh: 1: w3m: not found
Traceback (most recent call last):
  File "/home/sozu/.conky_scripts/weathericon.py", line 12, in <module>
    f = open("weathercondition")
IOError: [Errno 2] No such file or directory: 'weathercondition'
/bin/sh: 1: w3m: not found
Traceback (most recent call last):
  File "/home/sozu/.conky_scripts/thermostaticon.py", line 18, in <module>
    f = open("weathertemp")
IOError: [Errno 2] No such file or directory: 'weathertemp'
Conky: curl: no data from server, got HTTP status 404
Traceback (most recent call last):
  File "/home/sozu/.conky_scripts/gmail_parser.py", line 46, in <module>
    f = auth()  # Do auth and then get the feed
  File "/home/sozu/.conky_scripts/gmail_parser.py", line 29, in auth
    f = opener.open(_URL)
  File "/usr/lib/python2.7/urllib.py", line 207, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 450, in open_https
    return self.http_error(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 371, in http_error
    result = method(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 664, in http_error_301
    return self.http_error_302(url, fp, errcode, errmsg, headers, data)
  File "/usr/lib/python2.7/urllib.py", line 634, in http_error_302
    data)
  File "/usr/lib/python2.7/urllib.py", line 660, in redirect_internal
    return self.open(newurl)
  File "/usr/lib/python2.7/urllib.py", line 207, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 450, in open_https
    return self.http_error(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 371, in http_error
    result = method(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 695, in http_error_401
    return getattr(self,name)(url, realm)
  File "/usr/lib/python2.7/urllib.py", line 777, in retry_https_basic_auth
    return self.open(newurl)
  File "/usr/lib/python2.7/urllib.py", line 207, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 450, in open_https
    return self.http_error(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 371, in http_error
    result = method(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 682, in http_error_401
    errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 380, in http_error_default
    raise IOError, ('http error', errcode, errmsg, headers)
IOError: ('http error', 401, 'Unauthorized', <httplib.HTTPMessage instance at 0x2c90098>)
Conky: can't open /sys/class/power_supply/[Bat/uevent: No such file or directory
Conky: can't open /proc/acpi/battery/[Bat/state: No such file or directory
Conky: curl: no data from server, got HTTP status 404
Traceback (most recent call last):
  File "/home/sozu/.conky_scripts/gmail_parser.py", line 46, in <module>
    f = auth()  # Do auth and then get the feed
  File "/home/sozu/.conky_scripts/gmail_parser.py", line 29, in auth
    f = opener.open(_URL)
  File "/usr/lib/python2.7/urllib.py", line 207, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 450, in open_https
    return self.http_error(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 371, in http_error
    result = method(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 664, in http_error_301
    return self.http_error_302(url, fp, errcode, errmsg, headers, data)
  File "/usr/lib/python2.7/urllib.py", line 634, in http_error_302
    data)
  File "/usr/lib/python2.7/urllib.py", line 660, in redirect_internal
    return self.open(newurl)
  File "/usr/lib/python2.7/urllib.py", line 207, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 450, in open_https
    return self.http_error(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 371, in http_error
    result = method(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 695, in http_error_401
    return getattr(self,name)(url, realm)
  File "/usr/lib/python2.7/urllib.py", line 777, in retry_https_basic_auth
    return self.open(newurl)
  File "/usr/lib/python2.7/urllib.py", line 207, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.7/urllib.py", line 450, in open_https
    return self.http_error(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 371, in http_error
    result = method(url, fp, errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 682, in http_error_401
    errcode, errmsg, headers)
  File "/usr/lib/python2.7/urllib.py", line 380, in http_error_default
    raise IOError, ('http error', errcode, errmsg, headers)
IOError: ('http error', 401, 'Unauthorized', <httplib.HTTPMessage instance at 0x20c0098>)
Conky: can't open /proc/acpi/battery/[Bat/state: No such file or directory
^CConky: received SIGINT or SIGTERM to terminate. bye!

```
Well, it seems to give lots of errors?

The CTRL+C did work, it killed conky in terminal.
Then tried to do that ALT+F2 and wrote conky but nothing appears on desktop still.

[edit]
I read the error from beginning, and first error it says that weathercondition file doesn't exist, when it actually do exist in same folder as the conky.sh does.
Though the weathercondition file seems to be completely empty.

---

### Post by deadflowr on 2013-11-10
You'll probably get more help in this thread
[http://ubuntuforums.org/showthread.php?t=281865&page=2242](http://ubuntuforums.org/showthread.php?t=281865&page=2242)

The fellows and ladies in there are conky geniuses.

---

