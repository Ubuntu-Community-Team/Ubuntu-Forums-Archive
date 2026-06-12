---
title: "Question mark instead of Firefox icon in Launcher"
date: 2013-03-12
forum: Desktop Environments
---

### Post by kkkkdddd on 2013-03-12
I am using Ubuntu 12.04 which was upgraded from 10.04 about month ago.
Some time after an upgrade the Firefox icon in the Launcher changed into question mark.

```
/usr/share/applications$ ls -l|grep firefox
-rw-r--r-- 1 root root  7902 mar  7 13:28 firefox.desktop
```

```
/usr/share/pixmaps$ ls -l|grep firefox
lrwxrwxrwx  1 root root    38 mar  7 16:52 firefox.png -> ../../lib/firefox/icons/mozicon128.png
```

I have already tried:
-reinstallation of firefox
-restart of Ubuntu
-placing an icon instead of symlink in /usr/share/pixmaps

I have attached:
-screen-shot which shows the problem and that the icon is shown properly in /usr/share/pixmaps/
[ATTACH=CONFIG]240072[/ATTACH]
-firefox.desktop (I had to change name to firefox.desktop.txt)
[ATTACH]240073[/ATTACH]

Could you help me?

---

### Post by solarghost on 2013-03-12
Hi

Try installing an application called Alacarte ([https://apps.ubuntu.com/cat/applications/precise/alacarte/](https://apps.ubuntu.com/cat/applications/precise/alacarte/)) from the app center. Find the Firefox option (under Internet) and upload the icon there. Then try logout and back in again.

---

### Post by Ediaan on 2013-03-13
You could always try an alternative, like Chromium?

---

### Post by kkkkdddd on 2013-03-13
> **solarghost said:**
> Hi

Try installing an application called Alacarte ([https://apps.ubuntu.com/cat/applications/precise/alacarte/](https://apps.ubuntu.com/cat/applications/precise/alacarte/)) from the app center. Find the Firefox option (under Internet) and upload the icon there. Then try logout and back in again.


When I click "Properties" in Alacarte (on any entry):

Traceback (most recent call last):
  File "/usr/share/alacarte/Alacarte/MainWindow.py", line 634, in on_properties_button_clicked
    self.on_edit_properties_activate(None)
  File "/usr/share/alacarte/Alacarte/MainWindow.py", line 391, in on_edit_properties_activate
    process = subprocess.Popen(['gnome-desktop-item-edit', file_path], env=os.environ)
  File "/usr/lib/python2.7/subprocess.py", line 679, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1249, in _execute_child
    raise child_exception
OSError: [Errno 2] Nie ma takiego pliku ani katalogu

---

### Post by kkkkdddd on 2013-03-20
I have found a solution to my problem.

I had "firefox.desktop" in 2 folders:

~/.local/share/applications
and
/usr/share/applications

I also had "firefox-3.0.desktop" and "userapp-firefox-8JL08U.desktop" in 
~/.local/share/applications

To solve the problem:
1.
rm ~/.local/share/applications/firefox.desktop
rm ~/.local/share/applications/firefox-3.0.desktop
rm ~/.local/share/applications/userapp-firefox-8JL08U.desktop
2.
log out and log in
3.
readd firefox to the laucher

---

