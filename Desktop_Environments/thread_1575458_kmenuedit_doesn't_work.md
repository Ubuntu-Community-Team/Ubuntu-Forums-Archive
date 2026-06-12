---
title: "kmenuedit doesn't work"
date: 2010-09-15
forum: Desktop Environments
---

### Post by someitalian123 on 2010-09-15
The changes I make in kmenuedit don't take effect. I get error message that says

Unable to contact khotkeys. Your changes are saved, but they could not be activated.

and in the terminal getting this

linux@linux:~$ kdesudo kmenuedit
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
kmenuedit(1573): "org.freedesktop.DBus.Error.NameHasNoOwner" : "Could not get owner of name 'org.kde.kded': no such name" 
kdeinit4: preparing to launch /usr/lib/libkdeinit4_klauncher.so
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kded4.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kconf_update.so
"KConfigIni: In file /tmp/kde-root/kconf_updateCZ1598.tmp, line 1: " Invalid entry (missing '=') 
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
kdeinit4: preparing to launch /usr/bin/knotify4
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
knotify(1712) KNotify::event: 1  ref= 0

---

### Post by someitalian123 on 2010-09-16
bump

---

### Post by Zorael on 2010-09-17
Menu entries are saved on a per-user basis, so don't run kmenuedit as root (with kdesudo).
```
$ kmenuedit
```
If you want to make system-wide changes to all menus, you would have to manually edit .desktop files in **/usr/share/applications**. That's a bit bothersome, and changes to an application's menu entry (ergo, its .desktop file) would be lost upon upgrading that application's package.

As a sidenote, to remove any changes you've made to your menu (and open-with preferences for filetypes/mimetypes), simply rename or remove the directory **~/.local/share/applications**. Then run '**kbuildsycoca4**'.
```
$ mv ~/.local/share/applications ~/applications.backup
$ kbuildsycoca4
```

---

### Post by someitalian123 on 2010-10-06
I should really check the thread that I post more often. Thanks for the reply, not running as root works but I still get this in the terminal

Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 

Any idea why?

---

### Post by Zorael on 2010-10-07
> **someitalian123 said:**
> I should really check the thread that I post more often.
Do as I do - set the default subscription notification type to No email notification. Then the threads you've posted in get listed in your User CP whenever there are new replies in it.

```
Bus::open: Can not get ibus-daemon's address. 
IBusIn<putContext::createInputContext: no connection to ibus-daemon
```
As of 10.04, Kubuntu sets the default input method engine in KDE apps to [ibus](http://en.wikipedia.org/wiki/Intelligent_Input_Bus). The message you're getting is merely the KDE app complaining that the ibus daemon isn't running. You don't need it unless you want to input complex characters, like Chinese, Japanese or Korean.

If you feel it pollutes your terminal, you can try disabling all debug output. Run '**kdebugdialog**', check Disable all debug output and hit OK. That should make KDE apps much less spammy. I'm not completely sure it helps with the ibus message, but I don't see why it shouldn't.

---

### Post by someitalian123 on 2010-10-11
Thanks

---

