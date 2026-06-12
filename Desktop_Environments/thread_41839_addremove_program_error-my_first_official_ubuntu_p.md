---
title: "add/remove program error-my first official ubuntu problem"
date: 2005-06-15
forum: Desktop Environments
---

### Post by byen on 2005-06-15
hey guys,
After 60 days of solid use... i finally stumbled upon my first ubuntu problem....and here it is:
when i hit the add/remove program option in the application installer...nuthin happens! the busy cursor is on but thats it....it used to work be4 but does not anymore? any idea? (PS- when i hit the advanced button..it does go to the synaptic package manager as it shud!)

any suggestions?
thank you for your help.

---

### Post by Majlo on 2005-06-15
I have the same problem.
When i run Package Manager from terminal then :

```
mario@ubuntu:~$ gnome-app-install
Reading package lists... Done
Building dependency tree... Done
Traceback (most recent call last):
  File "/usr/lib/gnome-app-install/AppInstall.py", line 125, in idle
    self.updateCache()
  File "/usr/lib/gnome-app-install/AppInstall.py", line 144, in updateCache
    self.populate_menu()
  File "/usr/lib/gnome-app-install/AppInstall.py", line 242, in populate_menu
    import locale ; menu.setLocale(locale.getlocale(locale.LC_MESSAGES)[0])
AttributeError: Menu instance has no attribute 'setLocale'
```

---

### Post by Majlo on 2005-06-15
I add this into bugzilla.ubuntu.com 

See [https://bugzilla.ubuntu.com/show_bug.cgi?id=11877](https://bugzilla.ubuntu.com/show_bug.cgi?id=11877)

---

### Post by dissident on 2005-06-16
For the record. I get the exact same error message as Majlo above. My installation is less then a week old, but I've made several usability tweaks in that time.

---

### Post by Majlo on 2005-06-16
Ok the problem is fixed 

See this page 
[https://bugzilla.ubuntu.com/show_bug.cgi?id=11871](https://bugzilla.ubuntu.com/show_bug.cgi?id=11871)

When i downgrade package python-xdg , gnome-menus and remove package smeg the problem is fixed.
I can open gnome-app-install again.

New version gnome-app-install_0+20050404a-3 haven`t the problem.

---

### Post by byen on 2005-06-16
[QUOTE=Majlo]Ok the problem is fixed 

When i downgrade package python-xdg , gnome-menus and remove package smeg the problem is fixed.
I can open gnome-app-install again.

New version gnome-app-install_0+20050404a-3 haven`t the problem.[/QUOTE]

how do i downgrade the said applications? sorry if this Q sounds silly but i have no idea whatsoever...any help would be appretiated.

---

### Post by Majlo on 2005-06-16
[QUOTE=byen]how do i downgrade the said applications? sorry if this Q sounds silly but i have no idea whatsoever...any help would be appretiated.[/QUOTE]

Open Synaptic Package Manager and find package python-xdg .
Click on package and go to menu Package --> Force version and choose original hoary package..This same with gnome-menus .Package smeg will be remove automaticaly..

---

### Post by byen on 2005-06-16
wow! done!  just gotta make sure to avoid these babies getting upgraded automatically! thank you majlo ;-)

---

### Post by bier444 on 2005-06-30
hy

this bug is caused by smeg, that is not very nice. ther is a problem with python-xdg, ...

have a look at the link:
(ref.: [https://bugzilla.ubuntu.com/show_bug.cgi?id=11871](https://bugzilla.ubuntu.com/show_bug.cgi?id=11871))

i've uploaded a patched version of gnome-app-install-20050404v2, which works well.
the new version is gnome-app-install-20050404v3.
please use the updated version from 06-30-2005.
the install script is ALPHA, but maybe works well. no warranty!

bier444

---

### Post by byen on 2005-06-30
thank you bier will try it out.... did not know smeg was the culprit. that helps a bit. :-)

---

### Post by Amaranth on 2005-07-01
[QUOTE=bier444]hy

this bug is caused by smeg, that is not very nice. ther is a problem with python-xdg, ...

have a look at the link:
(ref.: [https://bugzilla.ubuntu.com/show_bug.cgi?id=11871](https://bugzilla.ubuntu.com/show_bug.cgi?id=11871))

i've uploaded a patched version of gnome-app-install-20050404v2, which works well.
the new version is gnome-app-install-20050404v3.
please use the updated version from 06-30-2005.
the install script is ALPHA, but maybe works well. no warranty!

bier444[/QUOTE]

Technically this wasn't caused by smeg. The problem is that newer python-xdg versions aren't backward compatible with older versions (it it pre-1.0 after all). Of course smeg is the reason the new python-xdg gets installed...

Solutions: get someone to put the patched version of gnome-app-install in backports, don't use gnome-app-install, don't use smeg

Sorry I can't help more.

---

### Post by bier444 on 2005-07-10
hy

i worked on the install-script, the first version did not work correctly. sorry for that. this is the new version (beta state). it should do now the correct install thing.

/********************************************************/
#!/bin/sh
# install-gai.sh, vs. 02, beta state
# developed by [email]bier444@yahoo.de[/email]

install -m 755 ./src/gnome-app-install /usr/bin/gnome-app-install

mkdir /usr/lib/gnome-app-install 2>/dev/null
install -m 644 ./src/AppInstall.py /usr/lib/gnome-app-install/AppInstall.py

cp ./po/es.gmo /usr/share/locale/es/LC_MESSAGES/gnome-app-install.mo
cp ./po/de.gmo /usr/share/locale/de/LC_MESSAGES/gnome-app-install.mo
cp ./po/el.gmo /usr/share/locale/el/LC_MESSAGES/gnome-app-install.mo
cp ./po/da.gmo /usr/share/locale/da/LC_MESSAGES/gnome-app-install.mo
cp ./po/pl.gmo /usr/share/locale/pl/LC_MESSAGES/gnome-app-install.mo
cp ./po/fr.gmo /usr/share/locale/fr/LC_MESSAGES/gnome-app-install.mo

mkdir -p /usr/share/glib-2.0/gettext/po 2>/dev/null
cp ./po/Makefile.in.in /usr/share/glib-2.0/gettext/po/

mkdir /usr/share/applications 2>/dev/null
cp ./data/gnome-app-install.desktop /usr/share/applications/

mkdir /usr/share/gnome-app-install 2>/dev/null
cp ./data/gnome-app-install.glade /usr/share/gnome-app-install/

cp ./menu-data/*desktop /usr/share/gnome-app-install/
cp ./menu-data/*png /usr/share/gnome-app-install/
cp ./menu-data/*xpm /usr/share/gnome-app-install/
cp ./menu-data/applications.menu /usr/share/gnome-app-install/

/********************************************************/

bier444

---

