---
title: "How to make Compiz default in Ubuntu classic in 11.04"
date: 2011-04-16
forum: Desktop Environments
---

### Post by Hotshot5000 on 2011-04-16
I use Ubuntu Classic cause I can't stand Unity and somehow my default window manager is Metacity. I'd like to go back to Compiz but in Appearance there is no longer any Visual effects tab (I think it disappeared after installing ccsm). So it always loads Metacity and I have to use Compiz --replace to get it going. So how can I make it default to Compiz?
Also Compiz Fusion Icon does not work yet....I saw there is a bug reported and also a fix reported but somehow it didn't get here yet.

---

### Post by Copper Bezel on 2011-04-16
I'd suggest just making a startup item for compiz --replace under Preferences -> Startup Applications.

---

### Post by Krytarik on 2011-04-16
Try this, run these commands in a terminal:
```
gconftool-2 /desktop/gnome/applications/window_manager/current --type string --set /usr/bin/compiz
gconftool-2 /desktop/gnome/applications/window_manager/default --type string --set /usr/bin/compiz
```
The value for Metacity is "/usr/bin/metacity".

Greetings.

---

### Post by Hotshot5000 on 2011-04-16
I used compiz --replace as a startup. The second one with gconftool-2  doesn't work but I'll look into this command. Should I have used sudo?

---

### Post by Krytarik on 2011-04-16
> **Hotshot5000 said:**
> The second one with gconftool-2  doesn't work but I'll look into this command. Should I have used sudo?
No. But you have of course to relogin after running them.

---

### Post by Copper Bezel on 2011-04-16
Yeah, Krytarik's method is the "correct" one. It's always better to change a default setting than to have the system override it like this, so I'd play with that a bit. (You'll prevent Metacity from loading into memory in the first place and save 5-10 seconds of login time.)

---

### Post by Hotshot5000 on 2011-04-16
I can't find this path 
/desktop/gnome/applications/window_manager/current

there is no /desktop folder

---

### Post by Krytarik on 2011-04-16
> **Hotshot5000 said:**
> I can't find this path 
/desktop/gnome/applications/window_manager/current

there is no /desktop folder
You mean in "gconf-editor", right? Not the file system!

---

### Post by Hotshot5000 on 2011-04-16
OK my mistake. I'm new to Linux world, just installed it like 3 weeks ago. I went to gconf-editor and although I changed the default to /usr/bin/compiz every time I restart it says that current is metacity.

It says at default :Fallback window manager if user window manager can't be found. This key has been deprecated since GNOME 2.12. Maybe this could be an issue? It finds metacity first and doesn't bother checking there

---

### Post by Krytarik on 2011-04-16
> **Hotshot5000 said:**
> I went to gconf-editor and although I changed the default to /usr/bin/compiz every time I restart it says that current is metacity.

It says at default :Fallback window manager if user window manager can't be found. This key has been deprecated since GNOME 2.12. Maybe this could be an issue? It finds metacity first and doesn't bother checking there
So, why don't you simply run the given commands? Did you notice, that there are two key, "current" and "default"? You need to change both, or at least "current".

---

### Post by Hotshot5000 on 2011-04-16
Well I did ran them both and then logged off and on again and default remains /usr/bin/compiz while the current switches to metacity....as if it doesn't save the settings, just that after I run the commands and check in gconf-editor they are changed, only until relogging.

---

### Post by Krytarik on 2011-04-16
Hmm, weird! Try setting them as "Mandatory" in gconf-editor after running the commands again, or changing the values manually. To do so, right-click at the keys and choose "Set as Mandatory".

---

### Post by Hotshot5000 on 2011-04-16
Got them both mandatory entered the password and relogged. Still nothing. It does say something key not writable (even though I did write and it did save what I had written). The 2 keys also have an a in the icon, and the other 2 number of workspaces and workspace names don't and they are writable.

Also I noticed that in session/required_components I have metacity as a value at windowmanager. Should I change here?

Also in apps I have compiz and compiz-1....Is this OK?

Can't I just enable auto_save_session in apps/gnome-session/options?

---

### Post by Krytarik on 2011-04-16
> **Hotshot5000 said:**
> 
Also I noticed that in session/required_components I have metacity as a value at windowmanager. Should I change here?Yeah, try it, I also have it at "compiz" there.
> **Hotshot5000 said:**
> 
Also in apps I have compiz and compiz-1....Is this OK?I only have "compiz" there, I don't know why you have another one.
> **Hotshot5000 said:**
> 
Can't I just enable auto_save_session in apps/gnome-session/options?
That only saves running apps, not the window manager, imo.

Also, do you have a single or multiple monitor setup?

Btw, "a" only indicates that the type of the key is "string".

---

### Post by Hotshot5000 on 2011-04-16
Changed session/required_components to compiz and everything works now thank you for your input. Should I file this as a bug? Or it defaults to metacity by design if using Ubuntu Classic?

---

### Post by Krytarik on 2011-04-16
> **Hotshot5000 said:**
> Changed session/required_components to compiz and everything works now thank you for your input. Should I file this as a bug? Or it defaults to metacity by design if using Ubuntu Classic?
The default is, like in previous versions, Metacity. But there should of course be a GUI option, like in "Appearance -> Visual Effects", that allows you to switch to Compiz. I really don't know why those option is missing, maybe you should check for a bug report, or file one.

---

### Post by Copper Bezel on 2011-04-16
Ubuntu 11.04 uses the classic desktop as a fallback for the Compiz-based Unity. I imagine the change is related to that.

---

### Post by PBrn46 on 2011-04-22
> **Copper Bezel said:**
> Ubuntu 11.04 uses the classic desktop as a fallback for the Compiz-based Unity. I imagine the change is related to that.
@Copper Bezel: I'd think it's related to it too...

I have the same problem and the gconf-tool commands didn't work.

I would really like to default it to compiz without setting it in startup applications. Subscribed to this thread for further updates, if anybody can help! =D

---

### Post by Krytarik on 2011-04-22
@PBrn46: Did you set this too, as mentioned in post #14?:
```
gconftool-2 /desktop/gnome/session/required_components/windowmanager --type string --set compiz
```

---

### Post by PBrn46 on 2011-04-22
> **Krytarik said:**
> @PBrn46: Did you set this too, as mentioned in post #14?:
```
gconftool-2 /desktop/gnome/session/required_components/windowmanager --type string --set compiz
```
That worked. Thanks Krytarik! Skimmed past that post =)

---

### Post by Meriadok on 2011-04-30
Same problem here. After upgrade metacity loading on logging:
> 
wmctrl -m | grep Name | awk '{print $2}'
Metacity


All 3 keys in gconf are mandatorily set to compiz. Compiz --replace works well. Also i think i have too many variants in session list on logging screen: ubuntu, classic ubuntu, classic ubuntu (no effects), user difined session. But all of them start metacity.

Any idea?

---

### Post by Krytarik on 2011-04-30
@Meriadok: Make sure to *not* run 'gconf-editor' as root (with gksu/gksudo/sudo).
Otherwise you would change root's settings, not yours.

---

### Post by Meriadok on 2011-04-30
Thanks for fast answer. I run gconf not as a root.

---

### Post by Krytarik on 2011-04-30
> **Meriadok said:**
> Also i think i have too many variants in session list on logging screen: ubuntu, classic ubuntu, classic ubuntu (no effects), user difined session. But all of them start metacity.

These are the default session options, see here:
[http://ubuntuforums.org/showthread.php?t=1741293](http://ubuntuforums.org/showthread.php?t=1741293)

If you log in to "Ubuntu", do you have the launcher/panel?

---

### Post by Meriadok on 2011-04-30
Yes, after logging to "ubuntu" session, i have a normal panels, working windows with decorations etc. Before i removed unity i had a normal sidebar. Now both metacity and compiz operate normal. Compiz just doesn't want to load at startup. I added "compiz --replace" to startup applications but it looks like a very dirty workaround.

---

### Post by Krytarik on 2011-04-30
If you have the usual Unity-style launcher/panel in "Ubuntu" (thus Unity), Compiz is definitely running.
Or did you convert it into usual Gnome 2 look?

The same applies to "Ubuntu Classic" (with effects).

You can check in either session if Compiz is running with:
```
ps ax |grep -v grep |grep compiz
```It should look similar to this:```

 3178 ?        S     47:36 compiz
 3243 ?        Ss     0:00 /bin/sh -c /usr/bin/compiz-decorator
```

---

### Post by Meriadok on 2011-04-30
Just after logging without --replace workaround:

> ps ax |grep -v grep |grep metacity
 6816 ?        Sl     0:00 metacity


Now i haven't unity in my system but when i tried it all worked well. Now by removing unity package i turned system to gnome2 look.

Can be this compiz's behaviour a bug? Maybe i ought to open a bug issue on launchpad with link to this topic?

---

### Post by Krytarik on 2011-04-30
The process check for "compiz" turned out nothing?
> **Meriadok said:**
> 
Now i haven't unity in my system but when i tried it all worked well.
Without running "compiz --replace" before?
> **Meriadok said:**
> 
Now by removing unity package i turned system to gnome2 look.
Did you really remove packages? If so, I wonder what else has been removed alongside to it, then please check "/var/log/apt/history.log" for it.
> **Meriadok said:**
> 
Can be this compiz's behaviour a bug? Maybe i ought to open a bug issue on launchpad with link to this topic?
I don't think so by now.

---

### Post by Meriadok on 2011-04-30
> **Krytarik said:**
> The process check for "compiz" turned out nothing?

Yes, nothing. After compiz --replace it founds compiz.

> **Krytarik said:**
> Without running "compiz --replace" before?

Yes, it's the most weird thing.


> **Krytarik said:**
> Did you really remove packages? If so, I wonder what else has been removed alongside to it, then please check "/var/log/apt/history.log" for it.

In fact, actually nothing important depends on unity:
> Start-Date: 2011-04-30  08:31:26
Commandline: /usr/sbin/synaptic
Remove: unity:i386 (3.8.12-0ubuntu1), unity-2d:i386 (3.8.4.1-0ubuntu1), unity-2d-default-settings:i386 (3.8.4.1-0ubuntu1)
End-Date: 2011-04-30  08:31:49

Start-Date: 2011-04-30  08:32:59
Commandline: apt-get autoremove
Remove: unity-asset-pool:i386 (0.8.20-0ubuntu2), geoclue:i386 (0.12.0-1ubuntu8), libnux-0.9-common:i386 (0.9.48-0ubuntu1), unity-2d-panel:i386 (3.8.4.1-0ubuntu1), libqtgconf1:i386 (0.1-0ubuntu5), libnux-0.9-0:i386 (0.9.48-0ubuntu1), unity-place-applications:i386 (0.2.46-0ubuntu3), unity-2d-launcher:i386 (3.8.4.1-0ubuntu1), libunity-2d-private0:i386 (3.8.4.1-0ubuntu1), libqtbamf1:i386 (0.2.1-0ubuntu1), libgeoclue0:i386 (0.12.0-1ubuntu8), zeitgeist:i386 (0.7.1-1), libqtdee2:i386 (0.2.2-0ubuntu1), geoclue-ubuntu-geoip:i386 (0.0.2-0ubuntu5), unity-common:i386 (3.8.12-0ubuntu1), unity-2d-spread:i386 (3.8.4.1-0ubuntu1), unity-place-files:i386 (0.5.46-0ubuntu5), indicator-datetime:i386 (0.2.3-0ubuntu3), zeitgeist-extension-fts:i386 (0.0.7-0ubuntu1), zeitgeist-datahub:i386 (0.7.0-0ubuntu1), libutouch-geis1:i386 (2.0.10-0ubuntu1), libunity-misc0:i386 (0.2.1-0ubuntu2), nux-tools:i386 (0.9.48-0ubuntu1), libzeitgeist-1.0-1:i386 (0.3.10-0ubuntu1), unity-2d-places:i386 (3.8.4.1-0ubuntu1)
End-Date: 2011-04-30  08:34:22

I also checked .desktop files in /usr/share that are responsible for gnome sessions settings. Everything looks normal, everywhere compiz is set as default window manager.

---

### Post by Krytarik on 2011-04-30
Yeah, your log seems fine.

Could you try creating a new user and logging with those in to "Ubuntu" *and* "Ubuntu Classic"? Just to narrow down if it's a user-specific configuration issue.
If you want to do try that: "System -> Administration -> Users and Groups".

---

### Post by Meriadok on 2011-04-30
Done. New user, 2 log-ins. Result: Not-user-specific issue - both sessions started with metacity, after compiz --replace effects run fine.
Also, i've read ~/.xsession-errors and gdm logs. Nothing wm-specific.

---

### Post by Meriadok on 2011-04-30
I tried to play with /usr/share/gnome-session/ubuntu.desktop file. By default it looks like:
> 
[GNOME Session]
Name=Ubuntu
Required=windowmanager;panel;filemanager;
Required-windowmanager=compiz
Required-panel=compiz
Required-filemanager=nautilus
DefaultApps=gnome-settings-daemon;
IsRunnableHelper=/usr/lib/nux/unity_support_test
FallbackSessionsID=FallbackUnity2d;FallbackClassicGnome
FallbackUnity2d=2d-ubuntu
FallbackClassicGnome=classic-gnome
FallbackClassicGnomeMessage=It seems that you do not have the hardware required to run Unity. Please choose Ubuntu Classic at the login screen and you will be using the traditional environment.

[Desktop Entry]
X-Ubuntu-Gettext-Domain=gnome-session-2.0


First, i tried to delete rows:
> 
IsRunnableHelper=/usr/lib/nux/unity_support_test
FallbackSessionsID=FallbackUnity2d;FallbackClassicGnome
FallbackUnity2d=2d-ubuntu
FallbackClassicGnome=classic-gnome
FallbackClassicGnomeMessage=It seems that you do not have the hardware required to run Unity. Please choose Ubuntu Classic at the login screen and you will be using the traditional environment.


After this change i had only wallpaper, desktop icons and mouse after log-in. Then i decided to change required-panel to "gnome-panel". Now i had normal gnome-panel but still no wm (missing windows decorations, missing wm-specific hotkeys etc). Changing Required-windowmanager to /usr/bin/compiz gave nothing.
Now i understand the mechanism why i see metacity on startup. Compiz can't load and gnome-session fallbacks to classic-gnome according to ubuntu.desktop. But i still can't understand why compiz refuses to load at starup but then starts normally after compiz --replace.

---

### Post by Krytarik on 2011-04-30
> **Meriadok said:**
> 
Now i understand the mechanism why i see metacity on startup. Compiz can't load and gnome-session fallbacks to classic-gnome according to ubuntu.desktop.But i still can't understand why compiz refuses to load at starup but then starts normally after compiz --replace.
You didn't mention that you get those message at login before, is that the case then?
> **Meriadok said:**
> But i still can't understand why compiz refuses to load at starup but then starts normally after compiz --replace.
Me neither. Try removing "windowmanager" from the key "Required=" and running "compiz --replace" through "Startup Applications". It is in fact not really different from the usual way, aside from the timing, and that may be crucial.

---

### Post by Meriadok on 2011-05-01
Hmmmmmmm. Seems, SOLVED. Today i've tried to log-in in to recovery console session and run gnome-session manually with --debug option. I've read syslog and found that system fallbacks to 2d-gnome.desktop session. In this file metacity was set as window manager, I've changed it to compiz. After first reboot i gave system completely witout any wm. But now compiz seems to start normally even without workaround in startup applications. Why it didn't worked yesterday after deleing rows with unity checks in ubuntu.desktop file, i don't know. I'll try to found ubuntu.desktop file from maverick and compare. Very weird.

---

### Post by Krytarik on 2011-05-01
> **Meriadok said:**
> I'll try to found ubuntu.desktop file from maverick and compare.
The way how the window manager is chosen to run at login has changed in Natty. Now it is specified by the session options itself, before it was specified in Gconf, and was easier to modify.

---

