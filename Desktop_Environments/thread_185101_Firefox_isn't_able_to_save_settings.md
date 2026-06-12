---
title: "Firefox isn't able to save settings"
date: 2006-05-31
forum: Desktop Environments
---

### Post by BAzfH on 2006-05-31
Hey there,

i'm having trouble with my firefox installation in ubuntu dapper drake. If i try to configure a proxy in the Preferences and then click OK the dialog can't be closed. It seems like firefox does ignore the click on OK. Now when i cancel the dialog it seems as it does use the new settings anyway as surfing is done through the proxy, but when i restart firefox the settings are lost and problem starts again. Tried to solve the problem by reinstalling the package 'mozilla-firefox' with the apt-get --reinstall option, but it did not help.

Is there anybode else having the same problem? Is it a bug or something i missed?

Some informations:

```

schoenfeld@teekanne:~$ dpkg -l mozilla-firefox
Gewünscht=Unbekannt/Installieren/R=Entfernen/P=Säubern/Halten
| Status=Nicht/Installiert/Config/U=Entpackt/Fehlgeschl. Konf./Halb install.
|/ Fehler?=(keiner)/Halten/R=Neuinst. notw/X=beides (Status, Fehler: GROß=schlecht)
||/ Name           Version        Beschreibung
+++-==============-==============-============================================
ii  mozilla-firefo 1.5.dfsg+1.5.0 Transition package for firefox rename

```

I want to know if it's a bug, then i will report it, or if its solvable by any setting or.. something.

best regards
BAzfH

---

### Post by bakert on 2006-07-15
I have a somewhat similar problem - firefox isn't able to remember which toolbars are on view.  Whatever I do when I restart firefox it shows all the toolbars.  Proxies and extensions all work as they should.

Did you find a solution to your problem?

---

