---
title: "pidgin integration in unity"
date: 2011-05-31
forum: Desktop Environments
---

### Post by mejo on 2011-05-31
Hello,

Today I tried to setup pidgin at my fresh ubuntu 11.04 Natty Narwhal system. Unfortunately I didn't find a solution to integrate Pidgin into the unity desktop.

I didn't manage to add the tray icon to the unity tray. According to google, the following should do the trick:

```
$ gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'hp-systray', 'scp-dbus-service', 'pidgin']"
```Unfortunately it didn't change anything. The Pidgin tray icon is still missing.

Now I'm wondering whether there's a solution to integrate Pidgin into unity at all. My unity tray includes the letter icon, which lists Pidgin in a submenu. And it contains the instant messenger icon. Here I can change my status, but when I select 'Chat-Accounts' (in german: Chat-Konten), Empathy is started instead of Pidgin.

Greetings,
 jonas

---

### Post by Vesukka on 2011-07-23
I changed 'pidgin' to **'Pidgin'** and got the tray icon after I ran command 'unity --replace'.

---

### Post by hyperair on 2011-10-25
This is a bit late, but if you install pidgin-libnotify, you'll get a Pidgin entry in the messaging menu.

---

### Post by pabloab777 on 2012-01-03
I had already iinstalled **pidgin-libnotify** (dpkg -l |grep pidgin-libnotify) but Pidgin still was not on tray, Y had to:
```

gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'hp-systray', 'scp-dbus-service', 'Pidgin']"
unity --replace &

```
to have it. Pidgin remains on Launcher when minimized, but disappears but remains resident when "closed" with the x, forcing me to "killall pidgin". Sometimes even LibreOfficeCalc disappear from Launcher!

I'm also trying with **tilt2**, a taskbar... :S

$ unity --version
unity 4.24.0
$ pidgin --version
Pidgin 2.10.0 (libpurple 2.10.0)

---

### Post by hyperair on 2012-01-03
Did you enable the plugin (Tools->Plugins)? A pidgin entry should appear in the messaging indicator.

---

### Post by jxj on 2012-01-16
> gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'hp-systray', 'scp-dbus-service', 'pidgin']"

ok. but how can i undo this?

---

### Post by hyperair on 2012-01-16
```
gsettings reset com.canonical.Unity.Panel systray-whitelist
```

Or alternatively, you can navigate to com.canonical.Unity.Panel in dconf-editor, click on systray-whitelist, and click reset.

---

### Post by grooverider on 2012-01-31
indeed this command worked for me:
> gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'hp-systray', 'scp-dbus-service', 'Pidgin']"
then i rebooted as first time when i tried with > unity --replace i got some errors and my desktop was not responding, this is by the way on ubuntu 11.10/gnome 3.2.1/kernel 3.0.0-14-generic

---

