---
title: "Dockbarx 0.43 not working"
date: 2011-02-24
forum: Desktop Environments
---

### Post by lolwhites on 2011-02-24
I few weeks ago DockbarX upgraded tyo 0.43, and since then it hasn't worked at all; not just no window previews, but no icons for open applications - absolutely nothing.

This also applies when there's an applet in a panel, not just AWN. I've been through the forums, tried going into Compiz Settings and unchecking, then rechecking *KDE Compatibility* etc, but it does nothing.

Edot - installed awn-applet-dockbarx and gnome-dockbarx-applet from Synaptic but it doesn't help.

---

### Post by M7S on 2011-02-24
Do you have any errors in the log? ~/.dockbarx/log/dockbarx.log

---

### Post by lolwhites on 2011-02-24
The following message keeps coming up:

> ERROR	| 2011-02-19 07:48:10,199	|     self.themes = self.find_themes()
ERROR	| 2011-02-19 07:48:10,199	|   File "/usr/lib/pymodules/python2.6/dockbarx/theme.py", line 159, in find_themes
ERROR	| 2011-02-19 07:48:10,199	|     logger.exeption("Error loading theme from %s"%theme_path)
ERROR	| 2011-02-19 07:48:10,199	| AttributeError: Logger instance has no attribute 'exeption'

---

### Post by M7S on 2011-02-24
I made a stupid spelling error again. :S

Edit line 159 in file /usr/lib/pymodules/python2.6/dockbarx/theme.py so that it says logger.exception instead of logger.exeption

```
sudo gedit /usr/lib/pymodules/python2.6/dockbarx/theme.py
```

Then try again and send me the new error log.

---

### Post by lolwhites on 2011-02-24
Thanks, it works now. :)

---

### Post by M7S on 2011-02-24
I still want the log, even if DockbarX doesn't hang because of the bug anymore.

---

### Post by lolwhites on 2011-02-24
Here's the most recent one:

> INFO	| 2011-02-23 17:03:49,046	| DockbarX 0.43
INFO	| 2011-02-23 17:03:49,047	| DockbarX init
INFO	| 2011-02-23 17:03:57,666	| DockbarX reload
ERROR	| 2011-02-23 17:03:57,733	| Traceback (most recent call last):
ERROR	| 2011-02-23 17:03:57,733	|   File "/usr/lib/pymodules/python2.6/dockbarx/dockbar.py", line 237, in __reload_on_realized
ERROR	| 2011-02-23 17:03:57,793	|     self.reload()
ERROR	| 2011-02-23 17:03:57,794	|   File "/usr/lib/pymodules/python2.6/dockbarx/dockbar.py", line 281, in reload
ERROR	| 2011-02-23 17:03:57,794	|     self.theme = Theme()
ERROR	| 2011-02-23 17:03:57,794	|   File "/usr/lib/pymodules/python2.6/dockbarx/theme.py", line 118, in __init__
ERROR	| 2011-02-23 17:03:57,953	|     self.on_theme_changed()
ERROR	| 2011-02-23 17:03:58,209	|   File "/usr/lib/pymodules/python2.6/dockbarx/theme.py", line 121, in on_theme_changed
ERROR	| 2011-02-23 17:03:58,210	|     self.themes = self.find_themes()
ERROR	| 2011-02-23 17:03:58,210	|   File "/usr/lib/pymodules/python2.6/dockbarx/theme.py", line 159, in find_themes
ERROR	| 2011-02-23 17:03:58,210	|     logger.exeption("Error loading theme from %s"%theme_path)
ERROR	| 2011-02-23 17:03:58,211	| AttributeError: Logger instance has no attribute 'exeption'
INFO	| 2011-02-23 17:03:58,299	| DockbarX 0.43
INFO	| 2011-02-23 17:03:58,299	| DockbarX init
INFO	| 2011-02-23 17:03:58,663	| DockbarX reload
ERROR	| 2011-02-23 17:03:58,665	| Traceback (most recent call last):
ERROR	| 2011-02-23 17:03:58,665	|   File "/usr/lib/pymodules/python2.6/dockbarx/dockbar.py", line 237, in __reload_on_realized
ERROR	| 2011-02-23 17:03:58,666	|     self.reload()
ERROR	| 2011-02-23 17:03:58,666	|   File "/usr/lib/pymodules/python2.6/dockbarx/dockbar.py", line 281, in reload
ERROR	| 2011-02-23 17:03:58,666	|     self.theme = Theme()
ERROR	| 2011-02-23 17:03:58,666	|   File "/usr/lib/pymodules/python2.6/dockbarx/theme.py", line 118, in __init__
ERROR	| 2011-02-23 17:03:58,666	|     self.on_theme_changed()
ERROR	| 2011-02-23 17:03:58,667	|   File "/usr/lib/pymodules/python2.6/dockbarx/theme.py", line 121, in on_theme_changed
ERROR	| 2011-02-23 17:03:58,667	|     self.themes = self.find_themes()
ERROR	| 2011-02-23 17:03:58,667	|   File "/usr/lib/pymodules/python2.6/dockbarx/theme.py", line 159, in find_themes
ERROR	| 2011-02-23 17:03:58,667	|     logger.exeption("Error loading theme from %s"%theme_path)
ERROR	| 2011-02-23 17:03:58,667	| AttributeError: Logger instance has no attribute 'exeption'

---

### Post by M7S on 2011-02-25
Sorry, I meant the new log, after the program started working again. It should show some error still.

---

### Post by lolwhites on 2011-02-25
Here's the most recent log I have, from today:
> INFO	| 2011-02-24 10:23:07,532	| DockbarX 0.43
INFO	| 2011-02-24 10:23:07,532	| DockbarX init
INFO	| 2011-02-24 10:23:08,316	| DockbarX reload
ERROR	| 2011-02-24 10:23:08,577	| Traceback (most recent call last):
ERROR	| 2011-02-24 10:23:08,577	|   File "/usr/lib/pymodules/python2.6/dockbarx/dockbar.py", line 237, in __reload_on_realized
ERROR	| 2011-02-24 10:23:08,577	|     self.reload()
ERROR	| 2011-02-24 10:23:08,577	|   File "/usr/lib/pymodules/python2.6/dockbarx/dockbar.py", line 281, in reload
ERROR	| 2011-02-24 10:23:08,578	|     self.theme = Theme()
ERROR	| 2011-02-24 10:23:08,578	|   File "/usr/lib/pymodules/python2.6/dockbarx/theme.py", line 118, in __init__
ERROR	| 2011-02-24 10:23:08,578	|     self.on_theme_changed()
ERROR	| 2011-02-24 10:23:08,578	|   File "/usr/lib/pymodules/python2.6/dockbarx/theme.py", line 121, in on_theme_changed
ERROR	| 2011-02-24 10:23:08,578	|     self.themes = self.find_themes()
ERROR	| 2011-02-24 10:23:08,578	|   File "/usr/lib/pymodules/python2.6/dockbarx/theme.py", line 159, in find_themes
ERROR	| 2011-02-24 10:23:08,579	|     logger.exeption("Error loading theme from %s"%theme_path)
ERROR	| 2011-02-24 10:23:08,579	| AttributeError: Logger instance has no attribute 'exeption'
INFO	| 2011-02-24 10:23:09,009	| DockbarX 0.43
INFO	| 2011-02-24 10:23:09,009	| DockbarX init
INFO	| 2011-02-24 10:23:09,736	| DockbarX reload
ERROR	| 2011-02-24 10:23:10,434	| Traceback (most recent call last):
ERROR	| 2011-02-24 10:23:10,434	|   File "/usr/lib/pymodules/python2.6/dockbarx/dockbar.py", line 237, in __reload_on_realized
ERROR	| 2011-02-24 10:23:10,435	|     self.reload()
ERROR	| 2011-02-24 10:23:10,435	|   File "/usr/lib/pymodules/python2.6/dockbarx/dockbar.py", line 281, in reload
ERROR	| 2011-02-24 10:23:10,435	|     self.theme = Theme()
ERROR	| 2011-02-24 10:23:10,435	|   File "/usr/lib/pymodules/python2.6/dockbarx/theme.py", line 118, in __init__
ERROR	| 2011-02-24 10:23:10,435	|     self.on_theme_changed()
ERROR	| 2011-02-24 10:23:10,435	|   File "/usr/lib/pymodules/python2.6/dockbarx/theme.py", line 121, in on_theme_changed
ERROR	| 2011-02-24 10:23:10,436	|     self.themes = self.find_themes()
ERROR	| 2011-02-24 10:23:10,436	|   File "/usr/lib/pymodules/python2.6/dockbarx/theme.py", line 159, in find_themes
ERROR	| 2011-02-24 10:23:10,436	|     logger.exeption("Error loading theme from %s"%theme_path)
ERROR	| 2011-02-24 10:23:10,436	| AttributeError: Logger instance has no attribute 'exeption'

---

### Post by M7S on 2011-02-25
I'm confused, didn't you change that exeption -> exception thing to get it working?

---

### Post by lolwhites on 2011-02-25
Yes, I did. But the dates and times from that last log are from yesterday morning, before I made the change.

---

### Post by lolwhites on 2011-02-25
Is this what you're looking for?

> INFO	| 2011-02-25 07:31:06,018	| DockbarX 0.43
INFO	| 2011-02-25 07:31:06,018	| DockbarX init
INFO	| 2011-02-25 07:31:07,409	| DockbarX reload
ERROR	| 2011-02-25 07:31:07,411	| Error loading theme from /usr/share/dockbarx/themes/patch.tar.gz
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dockbarx/theme.py", line 157, in find_themes
    name = self.check(theme_path)
  File "/usr/lib/pymodules/python2.6/dockbarx/theme.py", line 246, in check
    config = tar.extractfile("config")
  File "/usr/lib/python2.6/tarfile.py", line 2101, in extractfile
    tarinfo = self.getmember(member)
  File "/usr/lib/python2.6/tarfile.py", line 1789, in getmember
    raise KeyError("filename %r not found" % name)
KeyError: "filename 'config' not found"
ERROR	| 2011-02-25 07:31:07,642	| Error loading theme from /usr/share/dockbarx/themes/gspcav1-20071224.tar.gz
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dockbarx/theme.py", line 157, in find_themes
    name = self.check(theme_path)
  File "/usr/lib/pymodules/python2.6/dockbarx/theme.py", line 246, in check
    config = tar.extractfile("config")
  File "/usr/lib/python2.6/tarfile.py", line 2101, in extractfile
    tarinfo = self.getmember(member)
  File "/usr/lib/python2.6/tarfile.py", line 1789, in getmember
    raise KeyError("filename %r not found" % name)
KeyError: "filename 'config' not found"
ERROR	| 2011-02-25 07:31:07,808	| Error loading theme from /usr/share/dockbarx/themes/colorizeme-shiki-0.2.tar.gz
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dockbarx/theme.py", line 157, in find_themes
    name = self.check(theme_path)
  File "/usr/lib/pymodules/python2.6/dockbarx/theme.py", line 246, in check
    config = tar.extractfile("config")
  File "/usr/lib/python2.6/tarfile.py", line 2101, in extractfile
    tarinfo = self.getmember(member)
  File "/usr/lib/python2.6/tarfile.py", line 1789, in getmember
    raise KeyError("filename %r not found" % name)
KeyError: "filename 'config' not found"
ERROR	| 2011-02-25 07:31:08,419	| Error loading theme from /usr/share/dockbarx/themes/pdfmod-0.5.tar.gz
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dockbarx/theme.py", line 157, in find_themes
    name = self.check(theme_path)
  File "/usr/lib/pymodules/python2.6/dockbarx/theme.py", line 246, in check
    config = tar.extractfile("config")
  File "/usr/lib/python2.6/tarfile.py", line 2101, in extractfile
    tarinfo = self.getmember(member)
  File "/usr/lib/python2.6/tarfile.py", line 1789, in getmember
    raise KeyError("filename %r not found" % name)
KeyError: "filename 'config' not found"
ERROR	| 2011-02-25 07:31:08,453	| Error loading theme from /usr/share/dockbarx/themes/gist74192-51ad0e1be0766007caca1d21ea1abdb2b3ac3e7e.tar.gz
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dockbarx/theme.py", line 157, in find_themes
    name = self.check(theme_path)
  File "/usr/lib/pymodules/python2.6/dockbarx/theme.py", line 246, in check
    config = tar.extractfile("config")
  File "/usr/lib/python2.6/tarfile.py", line 2101, in extractfile
    tarinfo = self.getmember(member)
  File "/usr/lib/python2.6/tarfile.py", line 1789, in getmember
    raise KeyError("filename %r not found" % name)
KeyError: "filename 'config' not found"
DEBUG	| 2011-02-25 07:43:20,237	| Opened window matched with gio app on id: nautilus
DEBUG	| 2011-02-25 07:44:09,767	| Opened window matched with gio app on id: google-chrome
DEBUG	| 2011-02-25 08:14:50,395	| Opened window matched with gio app on id: google-chrome
DEBUG	| 2011-02-25 08:59:52,498	| Opened window matched with gio app on longname: exe
DEBUG	| 2011-02-25 09:18:26,237	| Opened window matched with gio app on id: google-chrome
DEBUG	| 2011-02-25 09:18:41,498	| Opened window matched with gio app on id: virtualbox
DEBUG	| 2011-02-25 10:13:06,213	| Opened window matched with gio app on id: google-chrome
DEBUG	| 2011-02-25 10:25:02,175	| Opened window matched with gio app on id: google-chrome
DEBUG	| 2011-02-25 10:44:43,857	| Opened window matched with gio app on id: nautilus
DEBUG	| 2011-02-25 10:45:23,847	| Opened window matched with gio app on id: gedit
DEBUG	| 2011-02-25 11:32:57,768	| Opened window matched with gio app on id: google-chrome
DEBUG	| 2011-02-25 12:06:42,976	| Opened window matched with gio app on id: google-chrome
DEBUG	| 2011-02-25 12:06:50,149	| Opened window matched with gio app on id: cloudsn
DEBUG	| 2011-02-25 12:33:00,843	| Opened window matched with gio app on id: google-chrome
DEBUG	| 2011-02-25 12:33:11,421	| Opened window matched with gio app on id: banshee-1
DEBUG	| 2011-02-25 12:39:46,396	| Opened window matched with gio app on id: gmailwatcher
DEBUG	| 2011-02-25 13:28:32,257	| Opened window matched with gio app on id: google-chrome
DEBUG	| 2011-02-25 13:30:06,439	| Opened window matched with gio app on id: gmailwatcher
DEBUG	| 2011-02-25 15:21:55,828	| Opened window matched with gio app on id: google-chrome
DEBUG	| 2011-02-25 15:26:38,483	| Opened window matched with gio app on id: google-chrome
DEBUG	| 2011-02-25 15:29:45,734	| Opened window matched with gio app on id: nautilus
DEBUG	| 2011-02-25 15:30:00,001	| Opened window matched with gio app on id: gnumeric
DEBUG	| 2011-02-25 15:40:05,394	| Opened window matched with gio app on id: gmailwatcher
DEBUG	| 2011-02-25 15:41:27,906	| Opened window matched with gio app on id: libreoffice-calc
DEBUG	| 2011-02-25 15:42:27,420	| Opened window matched with gio app on id: libreoffice-writer
DEBUG	| 2011-02-25 15:42:30,026	| Opened window matched with gio app on id: google-chrome
DEBUG	| 2011-02-25 15:57:42,647	| Opened window matched with gio app on id: google-chrome
DEBUG	| 2011-02-25 16:21:28,193	| Opened window matched with gio app on id: gmailwatcher
DEBUG	| 2011-02-25 16:23:27,069	| Opened window matched with gio app on id: google-chrome
DEBUG	| 2011-02-25 16:40:28,332	| Opened window matched with gio app on id: google-chrome
DEBUG	| 2011-02-25 17:32:10,527	| Opened window matched with gio app on id: google-chrome
DEBUG	| 2011-02-25 17:51:29,385	| Opened window matched with gio app on id: google-chrome
DEBUG	| 2011-02-25 17:57:58,547	| Opened window matched with gio app on id: google-chrome
DEBUG	| 2011-02-25 18:14:42,295	| Opened window matched with gio app on id: google-chrome
DEBUG	| 2011-02-25 18:36:56,060	| Opened window matched with gio app on id: nautilus
DEBUG	| 2011-02-25 18:37:06,238	| Opened window matched with gio app on id: eog
DEBUG	| 2011-02-25 18:38:05,768	| Opened window matched with gio app on id: totem
DEBUG	| 2011-02-25 18:38:21,602	| Opened window matched with gio app on id: totem
DEBUG	| 2011-02-25 18:38:44,559	| Opened window matched with gio app on id: totem
DEBUG	| 2011-02-25 18:39:14,320	| Opened window matched with gio app on id: totem
DEBUG	| 2011-02-25 18:39:44,050	| Opened window matched with gio app on id: totem
DEBUG	| 2011-02-25 18:40:26,473	| Opened window matched with gio app on id: totem
DEBUG	| 2011-02-25 18:40:57,628	| Opened window matched with gio app on id: totem
DEBUG	| 2011-02-25 18:41:06,535	| Opened window matched with gio app on id: totem
DEBUG	| 2011-02-25 18:41:37,087	| Opened window matched with gio app on id: totem
DEBUG	| 2011-02-25 18:42:50,716	| Opened window matched with gio app on id: totem
DEBUG	| 2011-02-25 18:44:56,185	| Opened window matched with gio app on id: eog
DEBUG	| 2011-02-25 20:21:35,507	| Opened window matched with gio app on id: gnome-terminal
DEBUG	| 2011-02-25 20:21:48,450	| Opened window matched with gio app on id: gedit
DEBUG	| 2011-02-25 20:30:37,007	| Opened window matched with gio app on id: vlc
DEBUG	| 2011-02-25 20:31:09,505	| Opened window matched with gio app on id: gmailwatcher
DEBUG	| 2011-02-25 21:03:00,211	| Opened window matched with gio app on id: nautilus
DEBUG	| 2011-02-25 21:03:12,182	| Opened window matched with gio app on id: evince
DEBUG	| 2011-02-25 21:33:06,059	| Opened window matched with gio app on id: nautilus
DEBUG	| 2011-02-25 21:33:17,442	| Opened window matched with gio app on id: gedit
DEBUG	| 2011-02-25 21:33:36,104	| Opened window matched with gio app on id: google-chrome

---

### Post by M7S on 2011-02-26
That's it, yes. You have some really wierd files in /usr/share/dockbarx/themes/ I wonder where they came from. Did you install from dockbarx ppa or from webupd8 ppa or manually? I just want to make sure there are no wierd things going on in any of the dockbarx deb files. If you think you moved those files there yourself, then it's all ok.

---

### Post by lolwhites on 2011-02-26
I think it was the webupd8 one.

---

### Post by M7S on 2011-02-26
Thanks, and you haven't put any files in the folder?

---

### Post by lolwhites on 2011-02-26
I've added a few themes, and am currently using PabloGlass.

---

### Post by M7S on 2011-02-26
So it could be that you accidentally have put those files mentioned in your there (patch.tar.gz, gspcav1-20071224.tar.gz and so on)?

---

### Post by lolwhites on 2011-02-26
Possibly, but I didn't add the files manually, I installed them via the Preferences dialogue box.

---

