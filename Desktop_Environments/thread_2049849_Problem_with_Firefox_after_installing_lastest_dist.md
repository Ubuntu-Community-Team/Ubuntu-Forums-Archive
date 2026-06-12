---
title: "Problem with Firefox after installing lastest dist-upgrade (12.04)"
date: 2012-08-29
forum: Desktop Environments
---

### Post by inckiekage on 2012-08-29
My Ubuntu 12.04 Desktop offered me some updates today, after installing them, my Firefox start to act weird

The scroll bar on some pages doesn't work, and some pages the input boxes don't work. 

All other things in the browser works fine. I can mark text on pages, plugins like flash and java applets runs and i can close the browser fine.

Here is some dist-upgrade logs

**history.log **
```

kimse@kimse-laptop:~$ cat /var/log/dist-upgrade/history.log 

Start-Date: 2012-08-29  10:56:13
Upgrade: firefox-globalmenu:amd64 (14.0.1+build1-0ubuntu0.12.04.1, 15.0+build1-0ubuntu0.12.04.1), firefox:amd64 (14.0.1+build1-0ubuntu0.12.04.1, 15.0+build1-0ubuntu0.12.04.1)
Remove: xul-ext-unity:amd64 (2.0-0precise1), xul-ext-websites-integration:amd64 (1.2.0-0precise3), unity-webapps-preview:amd64 (2.1), xul-ext-webaccounts:amd64 (0.2+bzr13-0precise1)
End-Date: 2012-08-29  10:56:24

Start-Date: 2012-08-29  11:01:01
Remove: libhal1:amd64 (0.5.14-8), libgsoap1:amd64 (2.8.4-2)
End-Date: 2012-08-29  11:01:03

```

**apt.log** 
```
kimse@kimse-laptop:~$ cat /var/log/dist-upgrade/apt.log 
Log time: 2012-08-29 10:25:37.009016
Starting
Starting 2
Investigating (0) xul-ext-websites-integration [ amd64 ] < 1.2.0-0precise3 > ( web )
Broken xul-ext-websites-integration:amd64 Breaks on firefox [ amd64 ] < 14.0.1+build1-0ubuntu0.12.04.1 -> 15.0+build1-0ubuntu0.12.04.1 > ( web ) (>= 14.+)
  Considering firefox:amd64 17 as a solution to xul-ext-websites-integration:amd64 3
  Removing xul-ext-websites-integration:amd64 rather than change firefox:amd64
Investigating (0) xul-ext-unity [ amd64 ] < 2.0-0precise1 > ( web )
Broken xul-ext-unity:amd64 Depends on xul-ext-websites-integration [ amd64 ] < 1.2.0-0precise3 > ( web )
  Considering xul-ext-websites-integration:amd64 3 as a solution to xul-ext-unity:amd64 1
  Removing xul-ext-unity:amd64 rather than change xul-ext-websites-integration:amd64
Investigating (0) xul-ext-webaccounts [ amd64 ] < 0.2+bzr13-0precise1 > ( web )
Broken xul-ext-webaccounts:amd64 Breaks on firefox [ amd64 ] < 14.0.1+build1-0ubuntu0.12.04.1 -> 15.0+build1-0ubuntu0.12.04.1 > ( web ) (>= 14.+)
  Considering firefox:amd64 17 as a solution to xul-ext-webaccounts:amd64 1
  Removing xul-ext-webaccounts:amd64 rather than change firefox:amd64
Investigating (0) unity-webapps-preview [ amd64 ] < 2.1 > ( metapackages )
Broken unity-webapps-preview:amd64 Depends on xul-ext-unity [ amd64 ] < 2.0-0precise1 > ( web )
  Considering xul-ext-unity:amd64 1 as a solution to unity-webapps-preview:amd64 0
  Removing unity-webapps-preview:amd64 rather than change xul-ext-unity:amd64
Done
MarkUpgrade() called on a non-upgrable pkg: 'brasero'
ERROR:root:Upgrading 'brasero' failed
Log time: 2012-08-29 10:56:26.203944
```

**apt-term.log **
```
kimse@kimse-laptop:~$ cat /var/log/dist-upgrade/apt-term.log 

Log started: 2012-08-29  10:56:13
(Reading database ... 252564 files and directories currently installed.)
Removing unity-webapps-preview ...
Removing xul-ext-unity ...
Removing xul-ext-webaccounts ...
Removing xul-ext-websites-integration ...
(Reading database ... 252451 files and directories currently installed.)
Preparing to replace firefox-globalmenu 14.0.1+build1-0ubuntu0.12.04.1 (using .../firefox-globalmenu_15.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-globalmenu ...
Preparing to replace firefox 14.0.1+build1-0ubuntu0.12.04.1 (using .../firefox_15.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Setting up firefox (15.0+build1-0ubuntu0.12.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (15.0+build1-0ubuntu0.12.04.1) ...
Log ended: 2012-08-29  10:56:24

Log started: 2012-08-29  11:01:01
(Reading database ... 252453 files and directories currently installed.)
Removing libgsoap1 ...
Removing libhal1 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Log ended: 2012-08-29  11:01:03
```

---

### Post by irv on 2012-08-29
Were you running Firefox when you did the updates this morning? If so have you restarted Firefox? Have your rebooted you computer since the updates?
I did the updates this morning and I am also running the 64bit version and everything is working find.

---

### Post by inckiekage on 2012-08-29
Firefox was running while installing but, I have reboot several times since.

---

### Post by irv on 2012-08-29
I would try completely removing it and them reinstall it. I found sometime this is the easy way to fix things when things go wrong.

---

### Post by ludar on 2012-09-01
I have similar problem. If You have installed "Translate This!" extension then try to switch it off or uninstall it. 

This helped me.

---

### Post by inckiekage on 2012-09-01
I dont have that plugin, reistalling it didn't help either. also triede to completely remove <home-path>/.mozilla folder

---

