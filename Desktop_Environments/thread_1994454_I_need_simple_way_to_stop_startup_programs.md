---
title: "I need simple way to stop startup programs"
date: 2012-06-02
forum: Desktop Environments
---

### Post by forsubhi on 2012-06-02
I try to stop startup programs  from system setting --> startup and shutdown  but I don't see my  programs and every time golden dict and empathy startup automatically , 
I need simple way to remove them from startup in kubuntu 11.10

please help me !

---

### Post by mparillo on 2012-06-03
Do you have a .desktop file under share/autostart (either under $KDEHOME or under $KDEDIR)?


[http://l10n.kde.org/docs/admin/autostart-and-runonce.html](http://l10n.kde.org/docs/admin/autostart-and-runonce.html)

---

### Post by forsubhi on 2012-06-03
No , I have .directory file

---

### Post by forsubhi on 2012-06-19
this  work for me
[http://askubuntu.com/questions/109530/how-do-i-restore-my-kde-desktop-to-default](http://askubuntu.com/questions/109530/how-do-i-restore-my-kde-desktop-to-default)

---

### Post by VMC on 2012-06-19
> **forsubhi said:**
> I try to stop startup programs  from system setting --> startup and shutdown  but I don't see my  programs and every time golden dict and empathy startup automatically , 
I need simple way to remove them from startup in kubuntu 11.10

please help me !

See if yo find it here:

```
dolphin /usr/share/autostart
```

---

### Post by forsubhi on 2012-06-19
I think  that this method is correct 

```
subhi@subhi-pc:~$ ls /usr/share/autostart
akonaditray.desktop           konqy_preload.desktop      polkit-kde-authentication-agent-1.desktop
kaddressbookmigrator.desktop  korgac.desktop             printer-applet.desktop
kalarm.autostart.desktop      krunner.desktop            restore_kmix_volumes.desktop
kgpg.desktop                  nepomukcontroller.desktop  synaptiks_autostart.desktop
klipper.desktop               nepomukserver.desktop      xsettings-kde.desktop
kmix_autostart.desktop        plasma-desktop.desktop
```

---

### Post by cottfcfan on 2012-06-20
```
cd /etc/xdg/autostart/
```
then:
```
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```
All your start up apps will now appear in "startup applications"

---

### Post by VMC on 2012-06-20
> **cottfcfan said:**
> ```
cd /etc/xdg/autostart/
```
then:
```
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```
All your start up apps will now appear in "startup applications"

That's good for ubuntu, but in kubuntu, there's not much there.
Most are in ```
/usr/share/autostart
```

---

### Post by cottfcfan on 2012-06-20
Sorry, didn't notice.
In Kubuntu, Autostart just has the things you manually added to startup.
The one below it "service manager" has all the other programs that autostart.

---

