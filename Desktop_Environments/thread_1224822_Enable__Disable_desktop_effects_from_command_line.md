---
title: "Enable / Disable desktop effects from command line?"
date: 2009-07-27
forum: Desktop Environments
---

### Post by skullmunky on 2009-07-27
Is it possible to enable and disable desktop effects / compiz from the command line?  It's all working just fine for me, but I use Maya, which is dramatically unable to cope with compositing window managers.  So, all Maya users miss out on all the fun.  I can use compiz the rest of the time, but have to go to the preferences and switch it on and off when using Maya.  What I'd like to do is add a line to the Maya launch script to check if a compositing window manager is running, disable it if it is, and re-enable it after quitting.   

Edit:

ok, found this way, but is it the right way?
Disable:
```

kwriteconfig --file kwinrc --group Compositing --key Enabled false
nohup kwin --replace

```

Enable:
```

kwriteconfig --file kwinrc --group Compositing --key Enabled true
nohup kwin --replace

```

---

### Post by gettinoriginal on 2009-07-27
I am not the smartest twig on the Ubuntu tree, but I believe you can switch window managers by:
```
metacity --replace
compiz --replace
```
Although I do not know if that works for all variants :confused:
And even though you didn't ask for it, an easier way is the compiz fusion icon that allows for switching window managers and window decorators with the click of a mouse.  :P

---

### Post by skullmunky on 2009-07-28
thanks ... I guess all window managers can be started with --replace to replace the currently running one.  I forgot to mention I'm primarily using KDE, which is why kwin instead of metacity/compiz.  I like Compiz-Fusion-Icon a lot but I'd really like to automate this as part of the bash script that launches Maya.

Currently the problem I'm having is that I need to launch kwin but have it disconnected from the current shell.  If my script has something like this (in /usr/autodesk/maya/bin/maya)

```

kwriteconfig --file kwinrc --group Compositing --key Enabled false
kwin --replace
./maya.bin

```

the problem is that the kwin process takes over, so we never get to actually launch maya.  using '&' would work except I'm going to launch ANOTHER kwin after maya exits, to return to compositing mode.  So I need to disconnect the kwin process from the bash script process that's calling it.  I notice plasma does this, not clear why kwin doesn't.  But anyway, that's a simple enough unix trick, right?

---

### Post by Zorael on 2009-07-28
You can disable compositing by calling kwin via a dbus call. That's probably true for Compiz as well.
```
$ qdbus org.kde.kwin /KWin toggleCompositing
```
So if you want it in a script;
```
#!/bin/bash

qdbus org.kde.kwin /KWin toggleCompositing
./maya.bin
qdbus org.kde.kwin /KWin toggleCompositing
```
Obviously, the above does it completely wrong if you call it when compositing is already disabled.
```
#!/bin/bash

if [ "$(qdbus org.kde.kwin /KWin compositingActive)" == "true" ];
then
        qdbus org.kde.kwin /KWin toggleCompositing   # active, so deactivating
fi

./maya.bin
qdbus org.kde.kwin /KWin toggleCompositing           # reactivating
```
And in turn, the above only works if calling ./maya.bin launches it in a foreground process (i.e it takes over the terminal session). If it starts as a child process, as is what would happen if you appended an ampersand (**&**) after it, you'd have to have a loop that checks every *n* seconds if the process is still running. And when it closes, toggles compositing again.
```
#!/bin/bash

if [ "$(qdbus org.kde.kwin /KWin compositingActive)" == "true" ];
then
        qdbus org.kde.kwin /KWin toggleCompositing   # active, so deactivating
fi

./maya.bin

while [ "$(pidof [COLOR="MediumTurquoise"]maya.bin[/COLOR])" ];  # replace [COLOR="MediumTurquoise"]maya.bin[/COLOR] with whatever its process is called if different
do
        # it's still running, checking again in [COLOR="Orange"]5[/COLOR] seconds, tweak delay as you like (the cpu overhead is minimal)
        sleep [COLOR="Orange"]5[/COLOR]
done

# loop ended = [COLOR="MediumTurquoise"]maya.bin[/COLOR] process no longer exists, safe to reactivate compositing
qdbus org.kde.kwin /KWin toggleCompositing
```
Now, if it *does* launch itself in a foreground process, the last script example will only delay reactivation of compositing, so pick the appropriate approach.

---

### Post by skullmunky on 2009-07-30
That's brilliant!  D-BUS is amazing.  

Except that didn't work for me, I don't see a toggleCompositing method - is that new in KDE 4.3?

```

qdbus org.kde.kwin /KWin

method Q_NOREPLY void org.kde.KWin.cascadeDesktop()
method void org.kde.KWin.circulateDesktopApplications()
method bool org.kde.KWin.compositingActive()
method int org.kde.KWin.currentDesktop()
method QList<int> org.kde.KWin.decorationSupportedColors()
method void org.kde.KWin.doNotManage(QString name)
method Q_NOREPLY void org.kde.KWin.killWindow()
method QStringList org.kde.KWin.listOfEffects()
method void org.kde.KWin.loadEffect(QString name)
method QStringList org.kde.KWin.loadedEffects()
method void org.kde.KWin.nextDesktop()
method void org.kde.KWin.previousDesktop()
method Q_NOREPLY void org.kde.KWin.reconfigure()
method void org.kde.KWin.reconfigureEffect(QString name)
method void org.kde.KWin.refresh()
signal void org.kde.KWin.reinitCompositing()
signal void org.kde.KWin.reloadConfig()
method bool org.kde.KWin.setCurrentDesktop(int desktop)
method void org.kde.KWin.showWindowMenuAt(qlonglong winId, int x, int y)
method void org.kde.KWin.toggleEffect(QString name)
method Q_NOREPLY void org.kde.KWin.unclutterDesktop()
method void org.kde.KWin.unloadEffect(QString name)
method bool org.kde.KWin.waitForCompositingSetup()
method QDBusVariant org.freedesktop.DBus.Properties.Get(QString interface_name, QString property_name)
method QVariantMap org.freedesktop.DBus.Properties.GetAll(QString interface_name)
method void org.freedesktop.DBus.Properties.Set(QString interface_name, QString property_name, QDBusVariant value)
method QString org.freedesktop.DBus.Introspectable.Introspect()

```

---

### Post by asmoore82 on 2009-07-30
I wrote this for 9.04 Gnome, maybe it will help:

```
**$ cat bin/EffectsSwitch** 
[COLOR="Blue"]#!/bin/bash[/COLOR]
[COLOR="Purple"]export[/COLOR] DISPLAY=:0
[COLOR="Purple"]for[/COLOR] env [COLOR="Purple"]in[/COLOR] $( cat /proc/$( pgrep -n -u "$USER" gnome-session )/environ |
                sed 's/\x00/\n/g' | grep -i dbus )
[COLOR="Purple"]do[/COLOR]
	[COLOR="Purple"]eval export[/COLOR] "$env"
[COLOR="Purple"]done[/COLOR]

[COLOR="Purple"]if[/COLOR] ps -A | grep metacity &>/dev/null; [COLOR="Purple"]then[/COLOR]
	winmanager="compiz"
[COLOR="Purple"]else[/COLOR]
	winmanager="metacity"
[COLOR="Purple"]fi[/COLOR]

notify-send -i desktop-effects "Desktop Effects" "Automatically Configuring."
nohup "$winmanager" --replace &>/dev/null &

[COLOR="Blue"]#End of File[/COLOR]
```

^^it makes all sorts of bad assumptions,
but works as a "toggle button" based on the `--replace` convention

---

### Post by Zorael on 2009-08-01
> **skullmunky said:**
> That's brilliant!  D-BUS is amazing.  

Except that didn't work for me, I don't see a toggleCompositing method - is that new in KDE 4.3?
Augh, that may well be. It could be included in versions older than the 4.2.98 (4.3rc3) I run, though. If you don't want to take the plunge, and/or you don't know how to manually fix things from a terminal when the packages don't install properly due to file conflicts (etc), you can get **4.2.4** from [Kubuntu updates ppa](https://launchpad.net/~kubuntu-ppa/+archive/ppa) (as opposed to [the Kubuntu backports ppa](https://launchpad.net/~kubuntu-ppa/+archive/backports) which houses the 4.2.98 packages).

Even though the ppa is mainainted by Kubuntu devs, the packages are still unsupported, so at your own risk. Not to mention I'm not at all sure that kwin in 4.2.4 contains that extra dbus call, either - mere optimistic speculation. ;3

---

